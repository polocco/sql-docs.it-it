---
title: Comandi che generano risultati con più set di righe (provider OLE DB Native Client) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- SQL Server Native Client OLE DB provider, commands
- SQL Server Native Client OLE DB provider, multiple rowsets
- commands [OLE DB]
- multiple-rowset results
ms.assetid: 4567668d-35fd-4162-b61f-f7536862cdcb
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a8f689ecd7d6c66880f217a8ea262acc113591af
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942870"
---
# <a name="commands-generating-multiple-rowset-results"></a>Comandi che generano risultati con più set di righe
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider di OLE DB di Native client può restituire più set di righe dalle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istruzioni. Tramite le istruzioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono restituiti più set di righe nelle condizioni seguenti:  
  
-   Le istruzioni SQL in batch vengono inviate come singolo comando.  
  
-   Le stored procedure consentono di implementare un batch di istruzioni SQL.  
  
## <a name="batches"></a>Batch  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider di OLE DB di Native Client riconosce il carattere punto e virgola come delimitatore di batch per le istruzioni SQL:  
  
```  
WCHAR*       wSQLString = L"SELECT * FROM Categories; "  
                          L"SELECT * FROM Products";  
```  
  
 L'invio di più istruzioni SQL in un batch è più efficiente dell'esecuzione separata delle singole istruzioni SQL. Questo tipo di invio riduce infatti i round trip in rete dal client al server.  
  
## <a name="stored-procedures"></a>Stored procedure  
 Tramite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene restituito un set di risultati per ogni istruzione di una stored procedure. Pertanto, dalla maggior parte delle stored procedure di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono restituiti più set di risultati.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
-   [Utilizzo dell'interfaccia IMultipleResults per elaborare più set di risultati](../../relational-databases/native-client-ole-db-commands/using-imultipleresults-to-process-multiple-result-sets.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Comandi](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
