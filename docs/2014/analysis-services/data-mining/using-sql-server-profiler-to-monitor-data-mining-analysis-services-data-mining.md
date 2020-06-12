---
title: Utilizzo di SQL Server Profiler per monitorare il data mining (Analysis Services-Data mining) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], Analysis Services
ms.assetid: 655ac93c-5c5c-4565-914b-915327f7d349
author: minewiskan
ms.author: owend
ms.openlocfilehash: 136f81e374878a9af8241175f1519c87a266515f
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2020
ms.locfileid: "84520181"
---
# <a name="using-sql-server-profiler-to-monitor-data-mining-analysis-services---data-mining"></a>Utilizzo di SQL Server Profiler per il monitoraggio di attività di data mining (Analysis Services - Data mining)
  Se si dispone delle autorizzazioni necessarie, è possibile utilizzare SQL Server Profiler per monitorare le attività di data mining emesse come richieste inviate a un'istanza di SQL Server Analysis Services. L'attività di data mining può includere l'elaborazione di modelli o strutture, query di stima o sul contenuto oppure la creazione di nuovi modelli o strutture.  
  
 In SQL Server Profiler viene utilizzato un oggetto `trace` per monitorare le richieste inviate da più client, tra cui [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], SQL Server Management Studio, servizi Web o componenti aggiuntivi Data Mining per Excel, a condizione che per tutte le attività venga utilizzata la stessa istanza di SQL Server Analysis Services. È necessario creare una traccia separata per ciascuna istanza di SQL Server Analysis Services da monitorare. Per informazioni generali sulle tracce e su come usare SQL Server Profiler, vedere [Usare SQL Server Profiler per il monitoraggio di Analysis Services](../instances/use-sql-server-profiler-to-monitor-analysis-services.md).  
  
 Per informazioni specifiche sui tipi di eventi da acquisire, vedere [Creare tracce del profiler per la riproduzione &#40;Analysis Services&#41;](../instances/create-profiler-traces-for-replay-analysis-services.md).  
  
## <a name="using-traces-to-monitor-data-mining"></a>Utilizzo di tracce per il monitoraggio di data mining  
 Quando si acquisiscono informazioni contenute in una traccia, è possibile specificare se salvare le informazioni in un file o in una tabella di un'istanza di SQL Server. A prescindere dal metodo di archiviazione dei dati, è possibile utilizzare SQL Server Profiler per visualizzare la traccia e filtrarla in base agli eventi. Nella tabella seguente sono elencati alcuni eventi e sottoclassi contenuti nella traccia [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] predefinita di interesse per il data mining.  
  
|EventClass|EventSubclass|Descrizione|  
|----------------|-------------------|-----------------|  
|**Inizio query**<br /><br /> **Fine query**|**0 - MDXQuery**|Contiene il testo di tutte le chiamate a stored procedure [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|**Inizio query**<br /><br /> **Fine query**|**1 - DMXQuery**|Contiene il testo e i risultati di istruzioni DMX (Data Mining Extensions).|  
|**Progress Report Begin**<br /><br /> **Progress Report End**|**34 - DataMiningProgress**|Fornisce informazioni sullo stato di avanzamento dell'algoritmo di data mining: durante la compilazione di un modello di clustering: ad esempio, il messaggio di stato segnala il cluster in corso di compilazione|  
|**Inizio query**<br /><br /> **Fine query**|EXECUTESQL|Contiene il testo della query Transact-SQL in esecuzione|  
|**Inizio query**<br /><br /> **Fine query**|**2-SQLQuery**|Contiene il testo delle query sui set di righe dello schema nel formato di tabelle del sistema.|  
|**INDIVIDUA inizio**<br /><br /> **DISCOVER End**|Multipli|Contiene il testo di chiamate di funzioni DMX o istruzioni DISCOVER, incapsulate in XMLA.|  
|**Erroree**|(nessuna)|Contiene il testo degli errori inviati dal server al client.<br /><br /> I messaggi di errore preceduti da **Errore (data mining):** o **Messaggio informativo (data mining):** sono generati in maniera specifica in risposta a richieste DMX. La sola visualizzazione di questi messaggi di errore non è tuttavia sufficiente, perché altri errori, quali quelli generati dal parser, potrebbero essere correlati al data mining senza questi prefissi.|  
  
 La visualizzazione delle istruzioni di comando nel registro di traccia consente di visualizzare anche la sintassi di istruzioni complesse inviate dal client al server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , comprese chiamate alle stored procedure di sistema. Queste informazioni possono essere utili per il debug oppure è possibile utilizzare le istruzioni valide come modello per la creazione di nuove query o modelli di stima. Per alcuni esempi di chiamate alle stored procedure acquisibili tramite traccia, vedere [Esempi di query sul modello di clustering](clustering-model-query-examples.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare un'istanza di Analysis Services](../instances/monitor-an-analysis-services-instance.md)   
 [Usare SQL Server eventi estesi &#40;&#41; XEvent per monitorare Analysis Services](../instances/monitor-analysis-services-with-sql-server-extended-events.md)  
  
  
