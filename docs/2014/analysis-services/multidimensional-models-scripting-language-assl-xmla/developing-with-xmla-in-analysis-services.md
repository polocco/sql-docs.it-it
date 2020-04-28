---
title: Sviluppo con XMLA in Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XML for Analysis, data mining
- commands [XML for Analysis]
- data mining [XML for Analysis]
- XMLA, data mining
- XML for Analysis, Analysis Services tasks
- XMLA, Analysis Services tasks
ms.assetid: 54445ee7-720c-4683-99a6-e75b3dcca904
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 27b143a9cc5c888c6e464d300d2ccfea114ef9bc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "80380682"
---
# <a name="developing-with-xmla-in-analysis-services"></a>Sviluppo con XMLA in Analysis Services
  XML for Analysis (XMLA) è protocollo XML basato su SOAP, progettato in modo specifico per accedere a tutti i dati di qualsiasi origine dati multidimensionale standard accessibile tramite una connessione HTTP. In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] l'unico protocollo utilizzato durante la comunicazione con applicazioni client è XMLA. Fondamentalmente, tutte le librerie client supportate da Analysis Services formulano richieste e risposte in XMLA.  
  
 Gli sviluppatori possono utilizzare XMLA per integrare un'applicazione client con [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], senza dipendenze dalle interfacce .NET Framework o COM. I requisiti delle applicazioni che includono l'hosting su un'ampia gamma di piattaforme possono essere soddisfatti tramite XMLA e una connessione HTTP a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è completamente conforme alla specifica del 1.1 di XMLA, estendendola inoltre all'abilitazione del supporto della definizione, della modifica e del controllo dei dati. Le estensioni di Analysis Services vengono denominate ASSL (Analysis Services Scripting Language). L'utilizzo combinato di XMLA e ASSL abilita un set di funzionalità più ampio rispetto a quello fornito dal solo protocollo XMLA. Per ulteriori informazioni su ASSL, vedere [sviluppo con Analysis Services linguaggio di scripting &#40;assl&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Argomento|Descrizione|  
