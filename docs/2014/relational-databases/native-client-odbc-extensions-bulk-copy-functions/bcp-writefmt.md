---
title: bcp_writefmt | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_writefmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_writefmt function
ms.assetid: cb4c1d37-667d-4bcd-b13c-eb638bcc9b69
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8d4a5067598b475ed8fe103606088d0e4d6d0554
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62689412"
---
# <a name="bcp_writefmt"></a>bcp_writefmt
  Crea un file di formato che contiene una descrizione del formato del file di dati della copia bulk corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RETCODE bcp_writefmt (  
HDBC   
hdbc  
,  
LPCTSTR   
szFormatFile  
);  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *hdbc*  
 Handle di connessione ODBC abilitato per la copia bulk.  
  
 *szFormatFile*  
 Percorso e nome del file utente per ricevere i valori di formato per il file di dati.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SUCCEED o FAIL.  
  
## <a name="remarks"></a>Osservazioni  
 Il file di formato specifica il formato dei dati di un file di dati creato dalla copia bulk. Le chiamate a [bcp_columns](bcp-columns.md) e [bcp_colfmt](bcp-colfmt.md) definiscono il formato del file di dati. **bcp_writefmt** Salva questa definizione nel file a cui fa riferimento *szFormatFile*. Per ulteriori informazioni, vedere [bcp_init](bcp-init.md).  
  
 Per ulteriori informazioni sulla struttura dei file di formato dei dati **bcp** , vedere [importare ed esportare dati per operazioni bulk tramite l'utilità bcp &#40;SQL Server&#41;](../import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md).  
  
 Per caricare un file di formato salvato, utilizzare [bcp_readfmt](bcp-readfmt.md).  
  
> [!NOTE]  
>  Il file di formato prodotto da **bcp_writefmt** è supportato solo dalle versioni dell'utilità **bcp** distribuite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con la versione 7,0 e successive.  
  
## <a name="example"></a>Esempio  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, _T("myTable"), _T("myData.csv"),  
   _T("myErrors"),    DB_OUT) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_columns(hdbc, 3) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
bcp_colfmt(hdbc, 1, SQLCHARACTER, 0, SQL_VARLEN_DATA, '\t', 1, 1);  
bcp_colfmt(hdbc, 2, SQLCHARACTER, 0, SQL_VARLEN_DATA, '\t', 1, 2);  
bcp_colfmt(hdbc, 3, SQLCHARACTER, 0, SQL_VARLEN_DATA, '\t', 1, 3);  
  
if (bcp_writefmt(hdbc, _T("myFmtFile.fmt")) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_exec(hdbc, &nRowsProcessed) == SUCCEED)  
   {  
   printf_s("%ld rows copied from SQL Server\n", nRowsProcessed);  
   }  
  
// Carry on.  
```  
  
## <a name="see-also"></a>Vedi anche  
 [Funzioni di copia bulk](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
