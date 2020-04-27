---
title: Creazione guidata modello di data mining (Analysis Services-Data mining) | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], data mining
- OLAP [Analysis Services], mining models
- Data Mining Wizard
- relational mining models [Analysis Services]
ms.assetid: d5fea90f-5f38-4639-8851-7707f6606a12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: eb853898d91533a61ae220ff2d73c032f2c65330
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66084736"
---
# <a name="data-mining-wizard-analysis-services---data-mining"></a>Creazione guidata modello di data mining (Analysis Services - Data mining)
  La creazione guidata modello di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data mining in viene avviata ogni volta che si aggiunge una nuova struttura di data mining a un progetto data mining. La procedura guidata consente di scegliere un'origine dati e di configurare una vista origine dati per definire i dati da utilizzare per l'analisi, quindi consente di creare un modello iniziale.  
  
 Nella fase finale della procedura guidata, è possibile dividere facoltativamente i dati in set di training e di testing e abilitare funzionalità quali il drill-through.  
  
## <a name="what-to-know-before-you-start"></a>Nozioni preliminari  
 Di seguito sono riportate le nozioni che è necessario apprendere prima di avviare la procedura guidata.  
  
-   Stabilire se la struttura e i modelli di data mining devono essere compilati in base a un database relazionale o a un cubo esistente in un database OLAP.  
  
-   Stabilire quali colonne contengono le chiavi che identificano in modo univoco un record del case.  
  
-   Stabilire quali colonne o attributi si desidera utilizzare per la stima. Stabilire quali colonne o attributi utilizzare come input per l'analisi.  
  
-   Stabilire quale algoritmo utilizzare. Gli algoritmi forniti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] hanno caratteristiche diverse e producono risultati diversi. Fortunatamente, non si è limitati a un modello per ogni set di dati, pertanto effettuare delle prove aggiungendo modelli diversi.  
  
-   Stabilire se sia necessario poter testare i modelli su un set di dati unificato. In tal caso, valutare l'utilizzo dell'opzione per riservare alcuni dati ai test. È possibile scegliere una percentuale e definire un limite in base a un numero specificato di righe.  
  
##  <a name="starting-the-data-mining-wizard"></a><a name="BKMK_Using_DM_Wizard"></a> Avvio della Creazione guidata modello di data mining  
 Per usare la Creazione guidata modello di data mining, è necessario avere aperto una soluzione in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] che contenga almeno un progetto OLAP o di data mining.  
  
-   Se la soluzione è pronta per il data mining, è possibile semplicemente fare clic con il pulsante destro del mouse sul nodo **Strutture di data mining** in Esplora soluzioni e selezionare **Nuova struttura di data mining** per avviare la procedura guidata.  
  
-   Se la soluzione non contiene progetti esistenti, è possibile aggiungere un nuovo progetto di data mining. Scegliere **Nuovo** dal menu **File**, quindi selezionare **Progetto**. Assicurarsi di scegliere il modello **Progetto multidimensionale e di data mining di Analysis Services**.  
  
-   È anche possibile utilizzare l'Importazione guidata di Analysis Services per ottenere metadati da una soluzione di data mining esistente. Non è tuttavia possibile selezionare singoli oggetti da importare. Verrà importato l'intero database, inclusi cubi, viste origine dati e così via. Si noti inoltre che la nuova soluzione creata tramite importazione viene configurata automaticamente per l'utilizzo del database predefinito locale. Potrebbe essere necessario apportare questa modifica in un'altra istanza prima di poter elaborare o esplorare gli oggetti. Se l'importazione viene eseguita da una versione precedente di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], potrebbe essere necessario aggiornare i riferimenti ai provider.  
  
 In seguito si creerà la struttura di data mining e un modello di data mining associato. È inoltre possibile creare la struttura di data mining e aggiungere in seguito i modelli, ma in generale è più facile creare prima un modello di test.  
  
