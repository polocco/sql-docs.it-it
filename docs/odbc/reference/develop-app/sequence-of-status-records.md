---
description: Sequenza di record di stato
title: Sequenza di record di stato | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 0e0436cc-230f-44b0-b373-04a57e83ee76
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b2cb519cab987a1abd924f1b779a7f07c3201475
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476453"
---
# <a name="sequence-of-status-records"></a>Sequenza di record di stato
Se vengono restituiti due o più record di stato, la gestione driver e il driver vengono classificati in base alle regole seguenti. Il record con il rango più alto è il primo record. L'origine di un record (Gestione driver, driver, gateway e così via) non viene considerata quando i record di rango.  
  
-   **Errori** di I record di stato che descrivono errori hanno il rango più alto. Tra i record degli errori, i record che indicano un errore di transazione o un possibile errore di transazione classificano tutti gli altri record. Se due o più record descrivono la stessa condizione di errore, gli stati definiti dalla specifica dell'interfaccia della riga di comando per il gruppo aperto (classi da 03 a HZ) sono in grado di classificare sqlstati definiti da ODBC e definiti dal driver.  
  
-   **Implementazione-nessun valore di dati definito** I record di stato che descrivono i valori di dati non definiti dal driver (classe 02) hanno il secondo rango più alto.  
  
-   **Avvisi** di I record di stato che descrivono gli avvisi (classe 01) hanno il rango più basso. Se due o più record descrivono la stessa condizione di avviso, gli avvisi SQLSTATE definiti dalla specifica dell'interfaccia della riga di comando per il gruppo Open definiscono la definizione di SQLSTATE definito da ODBC e dal driver.  
  
 Se sono presenti due o più record con il rango più alto, non è definito quale record è il primo record. L'ordine di tutti gli altri record non è definito. In particolare, poiché gli avvisi possono essere visualizzati prima degli errori, le applicazioni devono controllare tutti i record di stato quando una funzione restituisce un valore diverso da SQL_SUCCESS.
