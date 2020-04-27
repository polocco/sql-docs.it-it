---
title: Informazioni di riferimento sulle funzioni di aggregazione (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: db6542ee-02d0-4073-90e6-cba8f9510fbb
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5f4c61c346452664557396032cb4ea14f89da66c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66105325"
---
# <a name="aggregate-functions-reference-report-builder-and-ssrs"></a>Riferimento a funzioni di aggregazione (Generatore report e SSRS)
  Per includere valori aggregati nel report, è possibile utilizzare funzioni di aggregazione predefinite nelle espressioni. La funzione di aggregazione predefinita per i campi numerici è SUM. È possibile modificare l'espressione e utilizzare una funzione di aggregazione predefinita o specificare un ambito differente. L'ambito identifica il set di dati da utilizzare per il calcolo.  
  
 Quando l'elaboratore di report combina i dati e il layout del report, le espressioni per ogni elemento del report vengono valutate. Insieme a ogni pagina del report vengono visualizzati i risultati per ogni espressione negli elementi del report visualizzabile.  
  
 Nella tabella seguente sono elencate le categorie di funzioni predefinite supportate che possono essere incluse in un'espressione:  
  
-   [Funzioni di aggregazione predefinite](#CalculatingAggregates)  
  
-   [Restrizioni relative a campi, raccolte e funzioni di aggregazione predefiniti](#Restrictions)  
  
-   [Restrizioni relative alle aggregazioni nidificate](#NestedRestrictions)  
  
-   [Calcolo dei valori correnti](#CalculatingRunningValues)  
  
-   [Recupero di conteggi delle righe](#RetrievingRowCounts)  
  
-   [Ricerca di valori da un altro set di dati](#LookupFunctions)  
  
-   [Recupero di valori dipendenti dall'ordinamento](#RetrievingPostsortValues)  
  
-   [Recupero di aggregazioni server](#RetrievingServerAggregates)  
  
-   [Recupero del livello ricorsivo](#RetrievingRecursiveLevel)  
  
-   [Verifica dell'ambito](#TestingforScope)  
  
 Per determinare gli ambiti validi per una funzione, vedere l'argomento di riferimento delle singole funzioni. Per altre informazioni ed esempi, vedere [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="built-in-aggregate-functions"></a><a name="CalculatingAggregates"></a> Funzioni di aggregazione predefinite  
 Le funzioni predefinite seguenti calcolano i valori di riepilogo relativi a un set di dati numerici non Null nell'ambito predefinito o nell'ambito denominato.  
  
|**Funzione**|**Descrizione**|  
|------------------|---------------------|  
|[Avg](report-builder-functions-avg-function.md)|Restituisce la media di tutti i valori numerici non Null specificati dall'espressione, valutata nell'ambito specificato.|  
|[Numero](report-builder-functions-count-function.md)|Restituisce il conteggio dei valori non Null specificati dall'espressione, valutato nel contesto dell'ambito specificato.|  
|[CountDistinct](report-builder-functions-countdistinct-function.md)|Restituisce un conteggio di tutti i distinti valori non Null specificati dall'espressione, valutato nel contesto dell'ambito specificato.|  
|[Max](report-builder-functions-max-function.md)|Restituisce il valore massimo di tutti i valori numerici non Null specificati dall'espressione, nel contesto dell'ambito specificato. È possibile utilizzare questa funzione per specificare il valore massimo di un asse del grafico per controllare la scala.|  
|[Min](report-builder-functions-min-function.md)|Restituisce il valore minimo di tutti i valori numerici non Null specificati dall'espressione, nel contesto dell'ambito specificato. È possibile utilizzare questa funzione per specificare il valore minimo di un asse del grafico per controllare la scala.|  
|[StDev](report-builder-functions-stdev-function.md)|Restituisce la deviazione standard di tutti i valori numerici non Null specificati dall'espressione, valutata nell'ambito specificato.|  
|[StDevP](report-builder-functions-stdevp-function.md)|Restituisce la deviazione standard di popolazione di tutti i valori numerici non Null specificati dall'espressione, valutata nell'ambito specificato.|  
|[Sum](report-builder-functions-sum-function.md)|Restituisce la somma di tutti i valori numerici non Null specificati dall'espressione, valutata nell'ambito specificato.|  
|[Union](report-builder-functions-union-function.md)|Restituisce l'unione di tutti i valori di dati spaziali non Null di tipo `SqlGeometry` o `SqlGeography` specificati dall'espressione, valutati nell'ambito specificato.|  
|[Var](report-builder-functions-var-function.md)|Restituisce la varianza di tutti i valori numerici non Null specificati dall'espressione, valutata nell'ambito specificato.|  
|[VarP](report-builder-functions-varp-function.md)|Viene restituita la varianza della popolazione di tutti i valori numerici non Null specificati dall'espressione, valutata nel contesto dell'ambito specificato.|  
  
##  <a name="restrictions-on-built-in-fields-collections-and-aggregate-functions"></a><a name="Restrictions"></a>Restrizioni relative a campi, raccolte e funzioni di aggregazione predefiniti  
 Nella tabella seguente sono riepilogate le restrizioni nei percorsi del report in cui è possibile aggiungere espressioni contenenti riferimenti alle raccolte predefinite globali.  
  
|Percorso nel report|Campi|Parametri|ReportItems|PageNumber<br /><br /> TotalPages|DataSource<br /><br /> DataSet|variables|RenderFormat|  
|------------------------|------------|----------------|-----------------|-------------------------------|----------------------------|---------------|------------------|  
|Intestazione di pagina<br /><br /> Piè di pagina|Sì|Sì|Al massimo uno<br /><br /> Nota 1|Sì|Sì|Sì|Sì|  
|Corpo|Sì<br /><br /> Nota 2|Sì|Solo elementi nell'ambito corrente o in un ambito contenitore<br /><br /> Nota 3|No|Sì|Sì|Sì|  
|Parametro del report|No|Solo i parametri precedenti dell'elenco<br /><br /> Nota 4|No|No|No|No|No|  
|Campo|Sì|Sì|No|No|No|No|No|  
|Parametro della query|No|Sì|No|No|No|No|No|  
|Espressione di raggruppamento|Sì|Sì|No|No|Sì|No|No|  
|Espressione di ordinamento|Sì|Sì|No|No|Sì|Sì<br /><br /> Nota 5|No|  
|Espressione filtro|Sì|Sì|No|No|Sì|Sì<br /><br /> Nota 6|No|  
|Codice|No|Sì<br /><br /> Nota 7|No|No|No|No|No|  
|Lingua del report|No|Sì|No|No|No|No|No|  
|variables|Sì|Sì|No|No|Sì|Ambito corrente o contenitore|No|  
|Aggregazioni|Sì|Sì|Solo nell'intestazione di pagina/piè di pagina|Solo nelle aggregazioni dell'elemento del report|Sì|No|No|  
|Funzioni di ricerca|Sì|Sì|Sì|No|Sì|No|No|  
  
-   **Nota 1.** ReportItems deve essere incluso nella pagina del report visualizzabile; in caso contrario, il relativo valore è Null. Se la visibilità di un elemento del report dipende da un'espressione che restituisce False, l'elemento del report non sarà presente nella pagina.  
  
-   **Nota 2.** Se un riferimento a un campo viene usato in un ambito del gruppo e non è incluso nell'espressione di raggruppamento, il valore per il campo non è definito, a meno che nell'ambito non sia presente un solo valore. Per specificare un valore, usare First o Last e l'ambito del gruppo.  
  
-   **Nota 3.** Le espressioni che includono un riferimento a ReportItems possono specificare valori per altri parametri ReportItems nello stesso ambito del gruppo o in un ambito del gruppo contenitore.  
  
-   **Nota 4.** I valori della proprietà per i parametri precedenti possono essere Null.  
  
-   **Nota 5.** Solo negli ordinamenti di membri. Non può essere usata nelle espressioni di ordinamento dell'area dati.  
  
-   **Nota 6.** Solo nei filtri di membri. Non può essere usata in espressioni dei filtri dell'area dati o del set di dati.  
  
-   **Nota 7.** La raccolta di parametri non viene inizializzata fino al termine dell'elaborazione del blocco di codice, di conseguenza non è possibile usare i metodi per controllare i parametri durante l'inizializzazione.  
  
-   **Nota 8.** In tutte le aggregazioni, ad eccezione di Count e CountDistinct, i tipi di dati devono essere analoghi per tutti i valori oppure essere Null.  
  
##  <a name="restrictions-on-nested-aggregates"></a><a name="NestedRestrictions"></a> Restrizioni relative alle aggregazioni nidificate  
 Nella tabella seguente vengono riepilogate le restrizioni sulle funzioni di aggregazione che consentono la specifica di altre funzioni di aggregazione come aggregazioni nidificate.  
  
|Context|RunningValue|RowNumber|First (Primo)<br /><br /> Last (Ultimo)|Previous|Sum e altre funzioni di ordinamento preliminare|Aggregazioni ReportItem|Funzioni di ricerca|Funzione di aggregazione|  
|-------------|------------------|---------------|--------------------|--------------|-------------------------------------|---------------------------|----------------------|------------------------|  
|Valore corrente|No|No|No|No|Sì|No|Sì|No|  
|First (Primo)<br /><br /> Last (Ultimo)|No|No|No|No|Sì|No|No|No|  
|Previous|Sì|Sì|Sì|No|Sì|No|Sì|No|  
|Sum e altre funzioni di ordinamento preliminare|No|No|No|No|Sì|No|Sì|No|  
|Aggregazioni ReportItem|No|No|No|No|No|No|No|No|  
|Funzioni di ricerca|Sì|Sì<br /><br /> Nota 1|Sì<br /><br /> Nota 1|Sì<br /><br /> Nota 1|Sì<br /><br /> Nota 1|Sì<br /><br /> Nota 1|No|No|  
|Funzione di aggregazione|No|No|No|No|No|No|No|No|  
  
-   **Nota 1.** Le funzioni di aggregazione sono consentite solo all'interno dell'espressione *Source* di una funzione di ricerca se tale funzione non è contenuta in un'aggregazione. Le funzioni di aggregazione non sono consentite all'interno di espressioni *Destination* o *Result* di una funzione di ricerca.  
  
##  <a name="calculating-running-values"></a><a name="CalculatingRunningValues"></a>Calcolo dei valori correnti  
 Nelle funzioni predefinite seguenti vengono calcolati i valori correnti per un set di dati. `RowNumber` è simile a `RunningValue` in quanto consente la restituzione del valore corrente di un conteggio che viene incrementato per ogni riga all'interno dell'ambito contenitore. Il parametro di ambito per queste funzioni deve specificare un ambito contenitore che controlla quando deve essere riavviato il conteggio.  
  
|**Funzione**|**Descrizione**|  
|------------------|---------------------|  
|[RowNumber](report-builder-functions-rownumber-function.md)|Restituisce il conteggio parziale del numero di righe per l'ambito specificato. La funzione `RowNumber` riavvia il conteggio da 1, non da 0.|  
|[RunningValue](report-builder-functions-runningvalue-function.md)|Restituisce un'aggregazione parziale di tutti i valori numerici non Null specificati dall'espressione, valutata per l'ambito specificato.|  
  
##  <a name="retrieving-row-counts"></a><a name="RetrievingRowCounts"></a>Recupero dei conteggi delle righe  
 La funzione predefinita seguente calcola il numero di righe nell'ambito specificato. Utilizzare questa funzione per conteggiare tutte le righe, incluse quelle con valori Null.  
  
|**Funzione**|**Descrizione**|  
|------------------|---------------------|  
|[CountRows](report-builder-functions-countrows-function.md)|Restituisce il numero di righe nell'ambito specificato, incluse le righe con valori Null.|  
  
##  <a name="looking-up-values-from-another-dataset"></a><a name="LookupFunctions"></a>Ricerca di valori da un altro set di dati  
 Le funzioni di ricerca seguenti recuperano valori da un set di dati specificato.  
  
|**Funzione**|**Descrizione**|  
|------------------|---------------------|  
|[Funzione Lookup](report-builder-functions-lookup-function.md)|Restituisce un valore da un set di dati per un'espressione specificata.|  
|[Funzione LookupSet](report-builder-functions-lookupset-function.md)|Restituisce un set di valori da un set di dati per un'espressione specificata.|  
|[Funzione Multilookup](report-builder-functions-multilookup-function.md)|Restituisce il set di valori di prima corrispondenza per un set di nomi da un set di dati che contiene coppie nome/valore.|  
  
##  <a name="retrieving-sort-dependent-values"></a><a name="RetrievingPostsortValues"></a>Recupero di valori dipendenti dall'ordinamento  
 Le funzioni predefinite seguenti restituiscono il primo, l'ultimo o il precedente valore all'interno di un ambito specificato. Queste funzioni dipendono dal tipo di ordinamento dei valori dei dati. Utilizzare queste funzioni, ad esempio, per trovare il primo e l'ultimo valore in una pagina o per creare un'intestazione di pagina in formato dizionario. Usare `Previous` per confrontare il valore di una riga con il valore della riga precedente in un ambito specificato, ad esempio per trovare i valori in percentuale anno dopo anno in una tabella.  
  
|**Funzione**|**Descrizione**|  
|------------------|---------------------|  
|[Prima](report-builder-functions-first-function.md)|Restituisce il primo valore nell'ambito specificato dell'espressione specificata.|  
|[Ultima](report-builder-functions-last-function.md)|Restituisce l'ultimo valore nell'ambito specificato dell'espressione specificata.|  
|[Indietro](report-builder-functions-previous-function.md)|Restituisce il valore o il valore di aggregazione specificato per l'istanza precedente di un elemento all'interno dell'ambito specificato.|  
  
##  <a name="retrieving-server-aggregates"></a><a name="RetrievingServerAggregates"></a>Recupero di aggregazioni server  
 La funzione predefinita seguente recupera aggregazioni personalizzate dal provider di dati. Ad esempio, usando un tipo di origine dati di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , è possibile recuperare le aggregazioni calcolate sul server dell'origine dati da usare in un'intestazione di gruppo.  
  
|**Funzione**|**Descrizione**|  
|------------------|---------------------|  
|[Aggregazione](report-builder-functions-aggregate-function.md)|Restituisce un'aggregazione personalizzata dell'espressione specificata, secondo quanto definito dal provider di dati.|  
  
##  <a name="testing-for-scope"></a><a name="TestingforScope"></a>Test per ambito  
 La funzione predefinita seguente controlla il contesto corrente di un elemento del report per verificare se è un membro di un ambito specifico.  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|[InScope](report-builder-functions-inscope-function.md)|Indica se l'istanza corrente di un elemento è inclusa nell'ambito specificato.|  
  
##  <a name="retrieving-recursive-level"></a><a name="RetrievingRecursiveLevel"></a>Recupero del livello ricorsivo  
 La funzione predefinita seguente recupera il livello corrente quando viene elaborata una gerarchia ricorsiva. Usare il risultato di questa funzione con la proprietà `Padding` in una casella di testo per controllare il livello di rientro di una gerarchia visiva per un gruppo ricorsivo. Per altre informazioni, vedere [Creazione di gruppi di gerarchie ricorsive &#40;Generatore report e SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|[Level](report-builder-functions-level-function.md)|Restituisce il livello di nidificazione corrente in una gerarchia ricorsiva.|  
  
## <a name="see-also"></a>Vedi anche  
 [Utilizzo delle espressioni nei report &#40;Generatore report e SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40;Generatore report e SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
