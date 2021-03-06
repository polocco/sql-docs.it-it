---
description: Tipi di dati intervallo
title: Tipi di dati interval | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- second intervals [ODBC]
- data types [ODBC], interval data types
- interval data type [ODBC]
- day-time intervals [ODBC]
- intervals [ODBC], about intervals
- minute intervals [ODBC]
- day intervals [ODBC]
- year intervals [ODBC]
- month intervals [ODBC]
- interval data type [ODBC], about interval data types
- SQL data types [ODBC], interval
- year-month intervals [ODBC]
- C data types [ODBC], interval
- interval fields [ODBC]
ms.assetid: fba93f65-c1db-44f4-91ba-532f87241cf7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5b54996c2f2897e47e05088b1985d190acafaad3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429673"
---
# <a name="interval-data-types"></a>Tipi di dati intervallo
Un intervallo viene definito come la differenza tra due date e ore. Gli intervalli sono espressi in uno dei due modi diversi. Uno è un intervallo di *anno del mese* che esprime gli intervalli in termini di anni e un numero integrale di mesi. L'altro è un intervallo di *tempo* che esprime gli intervalli in termini di giorni, minuti e secondi. Questi due tipi di intervalli sono distinti e non possono essere misti, perché i mesi possono avere un numero di giorni variabile.  
  
 Un intervallo è costituito da un set di campi. Esiste un ordinamento implicito tra i campi. Ad esempio, in un intervallo di anno in mese, l'anno viene raggiunto per primo, seguito dal mese. Analogamente, in un intervallo giornaliero, i campi sono inclusi nell'ordine giorno, ora e minuto. Il primo campo in un tipo di intervallo viene chiamato campo *iniziale* o il campo di *ordine superiore* . L'ultimo campo è denominato campo *finale* .  
  
 A tutti gli intervalli, il campo principale non è vincolato dalle regole del calendario gregoriano. Ad esempio, in un intervallo di ore al minuto, il campo dell'ora non è vincolato a un valore compreso tra 0 e 23 (inclusi), in quanto normalmente è. I campi finali successivi al campo principale seguono i normali vincoli del calendario gregoriano. Per ulteriori informazioni, vedere [Constraints of the Gregorian Calendar](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md), più avanti in questa appendice.  
  
 Sono disponibili 13 tipi di dati SQL intervallo e 13 tipi di dati intervallo C. Ognuno dei tipi di dati intervallo C utilizza la stessa struttura, SQL_INTERVAL_STRUCT, per contenere i dati relativi all'intervallo. Per ulteriori informazioni, vedere la sezione successiva, [struttura intervallo C](../../../odbc/reference/appendixes/c-interval-structure.md). Per ulteriori informazioni sui tipi di dati SQL, vedere [tipi di dati SQL](../../../odbc/reference/appendixes/sql-data-types.md). Per ulteriori informazioni sui tipi di dati C, vedere [tipi di dati c](../../../odbc/reference/appendixes/c-data-types.md).  
  
|Identificatore di tipo|Class|Descrizione|  
|---------------------|-----------|-----------------|  
|MONTH|Anno mese|Numero di mesi tra due date.|  
|YEAR|Anno mese|Numero di anni tra due date.|  
|YEAR_TO_MONTH|Anno mese|Numero di anni e mesi tra due date.|  
|DAY|Giorno-ora|Numero di giorni tra due date.|  
|HOUR|Giorno-ora|Numero di ore tra due data/ora.|  
|MINUTE|Giorno-ora|Numero di minuti tra due date/ore.|  
|SECOND|Giorno-ora|Numero di secondi tra due date/ore.|  
|DAY_TO_HOUR|Giorno-ora|Numero di giorni/ore tra due data/ora.|  
|DAY_TO_MINUTE|Giorno-ora|Numero di giorni/ore/minuti tra due data/ora.|  
|DAY_TO_SECOND|Giorno-ora|Numero di giorni/ore/minuti/secondi tra due data e ora.|  
|HOUR_TO_MINUTE|Giorno-ora|Numero di ore/minuti tra due date/ore.|  
|HOUR_TO_SECOND|Giorno-ora|Numero di ore/minuti/secondi tra due data/ora.|  
|MINUTE_TO_SECOND|Giorno-ora|Numero di minuti/secondi tra due date/ore.|  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Struttura C Interval](../../../odbc/reference/appendixes/c-interval-structure.md)  
  
-   [Precisione del tipo di dati intervallo](../../../odbc/reference/appendixes/interval-data-type-precision.md)  
  
-   [Lunghezza del tipo di dati intervallo](../../../odbc/reference/appendixes/interval-data-type-length.md)  
  
-   [Valori letterali intervallo](../../../odbc/reference/appendixes/interval-literals.md)  
  
-   [Override della precisione iniziale e in secondi predefinita per i tipi di dati intervallo](../../../odbc/reference/appendixes/overriding-default-leading-and-seconds-precision-for-interval-data-types.md)
