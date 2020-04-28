---
title: Errori e batch | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- batches [ODBC], errors
- sql_success_with_info [ODBC]
- sql_success [ODBC]
- SQL statements [ODBC], batches
- sql_error [ODBC]
ms.assetid: 6debd41d-9f4c-4f4c-a44b-2993da5306f0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 36a402686a695a08748df24a7b40a228d7a2ca7f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300431"
---
# <a name="errors-and-batches"></a>Errori e batch
Quando si verifica un errore durante l'esecuzione di un batch di istruzioni SQL, è possibile uno dei quattro risultati seguenti. Ogni possibile risultato è specifico dell'origine dati e può anche dipendere dalle istruzioni incluse nel batch.  
  
-   Nessuna istruzione nel batch viene eseguita.  
  
-   Nessuna istruzione del batch viene eseguita e viene eseguito il rollback della transazione.  
  
-   Vengono eseguite tutte le istruzioni prima dell'istruzione Error.  
  
-   Vengono eseguite tutte le istruzioni ad eccezione dell'istruzione Error.  
  
 Nei primi due casi **SQLExecute** e **SQLExecDirect** restituiscono SQL_ERROR. Negli ultimi due casi, possono restituire SQL_SUCCESS_WITH_INFO o SQL_SUCCESS, a seconda dell'implementazione. In tutti i casi, è possibile recuperare ulteriori informazioni sugli errori con **SQLGetDiagField**, **SQLGetDiagRec**o **SQLError**. Tuttavia, la natura e la profondità di queste informazioni sono specifiche dell'origine dati. Inoltre, è improbabile che queste informazioni identifichino esattamente l'istruzione in errore.
