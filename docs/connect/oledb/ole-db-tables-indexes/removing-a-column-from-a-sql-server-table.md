---
title: Rimuovere un colonna da una tabella di SQL Server (OLE DB Driver)
description: Rimozione di una colonna da una tabella di SQL Server tramite OLE DB Driver per SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- removing columns
- DropColumn function
- OLE DB Driver for SQL Server, columns
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 7467d30e8cb13badbea21eff9804710ff4361259
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/28/2020
ms.locfileid: "87244112"
---
# <a name="removing-a-column-from-a-sql-server-table"></a>Rimozione di una colonna da una tabella di SQL Server
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver per SQL Server espone la funzione **ITableDefinition::DropColumn**. Questo consente ai consumer di rimuovere una colonna da una tabella di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 I consumer specificano il nome della tabella come stringa di caratteri Unicode nel membro *pwszName* dell'unione *uName* nel parametro *pTableID*. Il membro *eKind* di *pTableID* deve essere DBKIND_NAME.  
  
 Il consumer indica un nome di colonna nel membro *pwszName* dell'unione *uName* nel parametro *pColumnID*. Il nome di colonna è una stringa di caratteri Unicode. Il membro *eKind* di *pColumnID* deve essere DBKIND_NAME.  
  
## <a name="example"></a>Esempio  
  
### <a name="code"></a>Codice  
  
```  
DBID TableID;  
DBID ColumnID;  
HRESULT hr;  
  
TableID.eKind = DBKIND_NAME;  
TableID.uName.pwszName = L"MyTableName";  
  
ColumnID.eKind = DBKIND_NAME;  
ColumnID.uName.pwszName = L"MyColumnName";  
  
hr = m_pITableDefinition->DropColumn(&TableID, &ColumnID);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle e indici](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)  
  
  
