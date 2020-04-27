---
title: Eliminare un'origine dati (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: 910e3e16-7b91-49d8-80bb-b4243926afaa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff882caf0ce5d9ef7d2e9f059daed89ed4b50d82
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "63126104"
---
# <a name="delete-a-data-source-odbc"></a>Eliminare un'origine dati (ODBC)
  È possibile eliminare un'origine dati tramite l'amministratore ODBC, a livello di codice (tramite [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)) oppure eliminando un file (se il nome dell'origine dati è un file).  
  
### <a name="to-delete-a-data-source-by-using-odbc-administrator"></a>Per eliminare un'origine dati tramite Amministratore ODBC.  
  
1.  Nel **Pannello di controllo**aprire **strumenti di amministrazione**, quindi fare doppio clic su **origini dati (ODBC)**. In alternativa, è possibile eseguire odbcad32.exe dal prompt dei comandi.  
  
2.  Fare clic sulla scheda DSN **utente**, **DSN di sistema**o **DSN su file** .  
  
3.  Fare clic sull'origine dati da eliminare.  
  
4.  Fare clic su **Rimuovi**, quindi confermare l'eliminazione.  
  
## <a name="example"></a>Esempio  
 Per eliminare un'origine dati a livello di codice, chiamare [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) usando ODBC_REMOVE_DSN o ODBC_REMOVE_SYS_DSN come secondo parametro.  
  
 Nell'esempio seguente viene illustrato come è possibile eliminare un'origine dati a livello di programmazione.  
  
```  
// remove_odbc_data_source.cpp  
// compile with: ODBCCP32.lib user32.lib  
#include <iostream>  
#include <windows.h>  
#include <odbcinst.h>  
  
int main() {   
   LPCSTR provider = "SQL Server";   // Windows SQL Server Driver  
   LPCSTR provider = "SQL Server";   // Windows SQL Server driver  
   LPCSTR provider2 = "SQL Server Native Client 11.0";   // SQL Server 2012 Native Client driver  
   LPCSTR dsnname = "DSN=data2";  
   BOOL retval = SQLConfigDataSource(NULL, ODBC_REMOVE_DSN, provider, dsnname);  
   std::cout << retval;   // 1 if successful  
}  
```  
  
## <a name="see-also"></a>Vedi anche  
 [Configurazione delle procedure del driver ODBC di SQL Server](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  
