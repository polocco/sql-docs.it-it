---
description: sys.workload_management_workload_classifiers (Transact-SQL)
title: sys.workload_management_workload_classifiers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/05/2019
ms.prod: sql
ms.technology: system-objects
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: 78811f776f7492cdcdba10a0f257e3d9a8f44aa7
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/14/2020
ms.locfileid: "92033850"
---
# <a name="sysworkload_management_workload_classifiers-transact-sql"></a>sys.workload_management_workload_classifiers (Transact-SQL)

[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

 Restituisce i dettagli per i classificatori del carico di lavoro.  
  
|Nome colonna|Tipo di dati|Descrizione|Range|  
|-----------------|---------------|-----------------|-----------|
|classifier_id|**int**|ID univoco del classificatore. Non ammette i valori Null||
group_name|**sysname**|Nome del gruppo di carico di lavoro a cui è assegnato il classificatore. Non ammette i valori Null. Joinbile a sys.workload_management_workload_groups ||
name|**sysname**|Nome del classificatore. Deve essere univoco per l'istanza. Non ammette i valori Null.||
|importance|**sysname**|È l'importanza relativa di una richiesta nel gruppo del carico di lavoro e nei gruppi di carico di lavoro per le risorse condivise.  L'importanza specificata nel classificatore sostituisce l'impostazione di importanza del gruppo di carico di lavoro. Ammette i valori Null.  Se è null, viene utilizzata l'impostazione di importanza del gruppo di carico di lavoro.|Low, below_normal, Normal (impostazione predefinita), above_normal, High |
|create_time|**datetime**|Ora di creazione del classificatore. Non ammette i valori Null.||
modify_time|**datetime**|Ora dell'Ultima modifica del classificatore. Non ammette i valori Null.||
is_enabled|**bit**|INTERNAL||
|&nbsp;||||
  
## <a name="permissions"></a>Autorizzazioni

È richiesta l'autorizzazione VIEW SERVER STATE.

## <a name="next-steps"></a>Passaggi successivi

 Per un elenco di tutte le viste del catalogo per analisi sinapsi di Azure e data warehouse parallele, vedere [analisi delle sinapsi di Azure e viste del catalogo data warehouse parallele](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md). Per creare un classificatore del carico di lavoro, vedere [creare un classificatore del carico di lavoro](../../t-sql/statements/create-workload-classifier-transact-sql.md). Per ulteriori informazioni sulla classificazione del carico di lavoro, vedere [classificazione dei carichi di lavoro](/azure/sql-data-warehouse/sql-data-warehouse-workload-classification)