|-----------|-----------------|  
|[Gestione di connessioni e sessioni &#40;XMLA&#41;](managing-connections-and-sessions-xmla.md)|Viene descritto come connettersi a un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e come gestire sessioni e informazioni sullo stato in XMLA.|  
|[Gestione di errori e avvisi &#40;XMLA&#41;](handling-errors-and-warnings-xmla.md)|Descrive il modo in cui [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] restituisce le informazioni di errore e di avviso per metodi e comandi in XMLA.|  
|[Definizione e identificazione di oggetti &#40;&#41;XMLA](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)|Descrive identificatori di oggetto e riferimenti all'oggetto e il modo in cui utilizzarli in comandi XMLA.|  
|[Gestione delle transazioni &#40;&#41;XMLA](managing-transactions-xmla.md)|Viene illustrato in dettaglio come utilizzare i comandi [BeginTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/begintransaction-element-xmla), [CommitTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/committransaction-element-xmla)e [RollbackTransaction](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/rollbacktransaction-element-xmla) per definire e gestire in modo esplicito una transazione nella sessione XMLA corrente.|  
|[Annullamento di comandi &#40;&#41;XMLA](../multidimensional-models-scripting-language-assl-xmla/canceling-commands-xmla.md)|Viene descritto come utilizzare il comando [Cancel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla)per annullare comandi, sessioni e connessioni in XMLA.|  
|[Esecuzione di operazioni batch &#40;&#41;XMLA](performing-batch-operations-xmla.md)|Viene descritto come utilizzare il comando [batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) per eseguire più comandi XMLA, in serie o in parallelo, all'interno della stessa transazione o come transazioni separate, utilizzando un unico metodo [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) XMLA.|  
|[Creazione e modifica di oggetti &#40;XMLA&#41;](creating-and-altering-objects-xmla.md)|Viene descritto come utilizzare i comandi [create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla), [ALTER](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)e [Delete](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/delete-element-xmla) , insieme agli elementi ASSL (Analysis Services Scripting Language), per definire, modificare o rimuovere oggetti da un' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] istanza di.|  
|[Blocco e sblocco di database &#40;XMLA&#41;](locking-and-unlocking-databases-xmla.md)|Viene illustrato in dettaglio come utilizzare i comandi [Lock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) e [Unlock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) per bloccare e [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sbloccare un database.|  
|[Elaborazione di oggetti &#40;XMLA&#41;](processing-objects-xmla.md)|Viene descritto come utilizzare il comando [Process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) per elaborare un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oggetto.|  
|[Unione di partizioni &#40;&#41;XMLA](merging-partitions-xmla.md)|Viene descritto come utilizzare il comando [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla) per unire le partizioni in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] un'istanza di.|  
|[Progettazione di aggregazioni &#40;XMLA&#41;](designing-aggregations-xmla.md)|Viene descritto come utilizzare il comando [DesignAggregations](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/designaggregations-element-xmla) , in modalità iterativa o batch, per progettare le aggregazioni per una progettazione delle [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]aggregazioni in.|  
|[Backup, ripristino e sincronizzazione di database &#40;XMLA&#41;](backing-up-restoring-and-synchronizing-databases-xmla.md)|Viene descritto come utilizzare i comandi [backup](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla) e [Restore](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/restore-element-xmla) per eseguire il backup e [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] il ripristino di un database da un file di backup.<br /><br /> Viene inoltre descritto come utilizzare il comando [Synchronize](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/synchronize-element-xmla) per sincronizzare un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database di con un database esistente nella stessa istanza o in un'istanza diversa.|  
|[Inserimento, aggiornamento ed eliminazione di membri &#40;XMLA&#41;](inserting-updating-and-dropping-members-xmla.md)|Viene descritto come utilizzare i comandi [Insert](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla), [Update](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)e [Drop](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla) per aggiungere, modificare o eliminare membri da una dimensione abilitata per la scrittura.|  
|[Aggiornamento di celle &#40;&#41;XMLA](updating-cells-xmla.md)|Viene descritto come utilizzare il comando [UpdateCells](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/updatecells-element-xmla) per modificare i valori delle celle in una partizione abilitata per la scrittura.|  
|[Gestione delle cache &#40;&#41;XMLA](managing-caches-xmla.md)|Viene illustrato in dettaglio come utilizzare il comando [ClearCache](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla) per cancellare le cache [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] degli oggetti.|  
|[Monitoraggio di tracce &#40;&#41;XMLA](monitoring-traces-xmla.md)|Viene descritto come utilizzare il comando [Subscribe](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/subscribe-element-xmla) per sottoscrivere e monitorare una traccia esistente in un' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] istanza di.|  
  
## <a name="data-mining-with-xmla"></a>Data mining in XMLA  
 In XML for Analysis sono completamente supportati i set di righe dello schema di data mining. Questi set di righe forniscono informazioni per l'esecuzione di query sui modelli di data mining utilizzando il metodo [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) . Per ulteriori informazioni sui set di righe dello schema data mining, vedere [set di righe dello schema di data mining](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/data-mining-schema-rowsets) 
  
 Per ulteriori informazioni su DMX, vedere [Data Mining Extensions &#40;dmx&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference).  
  
## <a name="namespace-and-schema"></a>Spazio dei nomi e schema  
  
### <a name="namespace"></a>Spazio dei nomi  
 Lo schema definito in questa specifica utilizza lo spazio dei `https://schemas.microsoft.com/AnalysisServices/2003/Engine` nomi XML e l'abbreviazione standard "DDL".  
  
### <a name="schema"></a>SCHEMA  
 La definizione di uno schema XML Schema Definition Language (XSD) per il linguaggio di definizione dell'oggetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è basata sulla definizione degli elementi e della gerarchia dello schema descritti in questa sezione.  
  
## <a name="extensibility"></a>Estendibilità  
 L'estendibilità dello schema del linguaggio di definizione dell'oggetto viene fornito tramite un elemento `Annotation` incluso in tutti gli oggetti. Tale elemento può contenere qualsiasi valore XML valido da qualsiasi spazio dei nomi XML (diverso dallo spazio dei nomi di destinazione che definisce il linguaggio DDL), soggetto alle regole seguenti:  
  
-   Il valore XML può contenere solo elementi.  
  
-   Ogni elemento deve avere un nome univoco. È consigliabile che il valore dell'elemento `Name` faccia riferimento allo spazio dei nomi di destinazione.  
  
 Queste regole vengono imposte per consentire l'esposizione del tag `Annotation` come set di coppie nome/valore tramite altre interfacce, ad esempio DSO (Decision Support Objects) 9.0.  
  
 I commenti e gli spazi vuoti all'interno del tag `Annotation` non inclusi in un elemento figlio non possono essere mantenuti. Tutti gli elementi devono inoltre essere di lettura/scrittura. Gli elementi di sola lettura vengono ignorati.  
  
 Lo schema del linguaggio di definizione dell'oggetto è chiuso, poiché il server non consente la sostituzione di tipi derivati per gli elementi definiti nello schema. Di conseguenza il server accetta solo il set di elementi definito in questa sezione e nessun altro elemento né attributo. Gli elementi sconosciuti provocano la generazione di un errore da parte del motore di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo con Analysis Services linguaggio di scripting &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Informazioni sull'architettura Microsoft OLAP](../multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  
