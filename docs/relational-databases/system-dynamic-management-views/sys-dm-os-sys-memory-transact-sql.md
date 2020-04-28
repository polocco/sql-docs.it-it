---
title: sys. dm_os_sys_memory (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_sys_memory
- sys.dm_os_sys_memory_TSQL
- sys.dm_os_sys_memory
- dm_os_sys_memory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_sys_memory dynamic management view
ms.assetid: 1ca58814-1caa-44c1-b307-ff0bdcbbef62
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 891ae8c4f21d0a38302a7213aab22b8a70e855ba
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "79027951"
---
# <a name="sysdm_os_sys_memory-transact-sql"></a>sys.dm_os_sys_memory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Restituisce le informazioni sulla memoria dal sistema operativo.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è vincolato da e risponde a condizioni di memoria esterna a livello di sistema operativo e di limiti fisici dell'hardware sottostante. La determinazione dello stato complessivo del sistema è un'importante parte della valutazione dell'utilizzo della memoria di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Per chiamare questo oggetto [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] da [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]o, usare il nome **sys. dm_pdw_nodes_os_sys_memory**.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**total_physical_memory_kb**|**bigint**|Dimensione totale della memoria fisica disponibile per il sistema operativo, espressa in kilobyte (KB).|  
|**available_physical_memory_kb**|**bigint**|Dimensione della memoria fisica disponibile, espressa in KB.|  
|**total_page_file_kb**|**bigint**|Dimensione del limite del commit riportata dal sistema operativo, espressa in KB|  
|**available_page_file_kb**|**bigint**|Quantità totale di file di paging non utilizzati, in KB.|  
|**system_cache_kb**|**bigint**|Totale di memoria cache del sistema, espressa in KB.|  
|**kernel_paged_pool_kb**|**bigint**|Totale del pool paginato del kernel, espresso in KB.|  
|**kernel_nonpaged_pool_kb**|**bigint**|Totale del pool non paginato del kernel, espresso in KB.|  
|**system_high_memory_signal_state**|**bit**|Stato della notifica relativa alle risorse elevate della memoria di sistema. Un valore 1 indica che Windows ha impostato un segnale di memoria elevato. Per ulteriori informazioni, vedere [CreateMemoryResourceNotification](https://go.microsoft.com/fwlink/?LinkId=82427) in MSDN Library.|  
|**system_low_memory_signal_state**|**bit**|Stato della notifica relativa alle risorse insufficienti della memoria di sistema. Un valore 1 indica che Windows ha impostato un segnale di memoria basso. Per ulteriori informazioni, vedere [CreateMemoryResourceNotification](https://go.microsoft.com/fwlink/?LinkId=82427) in MSDN Library.|  
|**system_memory_state_desc**|**nvarchar(256)**|Descrizione dello stato della memoria. Vedere la tabella riportata di seguito.|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Identificatore del nodo su cui si trova questa distribuzione.|  
  
|Condizione|valore|  
|---------------|-----------|  
|system_high_memory_signal_state = 1<br /><br /> e<br /><br /> system_low_memory_signal_state = 0|La quantità di memoria fisica disponibile è elevata.|  
|system_high_memory_signal_state = 0<br /><br /> e<br /><br /> system_low_memory_signal_state = 1|La quantità di memoria fisica disponibile è bassa.|  
|system_high_memory_signal_state = 0<br /><br /> e<br /><br /> system_low_memory_signal_state = 0|L'utilizzo della memoria fisica è costante|  
|system_high_memory_signal_state = 1<br /><br /> e<br /><br /> system_low_memory_signal_state = 1|La stato della memoria fisica è in fase di transizione<br /><br /> Il segnale massimo e minimo non devono mai essere attivi contemporaneamente. Tuttavia, modifiche rapide a livello di sistema operativo possono fare sì che entrambi i valori sembrino essere attivi in un'applicazione della modalità utente. La visualizzazione di entrambi i segnali attivi verrà interpretata come una stato della transizione.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="see-also"></a>Vedere anche  
 [Viste a gestione dinamica e funzioni &#40;&#41;Transact-SQL](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [SQL Server viste a gestione dinamica relative al sistema operativo &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