###  <a name="relational-vs-olap-mining-models"></a><a name="BKMK_Relational"></a> Modelli di data mining relazionali e modelli di data mining di tipo OLAP  
 L'opzione successiva più importante consente di utilizzare un'origine dati relazionale o di basare il modello sui dati multidimensionali (OLAP).  
  
 A questo punto, la Creazione guidata modello di data mining può seguire due diversi percorsi a seconda che l'origine dati sia relazionale o in un cubo. Tutti gli altri elementi, ad eccezione del processo di selezione dati, sono uguali, ovvero la scelta dell'algoritmo, la possibilità di aggiungere un set di dati di dati di riferimento e così via, ma la selezione dei dati del cubo è un po' più complessa rispetto all'utilizzo di dati relazionali. (Sono inoltre disponibili opzioni aggiuntive se si crea un modello basato su un cubo.)  
  
 Per una descrizione dettagliata di ogni opzione vedere gli argomenti seguenti:  
  
 [Creare una struttura di data mining relazionale](create-a-relational-mining-structure.md)  
 Vengono analizzate le decisioni da prendere per la compilazione di un modello di data mining relazionale.  
  
 [Create an OLAP Mining Structure](create-an-olap-mining-structure.md)  
 Vengono descritte le opzioni e le selezioni aggiuntive da impostare per la scelta dei dati da un cubo OLAP.  
  
> [!NOTE]  
>  Non è necessario disporre di un cubo o di un database OLAP per eseguire il data mining. A meno che i dati non siano già archiviati in un cubo o non si desideri eseguire il data mining delle dimensioni o dei risultati di aggregazioni o calcoli OLAP, è consigliabile utilizzare una tabella o un'origine dati relazionale per il data mining.  
  
