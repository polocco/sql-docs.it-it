---
title: sys. dm_resource_governor_workload_groups_history_ex (database SQL di Azure) | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_workload_groups_history_ex_TSQL
- sys.dm_resource_governor_workload_groups_history_ex
- dm_resource_governor_workload_groups_history_ex
- dm_resource_governor_workload_groups_history_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_resource_governor_workload_groups_history_ex dynamic management view
author: joesackmsft
ms.author: josack
ms.openlocfilehash: 5fea5badf14ce9863f07dff189f1665788ec5fb6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "70873775"
---
# <a name="sysdm_resource_governor_workload_groups_history_ex-azure-sql-database"></a>sys.dm_resource_governor_workload_groups_history_ex (database SQL di Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Restituisce lo snapshot con intervallo di 20 secondi per gli ultimi 32 minuti (128 RECS in totale) delle statistiche dei pool di risorse per un database SQL di Azure.
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**pool_id**| INT |ID del pool di risorse. Non ammette i valori Null.|
|**group_id**| INT |ID del gruppo del carico di lavoro. Non ammette i valori Null.|
|**name**| nvarchar(256) |Nome del gruppo del carico di lavoro. Non ammette i valori Null.|
|**snapshot_time**| Datetime |Data/ora dello snapshot delle statistiche del gruppo di risorse.|
|**duration_ms**| INT |Durata tra lo snapshot corrente e quello precedente.|
|**active_worker_count**| INT |Totale ruoli di lavoro nello snapshot corrente.|
|**active_request_count**| INT |Conteggio corrente richieste. Non ammette i valori Null.|
|**active_session_count**| INT |Totale sessioni attive nello snapshot corrente.|
|**total_request_count**| bigint |Conteggio cumulativo delle richieste completate nel gruppo del carico di lavoro. Non ammette i valori Null.|
|**delta_request_count**| INT |Numero di richieste completate nel gruppo del carico di lavoro dall'ultimo snapshot. Non ammette i valori Null.|
|**total_cpu_usage_ms**| bigint |Utilizzo cumulativo della CPU, in millisecondi, da parte di questo gruppo del carico di lavoro. Non ammette i valori Null.|
|**delta_cpu_usage_ms**| INT |Utilizzo CPU in millisecondi dall'ultimo snapshot. Non ammette i valori Null.|
|**delta_cpu_usage_preemptive_ms**| INT |Le chiamate Win32 di tipo preemptive non governano dal RG della CPU SQL, dall'ultimo snapshot.|
|**delta_reads_reduced_memgrant_count**| INT |Conteggio delle concessioni di memoria che hanno raggiunto il limite massimo delle dimensioni della query dall'ultimo snapshot. Non ammette i valori Null.|
|**reads_throttled**| INT |Numero totale di letture limitate.|
|**delta_reads_queued**| INT |Il totale di letture IOs accodate dopo l'ultimo snapshot. Ammette i valori Null. Null se il gruppo di risorse non è governato per l'i/o.|
|**delta_reads_issued**| INT |Totale dei dispositivi IOs letti emessi dall'ultimo snapshot. Ammette i valori Null. Null se il gruppo di risorse non è governato per l'i/o.|
|**delta_reads_completed**| INT |Totale IOs di lettura completati dall'ultimo snapshot. Non ammette i valori Null.|
|**delta_read_bytes**| bigint |Numero totale di byte letti dall'ultimo snapshot. Non ammette i valori Null.|
|**delta_read_stall_ms**| INT |Tempo totale (in millisecondi) tra l'arrivo e il completamento dell'i/o di lettura dall'ultimo snapshot. Non ammette i valori Null.|
|**delta_read_stall_queued_ms**| INT |Tempo totale (in millisecondi) tra l'arrivo di i/o di lettura e il problema dall'ultimo snapshot. Ammette i valori Null. Null se il gruppo di risorse non è governato per l'i/o. Delta_read_stall_queued_ms diverso da zero significa che i/o sono interessati da RG.|
|**delta_writes_queued**| INT |Totale di scritture IOs accodate dall'ultimo snapshot. Ammette i valori Null. Null se il gruppo di risorse non è governato per l'i/o.|
|**delta_writes_issued**| INT |Il totale degli i/o di scrittura emessi dall'ultimo snapshot. Ammette i valori Null. Null se il gruppo di risorse non è governato per l'i/o.|
|**delta_writes_completed**| INT |Totale di operazioni di scrittura IOs completate dall'ultimo snapshot. Non ammette i valori Null.|
|**delta_writes_bytes**| bigint |Numero totale di byte scritti dall'ultimo snapshot. Non ammette i valori Null.|
|**delta_write_stall_ms**| INT |Tempo totale (in millisecondi) tra l'arrivo e il completamento i/o di scrittura dall'ultimo snapshot. Non ammette i valori Null.|
|**delta_background_writes**| INT |Totale scritture eseguite dalle attività in background dall'ultimo snapshot.|
|**delta_background_write_bytes**| bigint |Dimensioni totali di scrittura eseguite dalle attività in background dall'ultimo snapshot, in byte.|
|**delta_log_bytes_used**| bigint |Log usato dall'ultimo snapshot in byte.|
|**delta_log_temp_db_bytes_used**| bigint |Log tempdb utilizzato dall'ultimo snapshot in byte.|
|**delta_query_optimizations**| bigint |Numero di ottimizzazioni di query in questo gruppo del carico di lavoro dall'ultimo snapshot. Non ammette i valori Null.|
|**delta_suboptimal_plan_generations**| bigint |Numero di generazioni di piani non ottimali che si sono verificate in questo gruppo del carico di lavoro a causa di un utilizzo elevato di memoria dall'ultimo snapshot Non ammette i valori Null.
|**max_memory_grant_kb**| bigint |Concessione di memoria massima per il gruppo in KB.|
|**max_request_cpu_msec**| bigint |Limite massimo di utilizzo della CPU, in millisecondi, per una singola richiesta. Non ammette i valori Null.|
|**max_concurrent_request**| INT |Impostazione corrente per il numero massimo di richieste simultanee. Non ammette i valori Null.|
|**max_io**| INT |Limite massimo di i/o per il gruppo.|
|**max_global_io**| INT |Identificato solo a scopo informativo. Non supportato. Non è garantita la compatibilità con le versioni future.
|**max_queued_io**| INT |Identificato solo a scopo informativo. Non supportato. Non è garantita la compatibilità con le versioni future.|
|**max_log_rate_kb**| bigint |Frequenza massima di log (kilo-byte al sec) a livello di gruppo di risorse.|
|**max_session**| INT |Limite della sessione per il gruppo.|
|**max_worker**| INT |Limite di lavoro per il gruppo.|
|||

