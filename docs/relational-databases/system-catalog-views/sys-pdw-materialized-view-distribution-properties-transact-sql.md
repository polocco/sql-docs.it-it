---
description: sys.pdw_materialized_view_distribution_properties (Transact-SQL) (anteprima)
title: sys.pdw_materialized_view_distribution_properties (Transact-SQL)
ms.custom: seo-dt-2019
ms.date: 07/03/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d62b0e25-3226-4f87-a10a-b3a0d9555e19
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: ad934310f5bd4b5628efdf28788eff9ac7aa2503
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/14/2020
ms.locfileid: "92036977"
---
# <a name="syspdw_materialized_view_distribution_properties-transact-sql-preview"></a>sys.pdw_materialized_view_distribution_properties (Transact-SQL) (anteprima)

[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

Visualizza le visualizzazioni materializzate delle informazioni di distribuzione.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------| 
|object_id|**int**|ID della vista materializzata per cui sono state specificate le proprietà.| 
|distribution_policy |**tinyint**|2 = HASH</br>4 = ROUND_ROBIN|  
|distribution_policy_desc |**nvarchar(60)**|HASH, ROUND_ROBIN|  
 
## <a name="permissions"></a>Autorizzazioni

È richiesta l'autorizzazione VIEW DATABASE STATE.
 
## <a name="see-also"></a>Vedere anche

[CREATE MATERIALIZED VIEW AS SELECT &#40;Transact-SQL&#41;](../../t-sql/statements/create-materialized-view-as-select-transact-sql.md?view=azure-sqldw-latest)   
[ALTER MATERIALIZED VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/alter-materialized-view-transact-sql.md?view=azure-sqldw-latest)   
[EXPLAIN &#40;Transact-SQL&#41;](../../t-sql/queries/explain-transact-sql.md?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_mappings &#40;Transact-SQL&#41;](./sys-pdw-materialized-view-mappings-transact-sql.md?view=azure-sqldw-latest)   
[DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-pdw-showmaterializedviewoverhead-transact-sql.md?view=azure-sqldw-latest)   
[Viste del catalogo di Azure Synapse Analytics e Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
[Viste di sistema supportate in Azure Synapse Analytics](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-system-views)   
[Istruzioni T-SQL supportate in Azure Synapse Analytics](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-statements)