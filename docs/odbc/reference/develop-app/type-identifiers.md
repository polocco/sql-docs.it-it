---
description: Identificatori di tipi
title: Identificatori di tipo | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- type identifiers [ODBC]
- identifiers [ODBC], type
- type identifiers [ODBC], about type identifiers
ms.assetid: 1d9fdfa2-e378-44fe-ac66-9743d9bbdd5a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4ed41716cd351631578d01027663aa9e0f028c7d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487444"
---
# <a name="type-identifiers"></a>Identificatori di tipi
Per descrivere i tipi di dati SQL e C, ODBC definisce due set di *identificatori di tipo*. Un identificatore di tipo descrive il tipo di una colonna SQL o di un buffer C. Si tratta di un valore **#define** e viene in genere passato come argomento della funzione o restituito nei metadati.  
  
 Ad esempio, la chiamata seguente a **SQLBindParameter** associa una variabile di tipo SQL_DATE_STRUCT a un parametro date in un'istruzione SQL. L'identificatore di tipo C SQL_C_TYPE_DATE specifica il tipo della variabile di *Data* e l'identificatore del tipo SQL SQL_TYPE_DATE specifica il tipo del parametro dinamico.  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER  DateInd = 0;  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 0, 0,  
                  &Date, 0, &DateInd);  
```
