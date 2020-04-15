---
title: Comandi che generano risultati con più set di righe | Microsoft Docs
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
ms.openlocfilehash: 2cbdba7e16240b5adfd14c43a5916aaaf8cf0400
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304482"
---
# <a name="commands-generating-multiple-rowset-results"></a>Comandi che generano risultati con più set di righe
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può restituire più set di righe dalle istruzioni. Tramite le istruzioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono restituiti più set di righe nelle condizioni seguenti:  
  
-   Le istruzioni SQL in batch vengono inviate come singolo comando.  
  
-   Le stored procedure consentono di implementare un batch di istruzioni SQL.  
  
## <a name="batches"></a>Batch  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client riconosce il carattere punto e virgola come delimitatore batch per le istruzioni SQL:The Native Client OLE DB provider recognizes the punto e virgola character as a batch delimiter for SQL statements:  
  
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
 [Comandi:](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
