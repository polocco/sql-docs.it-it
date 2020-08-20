---
description: DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD (Transact-SQL)
title: DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD  (Transact-SQL)
ms.custom: seo-dt-2019
ms.date: 07/03/2019
ms.prod: sql
ms.technology: data-warehouse
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 2a849fdf387361bdf217e1b40a81aa8c600931d3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88479854"
---
# <a name="dbcc-pdw_showmaterializedviewoverhead-transact-sql"></a>DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD (Transact-SQL)  

[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

Visualizza il numero di modifiche incrementali nelle tabelle di base che vengono mantenute per le viste materializzate in [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. Il rapporto di overhead viene calcolato come TOTAL_ROWS / MAX (1, BASE_VIEW_ROWS).

![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi

```syntaxsql
DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD ( " [ schema_name .] materialized_view_name  " )
[;]
```

## <a name="arguments"></a>Argomenti

 *schema_name*     
 Nome dello schema a cui appartiene la vista.

*materialized_view_name*   
Nome della vista materializzata.

## <a name="remarks"></a>Commenti

Per mantenere aggiornate le viste materializzate in base alle modifiche ai dati nelle tabelle di base, il motore del data warehouse aggiunge righe di rilevamento a ogni vista interessata per riflettere le modifiche. La selezione da una vista materializzata include l'analisi dell'indice columnstore cluster della vista e l'applicazione di modifiche incrementali.Le righe di rilevamento (TOTAL_ROWS - BASE_VIEW_ROWS) non vengono eliminate finché gli utenti non ricompilano la vista materializzata.  

Il rapporto di overhead viene calcolato come TOTAL_ROWS/MAX(1, BASE_VIEW_ROWS).  Se è alto, le prestazioni di SELECT risulteranno ridotte.Gli utenti possono ricompilare la vista materializzata per ridurre il relativo rapporto di overhead.

## <a name="permissions"></a>Autorizzazioni  
  
È richiesta l'autorizzazione VIEW DATABASE STATE.  

## <a name="examples"></a>Esempi  

### <a name="a-this-example-returns-the-overhead-ratio-of-a-materialized-view"></a>R. Questo esempio restituisce il rapporto di overhead di una vista materializzata.

```sql
DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD ( "dbo.MyIndexedView" )
```

Output:

|OBJECT_ID|BASE_VIEW_ROWS|TOTAL_ROWS|OVERHEAD_RATIO|
|--------|--------|--------|--------|  
|1234|1|3 |3.0 |

</br>

### <a name="b-this-example-shows-how-the-materialized-view-overhead-increases-as-data-changes-in-base-tables"></a>B. Questo esempio mostra come l'overhead della vista materializzata aumenta per effetto delle modifiche ai dati nelle tabelle di base

Creare una tabella
```sql
CREATE TABLE t1 (c1 int NOT NULL, c2 int not null, c3 int not null)
```
Inserire cinque righe in t1
```sql
INSERT INTO t1 VALUES (1, 1, 1)
INSERT INTO t1 VALUES (2, 2, 2) 
INSERT INTO t1 VALUES (3, 3, 3) 
INSERT INTO t1 VALUES (4, 4, 4) 
INSERT INTO t1 VALUES (5, 5, 5) 
```
Creare viste materializzate MV1
```sql
CREATE materialized view MV1 
WITH (DISTRIBUTION = HASH(c1))  
AS
SELECT c1, count(*) total_number 
FROM dbo.t1 where c1 < 3
GROUP BY c1  
```
La selezione dalla vista materializzata restituisce due righe.

|c1|total_number|
|--------|--------| 
|1|1| 
|2|1|

Controllare l'overhead della vista materializzata prima di eventuali modifiche ai dati nella tabella di base.
```sql
DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD ("dbo.mv1")
```
Output:

|OBJECT_ID|BASE_VIEW_ROWS|TOTAL_ROWS|OVERHEAD_RATIO|
|--------|--------|--------|--------|  
|587149137|2|2 |1.00000000000000000 |

Aggiornare la tabella di base.  Questa query aggiorna 100 volte la stessa colonna nella stessa riga impostando lo stesso valore.  Il contenuto della vista materializzata non cambia.
```sql
DECLARE @p int
SELECT @p = 1
WHILE (@p < 101)
BEGIN
UPDATE t1 SET c1 = 1 WHERE c1 = 1
SELECT @p = @p+1
END  
```

La selezione dalla vista materializzata restituisce lo stesso risultato dell'esempio precedente.  

|c1|total_number|
|--------|--------| 
|1|1| 
|2|1|

Di seguito è riportato l'output di DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD ("dbo.mv1").  Alla vista materializzata sono state aggiunte 100 righe (total_row - base_view_rows) e il relativo valore di overhead_ratio è aumentato. 

|OBJECT_ID|BASE_VIEW_ROWS|TOTAL_ROWS|OVERHEAD_RATIO|
|--------|--------|--------|--------|  
|587149137|2|102 |51.00000000000000000 |

Dopo la ricompilazione della vista materializzata, vengono eliminate tutte le righe di rilevamento per le modifiche incrementali ai dati e il rapporto di overhead della vista viene ridotto.  

```sql
ALTER MATERIALIZED VIEW dbo.MV1 REBUILD
go
DBCC PDW_SHOWMATERIALIZEDVIEWOVERHEAD ("dbo.mv1")
```
Output

|OBJECT_ID|BASE_VIEW_ROWS|TOTAL_ROWS|OVERHEAD_RATIO|
|--------|--------|--------|--------|  
|587149137|2|2 |1.00000000000000000 |

## <a name="see-also"></a>Vedere anche

[Ottimizzazione delle prestazioni con vista materializzata](/azure/sql-data-warehouse/performance-tuning-materialized-views)   
[CREATE MATERIALIZED VIEW AS SELECT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-materialized-view-as-select-transact-sql?view=azure-sqldw-latest)   
[ALTER MATERIALIZED VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-materialized-view-transact-sql?view=azure-sqldw-latest)   
[EXPLAIN &#40;Transact-SQL&#41;](/sql/t-sql/queries/explain-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_column_distribution_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-column-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_distribution_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-distribution-properties-transact-sql?view=azure-sqldw-latest)   
[sys.pdw_materialized_view_mappings &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-pdw-materialized-view-mappings-transact-sql?view=azure-sqldw-latest)   
[Viste del catalogo di SQL Data Warehouse e Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
[Viste di sistema supportate in Azure SQL Data Warehouse](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-system-views)   
[Istruzioni T-SQL supportate in Azure SQL Data Warehouse](/azure/sql-data-warehouse/sql-data-warehouse-reference-tsql-statements)
