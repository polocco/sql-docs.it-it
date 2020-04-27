---
title: Gestione di soluzioni e oggetti di data mining | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], managing
- managing mining models
ms.assetid: 06fc61dd-925c-4347-8677-7046ee5d2f6f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 15574819cf0f0fec0d95fa2353c187cc55091e56
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66084200"
---
# <a name="management-of-data-mining-solutions-and-objects"></a>Gestione degli oggetti e delle soluzioni di data mining
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] include strumenti client che è possibile utilizzare per gestire strutture e modelli di data mining esistenti. In questa sezione vengono descritte le operazioni di gestione che è possibile eseguire utilizzando ciascun ambiente.  
  
 Oltre a questi strumenti, è possibile gestire a livello di programmazione oggetti di data mining mediante una libreria AMO o utilizzare gli altri client che si connettono a un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , ad esempio i componenti aggiuntivi Data mining per [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Spostamento di oggetti di data mining](moving-data-mining-objects.md)  
  
 [Requisiti e considerazioni sull'elaborazione &#40;data mining&#41;](processing-requirements-and-considerations-data-mining.md)  
  
 [Utilizzo di SQL Server Profiler per il monitoraggio di attività di data mining &#40;Analysis Services - Data Mining&#41;](using-sql-server-profiler-to-monitor-data-mining-analysis-services-data-mining.md)  
  
## <a name="location-of-data-mining-objects"></a>Percorso degli oggetti di data mining  
 Le strutture e i modelli di data mining elaborati vengono archiviati in un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Se si crea una connessione a un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database in `Immediate` modalità quando si sviluppano gli oggetti di data mining, tutti gli oggetti creati vengono immediatamente aggiunti al server mentre si lavora. Se invece si progettano oggetti di data mining in modalità **Offline** , ovvero l'impostazione predefinita quando si utilizza [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], gli oggetti di data mining creati sono solo contenitori di metadati fino a quando non vengono distribuiti a un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Pertanto, tutte le volte in cui si apporta una modifica a un oggetto, è necessario ridistribuire l'oggetto al server di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Per altre informazioni sull'architettura di data mining, vedere [Architettura fisica &#40;Analysis Services - Data Mining&#41;](physical-architecture-analysis-services-data-mining.md).  
  
> [!NOTE]  
>  Alcuni client, ad esempio i componenti aggiuntivi Data mining per [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007, consentono inoltre di creare modelli e strutture di data mining di sessione che usano una connessione a un'istanza, ma archiviano la struttura e i modelli nel server solo per la durata della sessione. Sebbene sia possibile gestire questi modelli tramite il client, analogamente alle strutture e ai modelli archiviati in un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , gli oggetti non vengono salvati in modo persistente dopo la disconnessione dall'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="managing-data-mining-objects-in-sql-server-data-tools"></a>Gestione di oggetti di data mining mediante gli strumenti dati di SQL Server  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] sono disponibili funzionalità che consentono di creare, esplorare e modificare oggetti di data mining in modo semplice.  
  
 I collegamenti seguenti consentono di accedere a informazioni sulla possibilità di modificare oggetti di data mining tramite [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]:  
  
-   [Modificare la vista origine dati utilizzata per una struttura di data mining](edit-the-data-source-view-used-for-a-mining-structure.md)  
  
-   [Modificare le proprietà di una struttura di data mining](change-the-properties-of-a-mining-structure.md)  
  
-   [Modificare le proprietà di un modello di data mining](change-the-properties-of-a-mining-model.md)  
  
-   [Visualizzare o modificare flag di modellazione &#40;Data mining&#41;](modeling-flags-data-mining.md)  
  
-   [Visualizzare o modificare i parametri dell'algoritmo](view-or-change-algorithm-parameters.md)  
  
 In genere si utilizzerà [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] come strumento per lo sviluppo di nuovi progetti e l'aggiunta a progetti esistenti, quindi per la gestione di progetti e oggetti distribuiti tramite strumenti quale [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Tuttavia, è possibile modificare direttamente gli oggetti già distribuiti a un'istanza di ssASnoversion tramite l'opzione `Immediate` e la connessione al server in modalità Online. Per ulteriori informazioni, vedere [Connect in Online Mode to an Analysis Services Database](../multidimensional-models/connect-in-online-mode-to-an-analysis-services-database.md).  
  
> [!WARNING]  
>  Per apportare qualsiasi modifica a una struttura oppure a un modello di data mining, incluse le modifiche di metadati, ad esempio un nome o una descrizione, è necessario rielaborare la struttura o il modello.  
  
 Se non si dispone del file della soluzione utilizzato per creare il progetto o gli oggetti di data mining, è possibile importare il progetto esistente dal server utilizzando la procedura guidata di importazione di Analysis Services, apportare modifiche agli oggetti, quindi eseguire nuovamente la distribuzione tramite l'opzione `Incremental`. Per altre informazioni, vedere [Importare un progetto di data mining usando l'Importazione guidata di Analysis Services](import-a-data-mining-project-using-the-analysis-services-import-wizard.md).  
  
## <a name="managing-data-mining-objects-in-sql-server-management-studio"></a>Gestione di oggetti di data mining mediante SQL Server Management Studio  
 In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]è possibile creare script per strutture e modelli di data mining, nonché elaborare o eliminare tali strutture e modelli. Sebbene sia possibile visualizzare solo un set limitato di proprietà utilizzando Esplora oggetti, per visualizzare metadati aggiuntivi relativi ai modelli di data mining è tuttavia possibile aprire una finestra **Query DMX** e selezionare una struttura di data mining.  
  
-   [Creare una query DMX in SQL Server Management Studio](create-a-dmx-query-in-sql-server-management-studio.md)  
  
## <a name="managing-data-mining-objects-programmatically"></a>Gestione di oggetti di data mining a livello di codice  
 È possibile creare, modificare, elaborare ed eliminare oggetti di data mining utilizzando i linguaggi di programmazione seguenti. Dal momento che ogni linguaggio è progettato per attività diverse, è possibile che siano presenti restrizioni relative al tipo di operazioni consentite. Non è ad esempio possibile modificare alcune proprietà degli oggetti di data mining utilizzando DMX (Data Mining Extensions). È infatti necessario utilizzare XMLA o AMO.  
  
### <a name="analysis-management-objects-amo"></a>AMO (Analysis Management Objects)  
 Gli oggetti AMO (Analysis Management Objects) sono un modello a oggetti compilato su XMLA che offre il controllo completo sugli oggetti di data mining. Tramite AMO, è possibile creare, distribuire e monitorare le strutture e i modelli di data mining.  
  
-   [Modello a oggetti AMO e concetti relativi](https://docs.microsoft.com/bi-reference/amo/amo-concepts-and-object-model)  
  
-   <xref:Microsoft.AnalysisServices>  
  
 **Restrizioni:** nessuna.  
  
### <a name="data-mining-extensions-dmx"></a>Data Mining Extensions (DMX)  
 È possibile utilizzare DMX con altre interfacce di comando, ad esempio [!INCLUDE[vstecado](../../includes/vstecado-md.md)] o ADOMD.Net, per creare, eliminare ed eseguire query su strutture e modelli di data mining.  
  
-   [Istruzioni DMX &#40;Data Mining Extensions&#41; per la definizione dei dati](/sql/dmx/dmx-statements-data-definition)  
  
 **Restrizioni:** alcune proprietà non possono essere modificate usando DMX.  
  
### <a name="xml-for-analysis-xmla"></a>XML for Analysis (XMLA)  
 XMLA (XML for Analysis) è il linguaggio DDL (Data Definition Language) per Analysis Services. XMLA consente di controllare la maggior parte degli oggetti di data mining e delle operazioni del server. Tutte le operazioni di gestione tra il client e il server possono essere eseguite tramite XMLA. Per semplicità è possibile usare il linguaggio ASSL ( [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language) per eseguire il wrapping degli elementi XML.  
  
 **Restrizioni:** [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] genera alcune istruzioni XMLA supportate solo per uso interno, che non possono essere usate negli script DDL XML.  
  
## <a name="see-also"></a>Vedi anche  
 [Guida per gli sviluppatori &#40;Analysis Services&#41;](../analysis-services-developer-documentation.md)  
  
  
