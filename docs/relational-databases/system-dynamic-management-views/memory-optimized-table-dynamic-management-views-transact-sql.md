---
title: Viste a gestione dinamica della tabella con ottimizzazione per la memoria (Transact-SQL)
ms.custom: seo-dt-2019
ms.date: 02/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: ccd82fed-1a3f-47de-85c4-1c9bdd80b027
author: stevestein
ms.author: sstein
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4981203eb0712eb1989959af38117d12f05bf9cb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "74412833"
---
# <a name="memory-optimized-table-dynamic-management-views-transact-sql"></a>Viste a gestione dinamica correlate alle tabelle con ottimizzazione per la memoria (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

  Le viste [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a gestione dinamica (DMV) seguenti vengono usate con OLTP in memoria:  
  
 Per altre informazioni, vedere [OLTP in memoria &#40;ottimizzazione in memoria&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
|||  
|-|-|   
|[sys. dm_db_xtp_checkpoint_stats &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-stats-transact-sql.md)|[sys. dm_db_xtp_checkpoint_files &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-checkpoint-files-transact-sql.md)|
|[sys. dm_db_xtp_gc_cycle_stats &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-gc-cycle-stats-transact-sql.md)|[sys.dm_db_xtp_hash_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-hash-index-stats-transact-sql.md)| 
|[sys.dm_db_xtp_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-index-stats-transact-sql.md)|[sys.dm_db_xtp_memory_consumers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-memory-consumers-transact-sql.md)|
|[sys.dm_db_xtp_merge_requests (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-merge-requests-transact-sql.md)|[sys.dm_db_xtp_object_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-object-stats-transact-sql.md)|
|[sys.dm_db_xtp_nonclustered_index_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-nonclustered-index-stats-transact-sql.md)|[sys.dm_db_xtp_table_memory_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-table-memory-stats-transact-sql.md)|  
|[sys. dm_db_xtp_transactions &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-transactions-transact-sql.md)|[sys. dm_xtp_gc_queue_stats &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-queue-stats-transact-sql.md)|  
|[sys. dm_xtp_gc_stats &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-gc-stats-transact-sql.md)|[sys. dm_xtp_system_memory_consumers &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-system-memory-consumers-transact-sql.md)|
|[sys. dm_xtp_transaction_stats &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-xtp-transaction-stats-transact-sql.md)||

### <a name="object-catalog-views"></a>Viste del catalogo per gli oggetti

Le viste del catalogo di oggetti seguenti vengono usate in modo specifico con OLTP in memoria.

|||  
|-|-|   
|[sys.hash_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-hash-indexes-transact-sql.md)|[sys.memory_optimized_tables_internal_attributes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-memory-optimized-tables-internal-attributes-transact-sql.md)|  

### <a name="internal-dmvs"></a>DMV interno

Sono disponibili DMV aggiuntive destinate solo all'uso interno e per le quali non viene fornita alcuna documentazione diretta. Nell'area delle tabelle ottimizzate per la memoria, i DMV non documentati includono quanto segue:

- sys. dm_xtp_threads
- sys. dm_xtp_transaction_recent_rows

