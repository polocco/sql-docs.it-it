---
description: SEQUENZE (Transact-SQL)
title: SEQUENZE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- SEQUENCES
- SEQUENCES_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SEQUENCES view
- INFORMATION_SCHEMA.SEQUENCES view
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7fa13582e155387bbe7b7122e0051d830be2261b
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2020
ms.locfileid: "89546335"
---
# <a name="sequences-transact-sql"></a>SEQUENZE (Transact-SQL)

[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Restituisce una riga per ogni sequenza a cui è possibile accedere dall'utente corrente nel database corrente.

Per recuperare informazioni da queste viste, specificare il nome completo di **INFORMATION_SCHEMA**_. view_name_.

|Nome colonna|Tipo di dati|Descrizione|
|-----------------|---------------|-----------------|
|**SEQUENCE_CATALOG**|**nvarchar(128)**|Qualificatore sequenza|
|**SEQUENCE_SCHEMA**|**nvarchar (** 128) * *|Nome dello schema che contiene la sequenza|
|**SEQUENCE_NAME**|**nvarchar(128)**|Nome sequenza|
|**DATA_TYPE**|**nvarchar (** 128 **)**|Tipo di dati Sequence|
|**NUMERIC_PRECISION**|**tinyint**|Precisione della sequenza|
|**NUMERIC_PRECISION_RADIX**|**smallint**|Base di precisione dei dati numerici approssimati, dei dati numerici esatti, dei dati integer o dei dati in valuta. Per gli altri tipi di dati viene restituito NULL.|
|**NUMERIC_SCALE**|**int**|Scala dei dati numerici approssimati, dei dati numerici esatti, dei dati integer o dei dati in valuta. Per gli altri tipi di dati viene restituito NULL.|
|**START_VALUE**|**int**|Primo valore che verrà restituito dall'oggetto sequenza.|
|**MINIMUM_VALUE**|**int**|Limiti per l'oggetto sequenza. Il valore minimo predefinito per un nuovo oggetto sequenza è il valore minimo del tipo di dati dell'oggetto sequenza. Tale valore è zero per il tipo di dati tinyint e un numero negativo per tutti gli altri tipi di dati.|
|**MAXIMUM_VALUE**|**int**|Limiti per l'oggetto sequenza. Il valore massimo predefinito per un nuovo oggetto sequenza è il valore massimo del tipo di dati dell'oggetto sequenza.|
|**INCREMENTO**|**int**|Valore utilizzato per incrementare (o diminuire se negativo) il valore dell'oggetto sequenza per ogni chiamata alla funzione NEXT VALUE FOR. Se l'incremento è un valore negativo, l'oggetto sequenza presenta un ordine decrescente. In caso contrario, l'ordine sarà crescente. L'incremento non può essere 0. L'incremento predefinito per un nuovo oggetto sequenza è 1.
|**CYCLE_OPTION**|**int**|Proprietà che specifica se l'oggetto sequenza deve riprendere dal valore minimo (o massimo per gli oggetti sequenza con ordine decrescente) o generare un'eccezione quando viene superato il relativo valore massimo o minimo. L'opzione predefinita che determina la ripresa dei nuovi oggetti sequenza è NO CYCLE.
|**DECLARED_DATA_TYPE**|**int**|Tipo di dati per il tipo di dati definito dall'utente.|
|**DECLARED_DATA_PRECISION**|**int**|Precisione per il tipo di dati definito dall'utente.|
|**DECLARED_NUJMERIC_SCALE**|**int**|Scala numerica per il tipo di dati definito dall'utente.|

**Esempio** Nell'esempio seguente vengono restituite informazioni sugli schemi nel database di prova:

```sql
SELECT * FROM test.INFORMATION_SCHEMA.SEQUENCES;
```

## <a name="see-also"></a>Vedere anche

- [Viste degli schemi delle informazioni &#40;&#41;Transact-SQL ](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)
- [sys.sequences &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sequences-transact-sql.md)
