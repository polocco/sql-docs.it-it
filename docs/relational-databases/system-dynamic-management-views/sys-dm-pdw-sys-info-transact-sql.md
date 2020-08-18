---
description: sys. dm_pdw_sys_info (Transact-SQL)
title: sys. dm_pdw_sys_info (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 686976b4-2d5d-4d64-bf12-56eba1dc59b1
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 0222938fe9e7b40b3982695e8e2bb47e86a2f078
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88397727"
---
# <a name="sysdm_pdw_sys_info-transact-sql"></a>sys. dm_pdw_sys_info (Transact-SQL)
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

  Fornisce un set di contatori a livello di appliance che riflettono l'attività complessiva nell'appliance.  
  
|Nome colonna|Tipo di dati|Descrizione|Range|  
|-----------------|---------------|-----------------|-----------|  
|total_sessions|**int**|Numero di sessioni attualmente presenti nel sistema.|da 0 a max_active_sessions (vedere di seguito).|  
|idle_sessions|**int**|Numero di sessioni attualmente inattive.||  
|active_requests|**int**|Numero di richieste attive attualmente in esecuzione.||  
|queued_requests|**int**|Numero di richieste attualmente accodate.||  
|active_loads|**int**|Numero di caricamenti attualmente in esecuzione nel sistema.||  
|queued_loads|**int**|Numero di caricamenti in coda in attesa di esecuzione.||  
|active_backups|**int**|Numero di backup attualmente in esecuzione.||  
|active_restores|**int**|Numero di ripristini di backup attualmente in esecuzione.||  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel data warehouse viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
