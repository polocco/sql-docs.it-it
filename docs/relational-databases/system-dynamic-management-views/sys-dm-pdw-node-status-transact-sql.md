---
title: sys. dm_pdw_node_status (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 8e263b65-81d0-49d0-8873-62ef424369d6
author: stevestein
ms.author: sstein
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4cd8788d19b06329d0280efc43a13a9a218e056c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "67899364"
---
# <a name="sysdm_pdw_node_status-transact-sql"></a>sys. dm_pdw_node_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Include informazioni aggiuntive (oltre a [sys. dm_pdw_nodes &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)) sulle prestazioni e lo stato di tutti i nodi del dispositivo. Elenca una riga per nodo nell'appliance.  
  
|Nome colonna|Tipo di dati|Descrizione|Range|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|ID numerico univoco associato al nodo.<br /><br /> Chiave per questa visualizzazione.|Univoco nell'appliance, indipendentemente dal tipo.|  
|process_id|**int**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|process_name|**nvarchar(255)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|allocated_memory|**bigint**|Memoria allocata totale in questo nodo.||  
|available_memory|**bigint**|Memoria totale disponibile in questo nodo.||  
|process_cpu_usage|**bigint**|Utilizzo totale della CPU del processo, in cicli.||  
|total_cpu_usage|**bigint**|Utilizzo totale della CPU, in cicli.||  
|thread_count|**bigint**|Numero totale di thread in uso in questo nodo.||  
|handle_count|**bigint**|Numero totale di handle in uso in questo nodo.||  
|total_elapsed_time|**bigint**|Tempo totale trascorso dall'avvio o dal riavvio del sistema.|Tempo totale trascorso dall'avvio o dal riavvio del sistema. Se total_elapsed_time supera il valore massimo per un numero intero (24,8 giorni in millisecondi), si verificherà un errore di materializzazione causato da un overflow.<br /><br /> Il valore massimo in millisecondi equivale a 24,8 giorni.|  
|is_available|**bit**|Flag che indica se il nodo è disponibile.||  
|sent_time|**datetime**|Ultima volta in cui un pacchetto di rete è stato inviato da questo nodo.||  
|received_time|**datetime**|Ora dell'ultima ricezione di un pacchetto di rete da questo nodo.||  
|error_id|**nvarchar (36)**|Identificatore univoco dell'ultimo errore che si è verificato in questo nodo.||  
  
## <a name="see-also"></a>Vedi anche  
 [SQL Data Warehouse e Parallel data warehouse viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
