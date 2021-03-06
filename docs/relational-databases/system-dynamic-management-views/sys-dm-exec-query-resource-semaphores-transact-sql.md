---
description: sys.dm_exec_query_resource_semaphores (Transact-SQL)
title: sys. dm_exec_query_resource_semaphores (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_query_resource_semaphores_TSQL
- dm_exec_query_resource_semaphores_TSQL
- sys.dm_exec_query_resource_semaphores
- dm_exec_query_resource_semaphores
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_resource_semaphores dynamic management view
ms.assetid: e43a2aa9-dd52-4c89-911e-1a7d05f7ffbb
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6d782c81ce803441e91d6008ae5b0117522c3286
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2020
ms.locfileid: "89548550"
---
# <a name="sysdm_exec_query_resource_semaphores-transact-sql"></a>sys.dm_exec_query_resource_semaphores (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Vengono restituite le informazioni sullo stato del semaforo per le risorse query corrente in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **sys. dm_exec_query_resource_semaphores** fornisce lo stato generale della memoria di esecuzione delle query e consente di determinare se il sistema è in grado di accedere a memoria sufficiente. Questa visualizzazione integra le informazioni sulla memoria ottenute da [sys. dm_os_memory_clerks](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md) per fornire un quadro completo dello stato della memoria del server. **sys. dm_exec_query_resource_semaphores** restituisce una riga per il semaforo di risorsa normale e un'altra riga per il semaforo di risorse di query di piccole dimensioni. Esistono due requisiti per un semaforo di query di piccole dimensioni:  
  
-   La concessione di memoria richiesta deve essere inferiore a 5 MB  
  
-   Il costo della query deve essere inferiore a 3 unità di costo  
  
> [!NOTE]  
>  Per chiamare questo [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oggetto da o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] , usare il nome **sys. dm_pdw_nodes_exec_query_resource_semaphores**.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**resource_semaphore_id**|**smallint**|ID non univoco del semaforo di risorsa. È uguale a 0 per il semaforo di risorsa normale e a 1 per il semaforo di risorsa per query di dimensioni ridotte.|  
|**target_memory_kb**|**bigint**|Destinazione di utilizzo della concessione di memoria, espressa in kilobyte.|  
|**max_target_memory_kb**|**bigint**|Destinazione potenziale massima, espressa in kilobyte. È NULL per il semaforo di risorsa per query di dimensioni ridotte.|  
|**total_memory_kb**|**bigint**|Memoria utilizzata dal semaforo di risorsa, espressa in kilobyte. Se il sistema è sottoposto a un numero eccessivo di richieste di memoria o se la memoria minima forzata viene concessa di frequente, questo valore può essere maggiore dei valori **target_memory_kb** o **max_target_memory_kb** . La memoria totale è la somma della memoria disponibile e della memoria concessa.|  
|**available_memory_kb**|**bigint**|Memoria disponibile per una nuova concessione, espressa in kilobyte.|  
|**granted_memory_kb**|**bigint**|Memoria totale concessa, espressa in kilobyte.|  
|**used_memory_kb**|**bigint**|Parte fisica della memoria concessa, espressa in kilobyte.|  
|**grantee_count**|**int**|Numero di query attive a cui è stata concessa la memoria richiesta.|  
|**waiter_count**|**int**|Numero di query in attesa che venga concessa la memoria richiesta.|  
|**timeout_error_count**|**bigint**|Numero complessivo di errori di timeout dall'avvio del server. È NULL per il semaforo di risorsa per query di dimensioni ridotte.|  
|**forced_grant_count**|**bigint**|Numero complessivo di concessioni di memoria minima dall'avvio del server. È NULL per il semaforo di risorsa per query di dimensioni ridotte.|  
|**pool_id**|**int**|ID del pool di risorse a cui appartiene il semaforo di risorsa.|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] , [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Identificatore del nodo su cui si trova questa distribuzione.|  
  
## <a name="permissions"></a>Autorizzazioni  

In è [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] richiesta l' `VIEW SERVER STATE` autorizzazione.   
Nei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Premium, richiede l' `VIEW DATABASE STATE` autorizzazione nel database. Nei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli standard e Basic, richiede l'  **amministratore del server** o un account **amministratore Azure Active Directory** .   
  
## <a name="remarks"></a>Osservazioni  
 Le query che utilizzano viste a gestione dinamica che includono clausole ORDER BY o funzioni di aggregazione potrebbero aumentare l'utilizzo della memoria, contribuendo di conseguenza a causare il problema che dovrebbero risolvere.  
  
 Utilizzare **sys. dm_exec_query_resource_semaphores** per la risoluzione dei problemi ma non includerla nelle applicazioni che utilizzeranno versioni future di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 La funzionalità Resource Governor consente a un amministratore di database di distribuire risorse del server fra un massimo di 64 pool di risorse. In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e versioni successive, ogni pool si comporta come una piccola istanza indipendente del server e richiede 2 semafori.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica relative all'esecuzione &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_query_memory_grants &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)  
  
  


