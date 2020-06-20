---
title: Modellazione tabulare (SSAS tabulare) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 80027288-c203-4667-a3e1-40fa572b4975
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44f358f0f36e84ad903a0a4fcb0203291019e7aa
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84938496"
---
# <a name="tabular-modeling-ssas-tabular"></a>Modellazione tabulare (SSAS tabulare)
  I modelli tabulari sono database in memoria in Analysis Services. Utilizzando un processore di query multithreading e algoritmi di compressione all'avanguardia, il motore di analisi in memoria xVelocity (VertiPaq) offre accesso rapido ai dati e agli oggetti del modello tabulare mediante applicazioni client di creazione di report quali Microsoft Excel e Microsoft [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].  
  
 I modelli tabulari supportano l'accesso ai dati tramite due modalità, ovvero cache e DirectQuery. In modalità cache, è possibile integrare i dati da più origini, tra cui database relazionali, feed di dati e file di testo. In modalità DirectQuery, è possibile ignorare il modello in memoria, consentendo l'esecuzione di una query sui dati direttamente nell'origine (database relazionale di SQL Server) da parte delle applicazioni client.  
  
 I modelli tabulari vengono creati in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] utilizzando nuovi modelli relativi al modello di progetto tabulare. È possibile importare i dati da più origini e migliorare il modello aggiungendo relazioni, colonne calcolate, misure, indicatori KPI e gerarchie. I modelli possono quindi essere distribuiti in un'istanza di Analysis Services dove, tramite applicazioni client di creazione di report, è possibile effettuare la connessione a tali modelli. I modelli distribuiti possono essere gestiti in SQL Server Management Studio solo come modelli multidimensionali. Tali modelli, inoltre, possono essere partizionati per elaborazioni ottimizzate e protetti a livello di riga tramite ruoli basati sulla sicurezza.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Soluzioni di modelli tabulari &#40;SSAS tabulare&#41;](../tabular-model-solutions-ssas-tabular.md)  
  
 [Database modello tabulare &#40;SSAS tabulare&#41;](tabular-model-databases-ssas-tabular.md)  
  
 [Accesso ai dati di modello tabulare](tabular-model-data-access.md)  
  
  
