---
title: Recuperare una sola riga con IRow (OLE DB Driver) | Microsoft Docs
description: IRow consente l'accesso diretto alle colonne di un singolo oggetto riga. L'interfaccia IRow in OLE DB Driver per SQL Server è semplificata per migliorare le prestazioni.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- fetching rows
- IRow interface
- single row fetching [OLE DB Driver for SQL Server]
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- OLE DB Driver for SQL Server, fetching
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a305692bb544d9a9bbb0572cbd93449781aaabe9
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/25/2020
ms.locfileid: "88862469"
---
# <a name="fetching-a-single-row-with-irow-ole-db-driver"></a>Recupero di una sola riga con IRow (OLE DB Driver)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  L'implementazione dell'interfaccia **IRow** in OLE DB Driver per SQL Server è semplificata per migliorare le prestazioni. **IRow** consente l'accesso diretto alle colonne di un singolo oggetto riga. Se si prevede che il risultato dell'esecuzione di un comando produca esattamente una riga, **IRow** recupererà le colonne della riga in questione. Se il set di risultati include più righe, **IRow** esporrà solo la prima.  
  
 L'implementazione dell'interfaccia **IRow** non consente la navigazione all'interno della riga. A ogni colonna della riga è possibile accedere una sola volta, con un'eccezione. È infatti possibile accedere a una colonna una volta per trovarne le dimensioni e una seconda volta per recuperare i dati.  
  
> [!NOTE]  
>  **IRow::Open** supporta solo i tipi DBGUID_STREAM e DBGUID_NULL di oggetti da aprire.  
  
 Per ottenere un oggetto riga utilizzando il metodo **ICommand::Execute**, è necessario passare IID_IRow. L'interfaccia **IMultipleResults** deve essere utilizzata per gestire più set di risultati. **IMultipleResults** supporta **IRow** e **IRowset**. **IRowset** viene utilizzata per le operazioni bulk.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
-   [Uso di IRow::GetColumns](../../oledb/ole-db-rowsets/using-irow-getcolumns.md)   
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
