---
description: sys.trace_categories (Transact-SQL)
title: sys. trace_categories (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- trace_categories
- trace_categories_TSQL
- sys.trace_categories
- sys.trace_categories_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trace_categories catalog view
ms.assetid: f6a86766-e2a9-4d9f-a073-1b59e888ba7d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: a7f9b84010eb7d562dccb2f22c2e04bcadff2a1c
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2020
ms.locfileid: "89544985"
---
# <a name="systrace_categories-transact-sql"></a>sys.trace_categories (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Classi di evento simili vengono raggruppate in base a una categoria specifica. Ogni riga della vista del catalogo **sys. trace_categories** identifica una categoria univoca sul server. Queste categorie non cambiano per una versione specifica di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
 Per un elenco completo degli eventi di traccia supportati, vedere [SQL Server riferimento alla classe di evento](../../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
> **IMPORTANTE** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] In alternativa, utilizzare le viste del catalogo di Eventi estesi.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**category_id**|**smallint**|ID univoco della categoria. Questa colonna si trova anche nella vista del catalogo **sys. trace_events** .|  
|**nome**|**nvarchar(128)**|Nome univoco della categoria. Questo parametro non è localizzato.|  
|**type**|**tinyint**|Tipo di categoria:<br /><br /> 0 = normale<br /><br /> 1 = connessione<br /><br /> 2 = errore|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo dell'oggetto &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys. Traces &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-traces-transact-sql.md)   
 [sys. trace_columns &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-trace-columns-transact-sql.md)   
 [sys. trace_events &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-trace-events-transact-sql.md)   
 [sys. trace_event_bindings &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-trace-event-bindings-transact-sql.md)   
 [sys. trace_subclass_values &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-trace-subclass-values-transact-sql.md)  
  
  
