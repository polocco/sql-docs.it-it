---
title: Viste a gestione dinamica di SQL e Parallel data warehouse
ms.custom: seo-dt-2019
ms.date: 11/05/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: julieMSFT
ms.author: jrasnick
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: bbf63d4553630cce6d1d890f2d353442c14d6afd
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401618"
---
# <a name="sql-and-parallel-data-warehouse-dynamic-management-views"></a>Viste a gestione dinamica di SQL e Parallel data warehouse
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

In questo argomento vengono [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] elencate [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] le viste a gestione dinamica (DMV) e.  
  
 All [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] DMV iniziano con **sys. dm_pdw**.  
  
## <a name="sssdw-and-sspdw-dynamic-management-views"></a>[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] viste a gestione dinamica  
 Le viste a gestione dinamica seguenti si [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] applicano [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]sia a che a:  
  
 [sys. dm_pdw_dms_cores &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-dms-cores-transact-sql.md)  
  
 [sys. dm_pdw_dms_external_work &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-dms-external-work-transact-sql.md)  
  
 [sys. dm_pdw_dms_workers &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-dms-workers-transact-sql.md)  
  
 [sys. dm_pdw_errors &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md)  
  
 [sys. dm_pdw_exec_connections &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-connections-transact-sql.md)  
  
 [sys. dm_pdw_exec_requests &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)  
  
 [sys. dm_pdw_exec_sessions &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md)  
  
 [sys. dm_pdw_hadoop_operations &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-hadoop-operations-transact-sql.md)  
  
 [sys. dm_pdw_lock_waits &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-lock-waits-transact-sql.md)  
  
 [sys. dm_pdw_nodes &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)  
  
 [sys. dm_pdw_nodes_database_encryption_keys &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql.md)  
  
 [sys. dm_pdw_os_threads &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-os-threads-transact-sql.md)  
  
 [sys. dm_pdw_request_steps &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)  
  
 [sys. dm_pdw_resource_waits &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-resource-waits-transact-sql.md)  
  
 [sys. dm_pdw_sql_requests &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-sql-requests-transact-sql.md)  
  
 [sys. dm_pdw_sys_info &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-sys-info-transact-sql.md)  
  
 [sys. dm_pdw_wait_stats &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-wait-stats-transact-sql.md)  
  
 [sys. dm_pdw_waits &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md)

## <a name="sssdw-dynamic-management-views"></a>[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]Viste a gestione dinamica 
 Le viste a gestione dinamica seguenti si [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] applicano solo a:
 
[sys. dm_pdw_nodes_exec_query_plan &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-exec-query-plan-transact-sql.md)  

[sys. dm_pdw_nodes_exec_query_profiles &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-exec-query-profiles-transact-sql.md)  

[sys. dm_pdw_nodes_exec_query_statistics_xml &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-exec-query-statistics-xml-transact-sql.md)  

[sys. dm_pdw_nodes_exec_sql-text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-exec-sql-text-transact-sql.md)  

[sys. dm_pdw_nodes_exec_text_query_plan &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-exec-text-query-plan-transact-sql.md)

 [sys. dm_workload_management_workload_groups_stats &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-workload-management-workload-group-stats-transact-sql.md) (anteprima)

## <a name="sspdw-dynamic-management-views"></a>[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]Viste a gestione dinamica  
 Le viste a gestione dinamica seguenti si [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] applicano solo a:  
  
 [sys. dm_pdw_component_health_active_alerts &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-active-alerts-transact-sql.md)  
  
 [sys. dm_pdw_component_health_alerts &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-alerts-transact-sql.md)  
  
 [sys. dm_pdw_component_health_status &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-status-transact-sql.md)  
  
 [sys. dm_pdw_diag_processing_stats &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-diag-processing-stats-transact-sql.md)  
  
 [sys. dm_pdw_network_credentials &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md)  
  
 [sys. dm_pdw_node_status &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-node-status-transact-sql.md)  
  
 [sys. dm_pdw_os_event_logs &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-os-event-logs-transact-sql.md)  
  
 [sys. dm_pdw_os_performance_counters &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-os-performance-counters-transact-sql.md)  
  
 [sys. dm_pdw_query_stats_xe &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-query-stats-xe-transact-sql.md)  
  
 [sys. dm_pdw_query_stats_xe_file &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-query-stats-xe-file-transact-sql.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
