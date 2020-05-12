---
title: GROUPING (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/03/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- GROUPING
- GROUPING_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- null values [SQL Server], GROUPING function
- grouping columns
- ROLLUP operator
- GROUP BY clause, GROUPING function
- GROUPING function
- CUBE operator
ms.assetid: 4efa3868-1fc4-4626-8fb1-e863cc03e422
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: dd8046a013dab94bb25f4733cf9b8d49fb7bbaad
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82823151"
---
# <a name="grouping-transact-sql"></a>GROUPING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Indica se un'espressione della colonna specificata in un elenco GROUP BY è aggregata. GROUPING restituisce 1 per le espressioni aggregate o 0 per le espressioni non aggregate nel set di risultati. È possibile usare GROUPING solo in un elenco di \<selezione> SELECT e nelle clausole HAVING e ORDER BY quando GROUP BY è specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
GROUPING ( <column_expression> )  
```  
  
## <a name="arguments"></a>Argomenti  
 \<column_expression>  
 Colonna o espressione che contiene una colonna in una clausola [GROUP BY](../../t-sql/queries/select-group-by-transact-sql.md).  
  
## <a name="return-types"></a>Tipi restituiti  
 **tinyint**  
  
## <a name="remarks"></a>Osservazioni  
 GROUPING viene utilizzato per distinguere i valori Null restituiti da ROLLUP, CUBE o GROUPING SETS dai valori Null standard. Il risultato NULL restituito da un'operazione ROLLUP, CUBE o GROUPING SETS rappresenta un utilizzo particolare dei valori NULL. Funge infatti da segnaposto di colonna nel set di risultati e corrisponde a "tutti".  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono raggruppati gli importi di `SalesQuota` e aggregati gli importi di `SaleYTD` nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. La funzione `GROUPING` viene applicata alla colonna `SalesQuota`.  
  
```  
SELECT SalesQuota, SUM(SalesYTD) 'TotalSalesYTD', GROUPING(SalesQuota) AS 'Grouping'  
FROM Sales.SalesPerson  
GROUP BY SalesQuota WITH ROLLUP;  
GO  
```  
  
 Il set di risultati include due valori Null per `SalesQuota`. Il primo valore `NULL` rappresenta il gruppo di valori Null che derivano dalla colonna della tabella, il secondo valore `NULL` è incluso nella riga di riepilogo aggiunta dall'operazione ROLLUP. La riga di riepilogo indica gli importi della colonna `TotalSalesYTD` per tutti i gruppi `SalesQuota` ed è rappresentata dal valore `1` nella colonna `Grouping`.  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 SalesQuota     TotalSalesYTD       Grouping  
------------   -----------------   --------  
NULL           1533087.5999          0  
250000.00      33461260.59           0  
300000.00      9299677.9445          0  
NULL           44294026.1344         1  

(4 row(s) affected)
```  
  
## <a name="see-also"></a>Vedere anche  
 [GROUPING_ID &#40;Transact-SQL&#41;](../../t-sql/functions/grouping-id-transact-sql.md)   
 [GROUP BY &#40;Transact-SQL&#41;](../../t-sql/queries/select-group-by-transact-sql.md)  
  
  
