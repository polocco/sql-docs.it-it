---
title: Data mining (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], about data mining
ms.assetid: b1c912da-72f6-4d96-89c8-55a2c4f19e88
author: minewiskan
ms.author: owend
ms.openlocfilehash: 447b350aae97ded341788dd4b398441d6b1efdb2
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2020
ms.locfileid: "84522671"
---
# <a name="data-mining-ssas"></a>Data mining (SSAS)
  In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è disponibile una piattaforma integrata per le soluzioni in cui è incorporato il data mining. Per creare soluzioni di Business Intelligence con analisi predittiva è possibile utilizzare i dati relazionali o del cubo.  
  
## <a name="benefits-of-data-mining"></a>Vantaggi del data mining  
 Nel data mining vengono utilizzati principi statistici analizzati in modo approfondito per individuare modelli nei dati, consentendo di prendere decisioni intelligenti sui problemi complessi. Applicando gli algoritmi di data mining di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ai dati, è possibile prevedere tendenze, identificare modelli, creare regole e indicazioni, analizzare la sequenza di eventi in set di dati complessi e acquisire nuovi approfondimenti.  
  
 In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]il data mining è efficace, accessibile e integrato con gli strumenti preferiti dagli utenti per l'analisi e la creazione di report. Per ottenere un'utile panoramica generale sul data mining che si desidera avviare, vedere i collegamenti di questa sezione.  
  
## <a name="key-data-mining-features"></a>Caratteristiche principali del data mining  
 In SQL Server sono disponibili le caratteristiche seguenti per il supporto di soluzioni di data mining integrate:  
  
-   Più origini dati: non è necessario creare un data warehouse o un cubo OLAP per eseguire il data mining. È possibile utilizzare dati tabulari forniti da provider esterni o disponibili in fogli di calcolo o addirittura file di testo. È anche possibile eseguire il processo di data mining di cubi OLAP creati in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Tuttavia, non è possibile usare i dati di un database in memoria.  
  
-   Pulizia dati integrata, gestione dati ed ETL: in Data Quality Services sono disponibili strumenti avanzati per il profiling e la pulizia dei dati. Integration Services può essere utilizzato per compilare processi ETL per la pulizia dei dati, nonché per la compilazione, l'elaborazione, il training e l'aggiornamento di modelli.  
  
-   Più algoritmi personalizzabili: oltre a fornire algoritmi quali quelli di clustering, reti neurali e alberi delle decisioni, la piattaforma supporta lo sviluppo di algoritmi plug-in personalizzati.  
  
-   Infrastruttura di test del modello: testare i modelli e i set di dati utilizzando importanti strumenti statistici come la convalida incrociata, le matrici di classificazione, i grafici di accuratezza e a dispersione. Creare e gestire facilmente i set di testing e di training.  
  
-   Esecuzione di query e drill-through: creare query di stima, recuperare schemi e statistiche del modello ed eseguire il drill-through nei dati del case.  
  
-   Strumenti client: oltre agli strumenti di sviluppo e progettazione forniti da SQL Server, è possibile utilizzare i componenti aggiuntivi Data mining per Excel per creare ed esplorare i modelli, nonché per eseguirvi query. In alternativa creare client personalizzati, inclusi i servizi Web.  
  
-   Supporto del linguaggio di scripting e API gestita: tutti gli oggetti di data mining sono completamente programmabili. La generazione di script è possibile tramite MDX, XMLA o le estensioni PowerShell per [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Utilizzare il linguaggio DMX (Data Mining Extensions) per eseguire query e generare script velocemente.  
  
-   Sicurezza e distribuzione: tramite [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]viene fornita la sicurezza basata su ruoli, incluse autorizzazioni separate relative al drill-through per i dati del modello e della struttura. Distribuzione semplice di modelli agli altri server, in modo che gli utenti possano accedere agli schemi o effettuare stime  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 Negli argomenti di questa sezione sono illustrate le caratteristiche principali di Data mining di SQL Server e le attività correlate.  
  
-   [Concetti relativi al data mining](data-mining-concepts.md)  
  
-   [Algoritmi di data mining &#40;Analysis Services - Data mining&#41;](data-mining-algorithms-analysis-services-data-mining.md)  
  
-   [Strutture di data mining &#40;Analysis Services - Data mining&#41;](mining-structures-analysis-services-data-mining.md)  
  
-   [Modelli di data mining &#40;Analysis Services - Data mining&#41;](mining-models-analysis-services-data-mining.md)  
  
-   [Test e convalida &#40;Data mining&#41;](testing-and-validation-data-mining.md)  
  
-   [Query di data mining](data-mining-queries.md)  
  
-   [Soluzioni di data mining](data-mining-solutions.md)  
  
-   [Strumenti di data mining](data-mining-tools.md)  
  
-   [Architettura di data mining](data-mining-architecture.md)  
  
-   [Panoramica della sicurezza &#40;data mining&#41;](security-overview-data-mining.md)  
  
  
