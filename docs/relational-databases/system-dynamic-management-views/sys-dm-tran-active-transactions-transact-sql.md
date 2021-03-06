---
description: sys.dm_tran_active_transactions (Transact-SQL)
title: sys.dm_tran_active_transactions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_tran_active_transactions
- sys.dm_tran_active_transactions_TSQL
- dm_tran_active_transactions_TSQL
- dm_tran_active_transactions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_tran_active_transactions dynamic management view
ms.assetid: 154ad6ae-5455-4ed2-b014-e443abe2c6ee
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7980a8013f43083498e5147cad39a60471b681ec
ms.sourcegitcommit: 968969b62bc158b9843aba5034c9d913519bc4a7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/06/2020
ms.locfileid: "91753783"
---
# <a name="sysdm_tran_active_transactions-transact-sql"></a>sys.dm_tran_active_transactions (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Restituisce informazioni sulle transazioni per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Per chiamare questo [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oggetto da o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] , usare il nome **sys.dm_pdw_nodes_tran_active_transactions**.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|transaction_id|**bigint**|ID della transazione a livello di istanza, non a livello di database. È univoco solo in tutti i database all'interno di un'istanza, ma non tra tutte le istanze del server.|  
|name|**nvarchar(32)**|Nome della transazione. Viene sovrascritto se la transazione è contrassegnata e il nome contrassegnato sostituisce il nome della transazione.|  
|transaction_begin_time|**datetime**|Ora di avvio della transazione.|  
|transaction_type|**int**|Tipo di transazione.<br /><br /> 1 = Transazione di lettura/scrittura<br /><br /> 2 = Transazione di sola lettura<br /><br /> 3 = Transazione di sistema<br /><br /> 4 = Transazione distribuita|  
|transaction_uow|**uniqueidentifier**|Identificatore dell'unità di lavoro della transazione per le transazioni distribuite. MS DTC utilizza l'identificatore dell'unità di lavoro per gestire la transazione distribuita.|  
|transaction_state|**int**|0 = La transazione non è stata ancora inizializzata completamente.<br /><br /> 1 = La transazione è stata inizializzata ma non è stata avviata.<br /><br /> 2 = La transazione è attiva.<br /><br /> 3 = La transazione è terminata. Viene utilizzato per le transazioni di sola lettura.<br /><br /> 4 = Il processo di commit è stato inizializzato nella transazione distribuita. Riservato solo alle transazioni distribuite. La transazione distribuita è ancora attiva, ma non può essere ulteriormente elaborata.<br /><br /> 5 = La transazione è in uno stato preparato ed è in attesa di risoluzione.<br /><br /> 6 = è stato eseguito il commit della transazione.<br /><br /> 7 = L'esecuzione del rollback della transazione è in corso.<br /><br /> 8 = è stato eseguito il rollback della transazione.|  
|transaction_status|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|transaction_status2|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|dtc_state|**int**|**Si applica a**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] (dalla versione iniziale alla [versione corrente](/previous-versions/azure/ee336279(v=azure.100))).<br /><br /> 1 = ACTIVE<br /><br /> 2 = PREPARED<br /><br /> 3 = COMMITTED<br /><br /> 4 = ABORTED<br /><br /> 5 = RECOVERED|  
|dtc_status|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|dtc_isolation_level|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|filestream_transaction_id|**varbinary(128)**|**Si applica a**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] (dalla versione iniziale alla [versione corrente](/previous-versions/azure/ee336279(v=azure.100))).<br /><br /> [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|pdw_node_id|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] , [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Identificatore del nodo su cui si trova questa distribuzione.|  
  
## <a name="permissions"></a>Autorizzazioni

In è [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] richiesta l' `VIEW SERVER STATE` autorizzazione.   
Nei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Premium, richiede l' `VIEW DATABASE STATE` autorizzazione nel database. Nei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli standard e Basic, richiede l'  **amministratore del server** o un account **amministratore Azure Active Directory** .   
  
## <a name="see-also"></a>Vedere anche  
 [sys.dm_tran_session_transactions &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-tran-session-transactions-transact-sql.md)   
 [sys.dm_tran_database_transactions &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-tran-database-transactions-transact-sql.md)   
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Funzioni e viste a gestione dinamica relative alle transazioni &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)  
  
