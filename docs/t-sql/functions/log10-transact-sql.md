---
title: LOG10 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- LOG10
- LOG10_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- float expressions
- LOG10 function
- base-10 logarithms
- logarithm of expression
ms.assetid: 1eb7fb34-1937-4a39-a936-f5c0c7c7e06f
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 277a29cf91151e606fa79f4d27494dda3aa29859
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82822839"
---
# <a name="log10-transact-sql"></a>LOG10 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce il logaritmo in base 10 dell'espressione **float** specificata.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
LOG10 ( float_expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *float_expression*  
 [Espressione](../../t-sql/language-elements/expressions-transact-sql.md) di tipo **float** oppure di un tipo che può essere convertito in modo implicito in **float**.  
  
## <a name="return-types"></a>Tipi restituiti  
 **float**  
  
## <a name="remarks"></a>Osservazioni  
 Le funzioni LOG10 e POWER sono inversamente correlate. Ad esempio, 10 ^ LOG10(*n*) = *n*.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-calculating-the-base-10-logarithm-for-a-variable"></a>R. Calcolo del logaritmo in base 10 per una variabile.  
 Nell'esempio seguente viene calcolato il valore `LOG10` della variabile specificata.  
  
```  
DECLARE @var float;  
SET @var = 145.175643;  
SELECT 'The LOG10 of the variable is: ' + CONVERT(varchar,LOG10(@var));  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
The LOG10 of the variable is: 2.16189      
  
(1 row(s) affected)  
```  
  
### <a name="b-calculating-the-result-of-raising-a-base-10-logarithm-to-a-specified-power"></a>B. Calcolo del risultato dell'elevamento di un logaritmo in base 10 alla potenza specificata.  
 Nell'esempio seguente viene restituito il risultato dell'elevamento di un logaritmo in base 10 alla potenza specificata.  
  
```  
SELECT POWER (10, LOG10(5));   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-----------  
5  
  
(1 row(s) affected)  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-calculating-the-base-10-logarithm-for-a-value"></a>C: Calcolo del logaritmo in base 10 per un valore.  
 Nell'esempio seguente viene calcolato il valore `LOG10` del valore specificato.  
  
```  
SELECT LOG10(145.175642);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
-------------------  
2.16
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni matematiche &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)   
 [POWER &#40;Transact-SQL&#41;](../../t-sql/functions/power-transact-sql.md)   
 [LOG &#40;Transact-SQL&#41;](../../t-sql/functions/log-transact-sql.md)  
  
  

