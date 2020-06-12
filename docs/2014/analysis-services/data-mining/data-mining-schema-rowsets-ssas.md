---
title: Esecuzione di query sui set di righe dello schema di data mining (Analysis Services-Data mining) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- schema rowsets [Analysis Services], data mining
- data mining [Analysis Services], queries
- mining model content
- data mining [Analysis Services], schema rowsets
- schema rowsets [Analysis Services], retrieving
- data mining [Analysis Services], troubleshooting
ms.assetid: 442d8c29-07c7-45de-9a15-d556059f68d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8775ec4dbfb7d851d98e0a943d052589f45b1ade
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2020
ms.locfileid: "84523067"
---
# <a name="querying-the-data-mining-schema-rowsets-analysis-services---data-mining"></a>Esecuzione di query sui set di righe dello schema di data mining (Analysis Services - Data mining)
  In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]molti dei set di righe esistenti dello schema di data mining OLE DB sono esposti come set di tabelle di sistema su cui è possibile eseguire query tramite istruzioni DMX (Data Mining Extensions). Mediante la creazione di query sul set di righe dello schema di data mining, è possibile identificare i servizi disponibili, ottenere aggiornamenti sullo stato dei modelli e delle strutture e trovare dettagli sul contenuto del modello o sui parametri. Per una descrizione dei set di righe dello schema di data mining, vedere [Data Mining Schema Rowsets](../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
> [!NOTE]  
>  È anche possibile eseguire una query sul set di righe dello schema di data mining utilizzando l'analisi XMLA. Per altre informazioni sull'esecuzione di questa operazione in SQL Server Management Studio, vedere [Creare una query di data mining utilizzando XMLA](create-a-data-mining-query-by-using-xmla.md).  
  
## <a name="list-of-data-mining-schema-rowsets"></a>Elenco di set di righe dello schema di data mining  
 Nella tabella seguente sono elencati i set di righe dello schema di data mining che possono essere utili per l'esecuzione delle query e il monitoraggio.  
  
|Nome del set di righe|Descrizione|  
|-----------------|-----------------|  
|DMSCHEMA_MINING_MODELS|Elenca tutti i modelli di data mining nel contesto corrente.<br /><br /> Include informazioni quali la data di creazione, i parametri utilizzati per creare il modello e la dimensione del set di training.|  
|DMSCHEMA_MINING_COLUMNS|Elenca tutte le colonne utilizzate nei modelli di data mining nel contesto corrente.<br /><br /> Le informazioni specificano il mapping a una colonna di origine della struttura di data mining, il tipo di dati, la precisione e le funzioni di stima che possono essere utilizzate con la colonna.|  
|DMSCHEMA_MINING_STRUCTURES|Elenca tutte le strutture di data mining nel contesto corrente.<br /><br /> Le informazioni specificano se la struttura viene popolata, la data dell'ultima elaborazione della struttura e la definizione del set di dati di controllo per la struttura, se disponibile.|  
|DMSCHEMA_MINING_STRUCTURE_COLUMNS|Elenca tutte le colonne utilizzate nelle strutture di data mining nel contesto corrente.<br /><br /> Le informazioni specificano il tipo di contenuto e il tipo di dati, l'eventuale supporto dei valori Null e la presenza o meno di dati di tabella nidificati nella colonna.|  
|DMSCHEMA_MINING_SERVICES|Elenca tutti i servizi di data mining, o algoritmi, disponibili sul server specificato.<br /><br /> Le informazioni specificano i flag di modellazione supportati, i tipi di input e i tipi di origine dati supportati.|  
|DMSCHEMA_MINING_SERVICE_PARAMETERS|Elenca tutti i parametri per i servizi di data mining disponibili nell'istanza corrente.<br /><br /> Le informazioni includono il tipo di dati per ogni parametro, i valori predefiniti e i limiti superiore e inferiore.|  
|DMSCHEMA_MODEL_CONTENT|Restituisce il contenuto del modello se il modello è stato elaborato.<br /><br /> Per altre informazioni, vedere [Contenuto del modello di data mining &#40;Analysis Services - Data mining&#41;](mining-model-content-analysis-services-data-mining.md).|  
|DBSCHEMA_CATALOGS|Elenca tutti i database (cataloghi) nell'istanza corrente di Analysis Services.|  
|MDSCHEMA_INPUT_DATASOURCES|Elenca tutte le origini dati nell'istanza corrente di Analysis Services.|  
  
> [!NOTE]  
>  L'elenco nella tabella non è completo in quanto contiene solo i set di righe che possono essere utili per la risoluzione dei problemi.  
  
## <a name="examples"></a>Esempio  
 Nella sezione seguente sono riportati alcuni esempi di query sui set di righe dello schema di data mining.  
  
### <a name="example-1-list-data-mining-services"></a>Esempio 1: Elenco di servizi di data mining  
 Nella query seguente viene restituito un elenco di servizi di data mining disponibili sul server corrente, che indica gli algoritmi abilitati. Le colonne specificate per ogni servizio di data mining includono i flag di modellazione e i tipi di contenuto che possono essere utilizzati con ogni algoritmo, il GUID di ogni servizio e gli eventuali limiti di stima che potrebbero essere stati specificati per ogni servizio.  
  
```  
SELECT *  
FROM $system.DMSCHEMA_MINING_SERVICES  
```  
  
### <a name="example-2-list-mining-model-parameters"></a>Esempio 2: Elenco di parametri del modello di data mining  
 Nell'esempio seguente vengono restituiti i parametri utilizzati per creare uno specifico modello di data mining:  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM Clustering'  
```  
  
### <a name="example-3-list-all-rowsets"></a>Esempio 3: Elenco di tutti i set di righe  
 Nell'esempio seguente viene restituito un elenco completo di set di righe disponibili nel server corrente:  
  
```  
SELECT *   
FROM $system.DBSCHEMA_TABLES  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti relativi alla risoluzione dei problemi (Analysis Services - Dati mining)](https://msdn.microsoft.com/library/cc645881.aspx)  
  
  