### <a name="choosing-an-algorithm"></a>Scelta di un algoritmo  
 A questo punto, è necessario decidere quale algoritmo utilizzare per l'elaborazione dei dati. Questa decisione comporta delle difficoltà. Ogni algoritmo disponibile in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] presenta funzionalità diverse e produce risultati diversi, pertanto è possibile provare modelli diversi prima di determinare quale sia il più appropriato per i dati e il problema aziendale da risolvere. Per una spiegazione delle attività per le quali ogni algoritmo è più appropriato, vedere gli argomenti seguenti:  
  
 [Algoritmi di data mining &#40;Analysis Services - Data mining&#41;](data-mining-algorithms-analysis-services-data-mining.md)  
  
 Di nuovo, è possibile creare più modelli utilizzando algoritmi diversi o modificare i parametri in modo che gli algoritmi creino modelli diversi. La scelta dell'algoritmo non deve essere un ostacolo ed è consigliabile creare diversi modelli sugli stessi dati.  
  
### <a name="define-the-data-used-for-modeling"></a>Definire i dati utilizzati per la modellazione  
 Oltre a scegliere i dati da un'origine, è necessario specificare quale tabella della vista origine dati contiene i *dati del case*. La tabella del case verrà utilizzata per eseguire il training del modello di data mining e come tale deve contenere le entità da analizzare, ad esempio i clienti e le relative informazioni demografiche. Ogni case deve essere univoco e identificabile da una *chiave del case*.  
  
 Oltre a specificare la tabella del case, è possibile includere *tabelle annidate* nei dati. Una tabella nidificata contiene in genere informazioni aggiuntive sulle entità nella tabella del case, ad esempio le transazioni eseguite dal cliente o gli attributi con relazione molti-a-uno con l'entità. Ad esempio, una tabella annidata unita in join alla tabella del case **Customers** potrebbe includere un elenco di prodotti acquistati da ogni cliente. In un modello che analizza il traffico di un sito Web, la tabella nidificata potrebbe includere le sequenze delle pagine visitate dall'utente. Per altre informazioni, vedere [Tabelle annidate &#40;Analysis Services - Data mining&#41;](nested-tables-analysis-services-data-mining.md)  
  
### <a name="additional-features"></a>Funzionalità aggiuntive  
 Per assistere nella scelta dei dati appropriati e nella configurazione delle origini dati, la Creazione guidata modello di data mining fornisce queste funzionalità aggiuntive:  
  
-   **Auto-detection of data types**(Rilevamento automatico dei tipi di dati): tramite la procedura guidata verranno esaminate l'univocità e la distribuzione dei valori delle colonne, quindi verrà suggerito il tipo di dati più appropriato e un tipo di uso per i dati. È possibile eseguire l'override di questi suggerimenti selezionando valori da un elenco.  
  
-   **Suggestions for variables**(Suggerimenti per le variabili): è possibile fare clic su una finestra di dialogo e avviare un analizzatore che calcoli le correlazioni tra le colonne incluse nel modello e determini se le colonne consentono di stimare l'attributo del risultato, data la configurazione del modello. È possibile ignorare questi suggerimenti digitando valori diversi.  
  
-   **Selezione funzionalità**: la maggior parte degli algoritmi consente di rilevare automaticamente le colonne in grado di eseguire stime corrette e di usarle con priorità. Nelle colonne che contengono troppi valori viene applicata la *selezione delle funzionalità* per ridurre la cardinalità dei dati e aumentare le probabilità di trovare un modello significativo. È possibile influire sul comportamento di selezione delle funzionalità tramite parametri del modello.  
  
-   **Automatic cube slicing**(Sezionamento automatico del cubo): se il modello di data mining è basato su un'origine dati OLAP, la possibilità di sezionare il modello tramite attributi del cubo è disponibile automaticamente. È pratico per creare modelli basati su subset di dati del cubo.  
  
### <a name="completing-the-wizard"></a>Completamento procedura guidata  
 Nell'ultimo passaggio della creazione guidata viene assegnato un nome alla struttura di data mining e al modello di data mining associato. A seconda del tipo di modello creato, è anche possibile che siano disponibili le opzioni seguenti:  
  
-   Se si seleziona **Consenti drill-through**, la possibilità di eseguire il *drill-through* è abilitata nel modello. Tale funzionalità consente agli utenti che dispongono delle autorizzazioni appropriate di esplorare i dati di origine utilizzati per compilare il modello.  
  
-   Se si compila un modello OLAP, è possibile selezionare le opzioni **Create a new data mining cube**(Crea nuovo cubo di data mining) o **Crea dimensione di data mining**. Entrambe queste opzioni semplificano l'esplorazione del modello completato e l'esecuzione del drill-through nei dati sottostanti.  
  
 Dopo avere completato la Creazione guidata modello di data mining, utilizzare Progettazione modelli di data mining per modificare la struttura e i modelli di data mining, determinare l'accuratezza del modello, visualizzare le caratteristiche della struttura e dei modelli o eseguire stime in base ai modelli.  
  
 [Torna all'inizio](#BKMK_Using_DM_Wizard)  
  
## <a name="related-content"></a>Contenuto correlato  
 Per ulteriori informazioni sulle decisioni è necessario prendere per la creazione di un modello di data mining, vedere i collegamenti seguenti:  
  
 [Algoritmi di data mining &#40;Analysis Services - Data mining&#41;](data-mining-algorithms-analysis-services-data-mining.md)  
  
 [Tipi di contenuto &#40;Data mining&#41;](content-types-data-mining.md)  
  
 [Tipi di dati &#40;Data mining&#41;](data-types-data-mining.md)  
  
 [Selezione delle funzioni &#40;&#41;di data mining](feature-selection-data-mining.md)  
  
 [Valori mancanti &#40;Analysis Services - Data mining&#41;](missing-values-analysis-services-data-mining.md)  
  
 [Drill-through sui modelli di data mining](drillthrough-on-mining-models.md)  
  
## <a name="see-also"></a>Vedi anche  
 [Strumenti di data mining](data-mining-tools.md)   
 [Soluzioni di data mining](data-mining-solutions.md)  
  
  
