---
description: sys.dm_exec_background_job_queue_stats (Transact-SQL)
title: sys. dm_exec_background_job_queue_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_background_job_queue_stats
- sys.dm_exec_background_job_queue_stats
- dm_exec_background_job_queue_stats_TSQL
- sys.dm_exec_background_job_queue_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_background_job_queue_stats dynamic management view
ms.assetid: 27f62ab5-46c4-417e-814d-8d6437034d1c
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c79c0897f8be3997133cedaf54f42df55ea90486
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2020
ms.locfileid: "89534115"
---
# <a name="sysdm_exec_background_job_queue_stats-transact-sql"></a>sys.dm_exec_background_job_queue_stats (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Restituisce una riga in cui sono visualizzate le statistiche di aggregazione per ogni processo di Query Processor sottomesso per l'esecuzione asincrona (in background).  
  
> [!NOTE]  
>  Per chiamare questo [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oggetto da o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] , usare il nome **sys. dm_pdw_nodes_exec_background_job_queue_stats**.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**queue_max_len**|**int**|Lunghezza massima della coda.|  
|**enqueued_count**|**int**|Numero di richieste inviate correttamente alla coda.|  
|**started_count**|**int**|Numero di richieste di cui è stata avviata l'esecuzione.|  
|**ended_count**|**int**|Numero di richieste elaborate con esito positivo o con esito negativo.|  
|**failed_lock_count**|**int**|Numero di richieste non riuscite a causa di una contesta di blocchi o a causa di deadlock.|  
|**failed_other_count**|**int**|Numero di richieste non riuscite a causa di altri motivi.|  
|**failed_giveup_count**|**int**|Numero di richieste non riuscite perché è stato raggiunto il limite di tentativi.|  
|**enqueue_failed_full_count**|**int**|Numero di tentativi di accodamento non riusciti a causa della coda piena.|  
|**enqueue_failed_duplicate_count**|**int**|Numero di tentativi di accodamento duplicati.|  
|**elapsed_avg_ms**|**int**|Tempo medio trascorso della richiesta in millisecondi.|  
|**elapsed_max_ms**|**int**|Tempo trascorso della richiesta più lunga in millisecondi.|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] , [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Identificatore del nodo su cui si trova questa distribuzione.|  
  
## <a name="remarks"></a>Osservazioni  
 In questa vista vengono restituite solo le informazioni relative ai processi asincroni di aggiornamento delle statistiche. Per ulteriori informazioni sulle statistiche di aggiornamento asincrone, vedere [statistiche](../../relational-databases/statistics/statistics.md).  
  
## <a name="permissions"></a>Autorizzazioni

In è [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] richiesta l' `VIEW SERVER STATE` autorizzazione.   
Nei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Premium, richiede l' `VIEW DATABASE STATE` autorizzazione nel database. Nei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli standard e Basic, richiede l'  **amministratore del server** o un account **amministratore Azure Active Directory** .   

## <a name="examples"></a>Esempi  
  
### <a name="a-determining-the-percentage-of-failed-background-jobs"></a>R. Individuazione della percentuale di processi in background non riusciti  
 Nell'esempio seguente viene restituita la percentuale di processi in background non riusciti per tutte le query eseguite.  
  
```  
SELECT   
        CASE ended_count WHEN 0   
                THEN 'No jobs ended'   
                ELSE CAST((failed_lock_count + failed_giveup_count + failed_other_count) / CAST(ended_count AS float) * 100 AS varchar(20))   
        END AS [Percent Failed]  
FROM sys.dm_exec_background_job_queue_stats;  
GO  
```  
  
### <a name="b-determining-the-percentage-of-failed-enqueue-attempts"></a>B. Individuazione della percentuale di tentativi di accodamento non riusciti  
 Nell'esempio seguente viene restituita la percentuale di tentativi di accodamento non riusciti per tutte le query eseguite.  
  
```  
SELECT   
        CASE enqueued_count WHEN 0   
                THEN 'No jobs posted'   
                ELSE CAST((enqueue_failed_full_count + enqueue_failed_duplicate_count) / CAST(enqueued_count + enqueue_failed_full_count + enqueue_failed_duplicate_count AS float) * 100 AS varchar(20))   
        END AS [Percent Enqueue Failed]  
FROM sys.dm_exec_background_job_queue_stats;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Funzioni e viste a gestione dinamica relative all'esecuzione &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


