---
title: sys. dm_os_memory_nodes (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_memory_nodes_TSQL
- sys.dm_os_memory_nodes
- sys.dm_os_memory_nodes_TSQL
- dm_os_memory_nodes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_nodes dynamic management view
ms.assetid: bf4032fe-7db1-40e9-a62e-d69cebff4b44
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6f68524b2713b9d662c9e9ed0950334ea0a94ece
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "73983125"
---
# <a name="sysdm_os_memory_nodes-transact-sql"></a>sys.dm_os_memory_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Le allocazioni interne a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzano il gestore della memoria di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il rilevamento delle differenze tra i contatori della memoria del processo da **sys. dm_os_process_memory** e i contatori interni può indicare l'utilizzo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] della memoria da parte dei componenti esterni nello spazio di memoria.  
  
 I nodi vengono creati per nodi di memoria NUMA fisici. Potrebbero essere diversi dai nodi CPU in **sys. dm_os_nodes**.  
  
 Nessuna delle allocazioni eseguite direttamente tramite le routine di allocazione di memoria di Windows viene registrata. Nella tabella seguente sono fornite informazioni sulle allocazioni di memoria eseguite solo utilizzando interfacce dello strumento di gestione della memoria di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Per chiamare questo oggetto [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] da [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]o, usare il nome **sys. dm_pdw_nodes_os_memory_nodes**.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**memory_node_id**|**smallint**|Specifica l'ID del nodo di memoria. Correlato all' **memory_node_id** di **sys. dm_os_memory_clerks**. Non ammette i valori NULL.|  
|**virtual_address_space_reserved_kb**|**bigint**|Indica il numero di indirizzi virtuali riservati, in kilobyte (KB), di cui non è stato eseguito il commit né il mapping a pagine fisiche. Non ammette i valori NULL.|  
|**virtual_address_space_committed_kb**|**bigint**|Specifica la quantità di indirizzo virtuale, in KB, di cui è stato eseguito il commit o il mapping a pagine fisiche. Non ammette i valori NULL.|  
|**locked_page_allocations_kb**|**bigint**|Specifica la quantità di memoria fisica, in KB, bloccata da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Non ammette i valori NULL.|  
|**single_pages_kb**|**bigint**|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Quantità di memoria riservata, in KB, allocata utilizzando l'allocatore di pagine singole da thread in esecuzione sul nodo. Questa memoria è allocata dal pool di buffer. Questo valore indica il nodo in cui si è verificata la richiesta di allocazione, non la posizione fisica in cui la richiesta di allocazione è stata soddisfatta.|  
|**pages_kb**|**bigint**|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e versioni successive.<br /><br /> Specifica la quantità di memoria di cui è stato eseguito il commit, in KB, allocata da questo nodo NUMA dall'allocatore di pagine del gestore della memoria. Non ammette i valori NULL.|  
|**multi_pages_kb**|**bigint**|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Quantità di memoria riservata, in KB, allocata utilizzando l'allocatore di più pagine da thread in esecuzione sul nodo. Questa memoria è esterna al pool di buffer. Questo valore indica il nodo in cui si sono verificate le richieste di allocazione, non la posizione fisica in cui le richieste di allocazione sono state soddisfatte.|  
|**shared_memory_reserved_kb**|**bigint**|Specifica la quantità di memoria condivisa del nodo, in KB, che è stata riservata. Non ammette i valori NULL.|  
|**shared_memory_committed_kb**|**bigint**|Specifica la quantità di memoria condivisa del nodo, in KB, di cui è stato eseguito il commit. Non ammette i valori NULL.|  
|**cpu_affinity_mask**|**bigint**|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e versioni successive.<br /><br /> Solo per uso interno. Non ammette i valori NULL.|  
|**online_scheduler_mask**|**bigint**|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e versioni successive.<br /><br /> Solo per uso interno. Non ammette i valori NULL.|  
|**processor_group**|**smallint**|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e versioni successive.<br /><br /> Solo per uso interno. Non ammette i valori NULL.|  
|**foreign_committed_kb**|**bigint**|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e versioni successive.<br /><br /> Viene specificata la quantità totale di memoria di cui è stato eseguito il commit, in KB, da altri nodi di memoria. Non ammette i valori NULL.|  
|**target_kb** |**bigint** |**Si applica a**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)] e versioni [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]successive.<br /><br /> Specifica l'obiettivo della memoria per il nodo di memoria, in KB. |   
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Identificatore del nodo su cui si trova questa distribuzione.|  
  
## <a name="permissions"></a>Autorizzazioni

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]è richiesta `VIEW SERVER STATE` l'autorizzazione.   
Nei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Premium, richiede l' `VIEW DATABASE STATE` autorizzazione nel database. Nei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli standard e Basic, richiede l' **amministratore del server** o un account **amministratore Azure Active Directory** .   

## <a name="see-also"></a>Vedere anche  
  [SQL Server viste a gestione dinamica relative al sistema operativo &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


