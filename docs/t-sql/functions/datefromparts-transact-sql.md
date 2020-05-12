---
title: DATEFROMPARTS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DATEFROMPARTS_TSQL
- DATEFROMPARTS
dev_langs:
- TSQL
helpviewer_keywords:
- DATEFROMPARTS function
ms.assetid: 5b885376-87aa-41f1-9e18-04987aead250
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a84fe60979d460030248ca9de912cd9d0b9d9acc
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82823219"
---
# <a name="datefromparts-transact-sql"></a>DATEFROMPARTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

Questa funzione restituisce un valore **date** che esegue il mapping ai valori year, month e day specificati.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DATEFROMPARTS ( year, month, day )  
```  
  
## <a name="arguments"></a>Argomenti  
*year*  
Espressione Integer che specifica un anno.
  
*month*  
Espressione Integer che specifica un mese, compreso tra 1 e 12.
  
*day*  
Espressione Integer che specifica un giorno.
  
## <a name="return-types"></a>Tipi restituiti
**date**
  
## <a name="remarks"></a>Osservazioni  
`DATEFROMPARTS` restituisce un valore **date**, con la parte relativa alla data impostata sull'anno, mese e giorno specificati e la parte relativa all'ora impostata sul valore predefinito. Per gli argomenti non validi, `DATEFROMPARTS` genererà un errore. `DATEFROMPARTS` restituisce null se almeno un argomento obbligatorio ha un valore null.
  
Questa funzione consente di gestire la comunicazione remota con i server [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e versioni successive. Non può gestire la comunicazione remota con server precedenti alla versione [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].
  
## <a name="examples"></a>Esempi  
Questo esempio illustrata la funzione `DATEFROMPARTS` in azione.
  
```sql
SELECT DATEFROMPARTS ( 2010, 12, 31 ) AS Result;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
Result  
----------------------------------  
2010-12-31  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche
[date &#40;Transact-SQL&#41;](../../t-sql/data-types/date-transact-sql.md)
  
  

