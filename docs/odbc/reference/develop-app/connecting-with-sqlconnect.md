---
title: Connessione con SQLConnect | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- connecting to driver [ODBC], SQLConnect
- functions [ODBC], data source or driver connections
- SQLConnect function [ODBC], connecting
- connecting to data source [ODBC], SQLConnect
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: b16319d2-2c2c-4341-abb5-caa9e17362b4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 25c1dca7324f73f6aacf472fb225a09424c73d3a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "81294651"
---
# <a name="connecting-with-sqlconnect"></a>Connessione con SQLConnect
**SQLConnect** è la funzione di connessione più semplice. Richiede un nome di origine dati e accetta un ID utente e una password facoltativi. Funziona bene per le applicazioni che codificano a livello di codice un nome di origine dati e non richiedono un ID utente o una password. Funziona anche per le applicazioni che desiderano controllare il proprio "aspetto" o che non hanno un'interfaccia utente. Tali applicazioni possono compilare un elenco di origini dati utilizzando **SQLDataSources**, richiedere all'utente l'origine dati, l'ID utente e la password, quindi chiamare **SQLConnect**.  
  
 Nell'esempio seguente viene eseguita la connessione al database Northwind utilizzando un DSN denominato Northwind e vengono recuperati tutti i campi nome e cognome di tutti i record della tabella Employees.  
  
```  
// Connecting_with_SQLConnect.cpp  
// compile with: user32.lib odbc32.lib  
#include <windows.h>  
#include <sqlext.h>  
#include <mbstring.h>  
#include <stdio.h>  
  
#define MAX_DATA 100  
#define MYSQLSUCCESS(rc) ((rc == SQL_SUCCESS) || (rc == SQL_SUCCESS_WITH_INFO) )  
  
class direxec {  
   RETCODE rc; // ODBC return code  
   HENV henv; // Environment     
   HDBC hdbc; // Connection handle  
   HSTMT hstmt; // Statement handle  
  
   unsigned char szData[MAX_DATA]; // Returned data storage  
   SDWORD cbData; // Output length of data  
   unsigned char chr_ds_name[SQL_MAX_DSN_LENGTH]; // Data source name  
  
public:  
   direxec(); // Constructor  
   void sqlconn(); // Allocate env, stat, and conn  
   void sqlexec(unsigned char *); // Execute SQL statement  
   void sqldisconn(); // Free pointers to env, stat, conn, and disconnect  
   void error_out(); // Displays errors  
};  
  
// Constructor initializes the string chr_ds_name with the data source name.  
// "Northwind" is an ODBC data source (odbcad32.exe) name whose default is the Northwind database  
direxec::direxec() {  
   _mbscpy_s(chr_ds_name, SQL_MAX_DSN_LENGTH, (const unsigned char *)"Northwind");  
}  
  
// Allocate environment handle and connection handle, connect to data source, and allocate statement handle.  
void direxec::sqlconn() {  
   SQLAllocEnv(&henv);  
   SQLAllocConnect(henv, &hdbc);  
   rc = SQLConnect(hdbc, chr_ds_name, SQL_NTS, NULL, 0, NULL, 0);  
  
   // Deallocate handles, display error message, and exit.  
   if (!MYSQLSUCCESS(rc)) {  
      SQLFreeConnect(henv);  
      SQLFreeEnv(henv);  
      SQLFreeConnect(hdbc);  
      if (hstmt)  
         error_out();  
      exit(-1);  
   }  
  
   rc = SQLAllocStmt(hdbc, &hstmt);  
}  
  
// Execute SQL command with SQLExecDirect() ODBC API.  
void direxec::sqlexec(unsigned char * cmdstr) {  
   rc = SQLExecDirect(hstmt, cmdstr, SQL_NTS);  
   if (!MYSQLSUCCESS(rc)) {  //Error  
      error_out();  
      // Deallocate handles and disconnect.  
      SQLFreeStmt(hstmt,SQL_DROP);  
      SQLDisconnect(hdbc);  
      SQLFreeConnect(hdbc);  
      SQLFreeEnv(henv);  
      exit(-1);  
   }  
   else {  
      for ( rc = SQLFetch(hstmt) ; rc == SQL_SUCCESS ; rc=SQLFetch(hstmt) ) {  
         SQLGetData(hstmt, 1, SQL_C_CHAR, szData, sizeof(szData), &cbData);  
         // In this example, the data is sent to the console; SQLBindCol() could be called to bind   
         // individual rows of data and assign for a rowset.  
         printf("%s\n", (const char *)szData);  
      }  
   }  
}  
  
// Free the statement handle, disconnect, free the connection handle, and free the environment handle.  
void direxec::sqldisconn() {  
   SQLFreeStmt(hstmt,SQL_DROP);  
   SQLDisconnect(hdbc);  
   SQLFreeConnect(hdbc);  
   SQLFreeEnv(henv);  
}  
  
// Display error message in a message box that has an OK button.  
void direxec::error_out() {  
   unsigned char szSQLSTATE[10];  
   SDWORD nErr;  
   unsigned char msg[SQL_MAX_MESSAGE_LENGTH + 1];  
   SWORD cbmsg;  
  
   while (SQLError(0, 0, hstmt, szSQLSTATE, &nErr, msg, sizeof(msg), &cbmsg) == SQL_SUCCESS) {  
      sprintf_s((char *)szData, sizeof(szData), "Error:\nSQLSTATE=%s, Native error=%ld, msg='%s'", szSQLSTATE, nErr, msg);  
      MessageBox(NULL, (const char *)szData, "ODBC Error", MB_OK);  
   }  
}  
  
int main () {  
   direxec x;   // Declare an instance of the direxec object.  
   x.sqlconn();   // Allocate handles, and connect.  
   x.sqlexec((UCHAR FAR *)"SELECT FirstName, LastName FROM employees");   // Execute SQL command  
   x.sqldisconn();   // Free handles and disconnect  
}  
```