## <a name="permissions"></a>Autorizzazioni

Questa vista richiede l'autorizzazione VIEW SERVER STATE.

## <a name="remarks"></a>Osservazioni

Gli utenti possono accedere a questa vista a gestione dinamica per monitorare il consumo di risorse quasi in tempo reale per il pool di carico di lavoro degli utenti e per i pool interni di sistema dell'istanza del database SQL di Azure

> [!IMPORTANT]
> La maggior parte dei dati esposti da questa DMV è destinata al consumo interno ed è soggetta a modifiche.

## <a name="examples"></a>Esempi

Nell'esempio seguente vengono restituiti i dati di frequenza massima dei log e il consumo a ogni snapshot da parte del pool di utenti:

```sql
SELECT snapshot_time,
       name,
       max_log_rate_kb,
       delta_log_bytes_used
FROM sys.dm_resource_governor_workload_groups_history_ex
WHERE name LIKE 'User%'
ORDER BY snapshot_time DESC;
```

## <a name="see-also"></a>Vedere anche

- [Governance della frequenza di log delle traduzioni](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits-database-server#transaction-log-rate-governance)
- [Limiti delle risorse di DTU per pool elastico](https://docs.microsoft.com/azure/sql-database/sql-database-dtu-resource-limits-elastic-pools)
- [Limiti delle risorse di vCore per pool elastico](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-elastic-pools)
