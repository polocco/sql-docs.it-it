---
description: Pagina Espressioni
title: Pagina Espressioni | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.expressionspage.f1
helpviewer_keywords:
- Expressions Page dialog box
ms.assetid: c9016ec6-11c1-4ebd-b2a7-0fa6631fd9e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 23afd7d406cc201615b696961f7c3fe1072f9ba9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88425513"
---
# <a name="expressions-page"></a>Pagina Espressioni

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Usare la pagina **Espressioni** per modificare le espressioni di proprietà e accedere alle finestre di dialogo **Editor espressioni di proprietà** e **Property Expression Builder** (Generatore di espressioni di proprietà).  
  
 Le espressioni di proprietà aggiornano i valori delle proprietà durante l'esecuzione del pacchetto. È possibile utilizzare queste espressioni con le proprietà di pacchetti, attività, contenitori, gestioni connessioni e alcuni componenti del flusso di dati. Le espressioni vengono valutate e i risultati vengono utilizzati in sostituzione dei valori che sono stati impostati per le proprietà alla configurazione del pacchetto e dei relativi oggetti. Nelle espressioni possono essere presenti variabili e le funzioni e gli operatori forniti dal linguaggio delle espressioni. È possibile, ad esempio, generare la riga Oggetto di un'attività Invia messaggi concatenando il valore di una variabile contenente la stringa "Previsioni del tempo per:" e i risultati restituiti dalla funzione GETDATE() per ottenere la stringa "Previsioni del tempo per: 4/5/2006".  
  
 Per altre informazioni sulla scrittura di espressioni e sull'utilizzo di espressioni di proprietà, vedere [Espressioni di Integration Services &#40;SSIS&#41;](../../integration-services/expressions/integration-services-ssis-expressions.md) e [Utilizzo delle espressioni di proprietà nei pacchetti](../../integration-services/expressions/use-property-expressions-in-packages.md).  
  
## <a name="options"></a>Opzioni  
 **Espressioni (...)**  
 Fare clic sui puntini di sospensione per aprire la finestra di dialogo **Editor espressioni di proprietà** . Per altre informazioni, vedere [Editor espressioni di proprietà](../../integration-services/expressions/property-expressions-editor.md).  
  
 **\<property name>**  
 Fare clic sui puntini di sospensione per aprire la finestra di dialogo **Generatore di espressioni** . Per altre informazioni, vedere [Generatore di espressioni](../../integration-services/expressions/expression-builder.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md)   
 [Variabili di sistema](../../integration-services/system-variables.md)   
 [Espressioni di Integration Services &#40;SSIS&#41;](../../integration-services/expressions/integration-services-ssis-expressions.md)  
  
  
