---
title: 'Lezione 5: compilazione di modelli di rete neurale e di regressione logistica (Esercitazione intermedia sul data mining) | Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logistic regression [Analysis Services]
- data mining [Analysis Services], tutorials
- neural networks
- tutorials [Data Mining]
- neural network model [Analysis Services]
ms.assetid: 42c3701a-1fd2-44ff-b7de-377345bbbd6b
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: daf554338a50a81f46d86a77bf04e770fcc2512e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "63137456"
---
# <a name="lesson-5-building-neural-network-and-logistic-regression-models-intermediate-data-mining-tutorial"></a>Lezione 5: Compilazione dei modelli di rete neurale e di regressione logistica (Esercitazione intermedia sul data mining)
  
  
 Il reparto operativo di [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] è coinvolto in un progetto per migliorare il livello di soddisfazione dei clienti del call center. La gestione del call center è stata affidata a un fornitore che deve anche raccogliere dati sull'efficienza del call center che dovranno essere analizzati. Si desidera sapere se sono presenti dati interessanti, in particolare se i dati suggeriscono problemi del personale o soluzioni per migliorare la soddisfazione dei clienti.  
  
 Il set di dati è piccolo e riguarda solo un periodo di 30 giorni di funzionamento del call center. I dati includono il numero di operatori esperti per ogni turno, il numero di chiamate in ingresso, il numero di ordini e i problemi che è necessario risolvere, nonché il tempo medio che un cliente attende che qualcuno risponda a una chiamata. I dati includono anche una metrica della qualità del servizio basata sulla *frequenza di abbandono*, che è un indicatore della frustrazione del cliente.  
  
 Poiché non esistono previsioni per i risultati dei dati, si decide di utilizzare un modello di rete neurale per esplorare le possibili correlazioni. I modelli di rete neurale vengono spesso utilizzati per l'esplorazione perché consentono di analizzare relazioni complesse tra molti input e output.  
  
## <a name="what-you-will-learn"></a>Lezioni dell'esercitazione  
 In questa lezione verrà utilizzato l'algoritmo Microsoft Neural Network per compilare un modello che sarà possibile utilizzare con il team del reparto operativo per comprendere i dati. In questa lezione si tenterà di rispondere alle domande seguenti:  
  
-   Quali fattori influiscono sulla soddisfazione dei clienti?  
  
-   Che cosa può fare il call center per migliorare la qualità del servizio?  
  
 In base ai risultati si compilerà quindi un modello di regressione logistica che risulterà utile per ottenere le stime che saranno utilizzate dal team operativo per supportare la pianificazione del funzionamento del call center.  
  
 In questa lezione sono inclusi gli argomenti seguenti:  
  
-   [Aggiunta di una vista origine dati per i dati del Call Center &#40;esercitazione intermedia sul data mining&#41;](../../2014/tutorials/add-data-source-view-call-center-data-intermediate-data-mining.md)  
  
-   [Creazione di una struttura e di un modello di rete neurale &#40;esercitazione intermedia sul data mining&#41;](../../2014/tutorials/creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [Esplorazione del modello di Call Center &#40;esercitazione intermedia sul data mining&#41;](../../2014/tutorials/exploring-the-call-center-model-intermediate-data-mining-tutorial.md)  
  
-   [Aggiunta di un modello di regressione logistica alla struttura del Call Center &#40;esercitazione intermedia sul data mining&#41;](../../2014/tutorials/add-logistic-regression-model-to-call-center-intermediate-data-mining.md)  
  
-   [Creazione di stime per i modelli di Call Center &#40;esercitazione intermedia sul data mining&#41;](../../2014/tutorials/create-predictions-call-center-models-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Aggiunta di una vista origine dati per i dati del Call Center &#40;esercitazione intermedia sul data mining&#41;](../../2014/tutorials/add-data-source-view-call-center-data-intermediate-data-mining.md)  
  
## <a name="all-lessons"></a>Tutte le lezioni  
 [Lezione 1: creazione della soluzione intermedia di data mining &#40;esercitazione intermedia sul data mining&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [Lezione 2: compilazione di uno scenario di previsione &#40;esercitazione intermedia sul data mining&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 [Lezione 3: Compilazione di uno scenario Market Basket &#40;Esercitazione intermedia sul data mining&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 [Lezione 4: compilazione di uno scenario di clustering delle sequenze &#40;esercitazione intermedia sul data mining&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 Lezione 5: Scenario di rete neurale e di regressione logistica (Esercitazione intermedia sul data mining)  
  
## <a name="see-also"></a>Vedi anche  
 [Esercitazione di base sul data mining](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [Esercitazione intermedia sul data mining &#40;Analysis Services-&#41;di data mining](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
