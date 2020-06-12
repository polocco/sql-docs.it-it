---
title: Membri calcolati in sub-SELECT e sottocubi | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6e35e8f7-ae1c-4549-8432-accf036d2373
author: minewiskan
ms.author: owend
ms.openlocfilehash: 89e87d8c1f15dfd0f70ebaca92a81603b06ff0ff
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546543"
---
# <a name="calculated-members-in-subselects-and-subcubes"></a>Membri calcolati in sub-SELECT e sottocubi
  Nelle versioni precedenti i membri calcolati non erano consentiti nelle sub-SELECT o nei sottocubi. A partire da SQL Server 2008 sono invece consentiti e abilitati da una proprietà di connessione. Inoltre, con SQL Server 2008 R2 è stato introdotto un nuovo comportamento per i membri calcolati in sub-SELECT e sottocubi.  
  
## <a name="calculated-members-in-subselects-and-subcubes"></a>Membri calcolati in sub-SELECT e sottocubi  
 La `SubQueries` proprietà della stringa di connessione in <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> o nella proprietà delle `DBPROPMSMDSUBQUERIES` [proprietà XMLA supportate &#40;&#41;XMLA](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) definisce il comportamento o la tolleranza dei membri calcolati o dei set calcolati in sub-SELECT o sottocubi. Nel contesto di questo documento con il termine sub-SELECT si fa riferimento a sub-SELECT e sottocubi, se non diversamente specificato.  
  
 La proprietà SubQueries consente i valori riportati di seguito.  
  
|||  
|-|-|  
|Valore|Descrizione|  
|0|I membri calcolati non sono consentiti in sub-SELECT o sottocubi.<br /><br /> Durante la valutazione della sub-SELECT o del sottocubo viene generato un errore se si fa riferimento a un membro calcolato.|  
|1|I membri calcolati sono consentiti in sub-SELECT o sottocubi, ma nel sottospazio di restituzione non viene introdotto alcun predecessore.|  
|2|I membri calcolati sono consentiti in sub-SELECT o sottocubi e nel sottospazio di restituzione vengono introdotti i predecessori. Inoltre, nella selezione dei membri calcolati è consentita la granularità mista.|  
  
 L'utilizzo del valore 1 o 2 nella proprietà SubQueries consente di utilizzare i membri calcolati per filtrare il sottospazio di restituzione per i sub-SELECT.  
  
 Un esempio consentirà di chiarire il concetto; per replicare il comportamento sopra esposto, è prima di tutto necessario creare un membro calcolato, quindi eseguire una query per il sub-SELECT.  
  
 Nell'esempio che segue viene creato un membro calcolato che aggiunge [Seattle Metro] come città alla gerarchia [Geography].[Geography] sotto lo stato di Washington.  
  
 Per eseguire l'esempio, la stringa di connessione deve contenere la proprietà SubQueries con un valore di 1 e tutte le istruzioni MDX devono essere eseguite nella stessa sessione.  
  
 Eseguire prima l'espressione MDX seguente:  
  
```  
//Remember to set Subqueries=1 in the connection string prior  
//to issue these commands  
//--> AS2008 behavior  
CREATE MEMBER [Adventure Works].[Geography].[Geography].[State-Province].&[WA]&[US].[Seattle Metro Agg]   
   AS  AGGREGATE(   
                 {   
                   [Geography].[Geography].[City].&[Bellevue]&[WA]  
                 , [Geography].[Geography].[City].&[Issaquah]&[WA]  
                 , [Geography].[Geography].[City].&[Redmond]&[WA]  
                 , [Geography].[Geography].[City].&[Seattle]&[WA]  
                 }  
                )    
```  
  
 Quindi eseguire la query MDX seguente per visualizzare i membri calcolati consentiti nei sub-SELECT.  
  
```  
Select [Date].[Calendar Year].members on 0,  
       [Geography].[Geography].allmembers on 1  
from (Select {[Geography].[Geography].[State-Province].&[WA]&[US].[Seattle Metro Agg]} on 0 from [Adventure Works])  
Where [Measures].[Reseller Sales Amount]  
```  
  
 I risultati che si ottengono sono i seguenti:  
  
|||||||  
|-|-|-|-|-|-|  
||All Periods|CY 2001|CY 2002|CY 2003|CY 2004|  
|Seattle Metro Agg|$2,383,545.69|$291,248.93|$763,557.02|$915,832.36|$412,907.37|  
  
 Come già affermato, i predecessori di [Seattle Metro] non esistono nel sottospazio restituito, quando SubQueries=1, pertanto [Geography].[Geography].allmembers contiene solo il membro calcolato.  
  
 Se si esegue l'esempio utilizzando SubQueries=2, nella stringa di connessione i risultati saranno:  
  
|||||||  
|-|-|-|-|-|-|  
||All Periods|CY 2001|CY 2002|CY 2003|CY 2004|  
|All Geographies|(null)|(null)|(null)|(null)|(null)|  
|Stati Uniti|(null)|(null)|(null)|(null)|(null)|  
|Washington|(null)|(null)|(null)|(null)|(null)|  
|Seattle Metro Agg|$2,383,545.69|$291,248.93|$763,557.02|$915,832.36|$412,907.37|  
  
 Se quindi si utilizza SubQueries=2, i predecessori di [Seattle Metro] esistono nel sottospazio restituito, ma per tali membri non esiste alcun valore perché non vi sono membri normali che forniscano le aggregazioni. Ne consegue che nell'esempio vengono forniti valori Null per tutti i membri predecessori del membro calcolato.  
  
 Per comprendere il comportamento descritto, è opportuno ricordare che i membri calcolati non contribuiscono alle aggregazioni dei padri come i membri normali. Nel primo caso la sola applicazione di filtri da membri calcolati produrrà predecessori vuoti, perché non esistono membri normali che contribuiscano ai valori aggregati del sottospazio risultante. Se si aggiungono membri normali all'espressione di filtro, i valori aggregati deriveranno da tali membri normali. Continuando con l'esempio precedente, è possibile aggiungere la città di Portland, in Oregon e la città di Spokane, nello stato di Washington allo stesso asse su cui viene visualizzato il membro calcolato; come mostrato nell'espressione MDX seguente:  
  
```  
Select [Date].[Calendar Year].members on 0,  
       [Geography].[Geography].allmembers on 1  
from (Select {  
               [Seattle Metro Agg]  
             , [Geography].[Geography].[City].&[Portland]&[OR]  
             , [Geography].[Geography].[City].&[Spokane]&[WA]  
             } on 0 from [Adventure Works]  
     )  
Where [Measures].[Reseller Sales Amount]  
```  
  
 I risultati che si ottengono sono i seguenti:  
  
|||||||  
|-|-|-|-|-|-|  
||All Periods|CY 2001|CY 2002|CY 2003|CY 2004|  
|All Geographies|$235,171.62|$419.46|$4,996.25|$131,788.82|$97,967.09|  
|Stati Uniti|$235,171.62|$419.46|$4,996.25|$131,788.82|$97,967.09|  
|Oregon|$30,968.25|$419.46|$4,996.25|$17,442.97|$8,109.56|  
|Portland|$30,968.25|$419.46|$4,996.25|$17,442.97|$8,109.56|  
|97205|$30,968.25|$419.46|$4,996.25|$17,442.97|$8,109.56|  
|Washington|$204,203.37|(null)|(null)|$114,345.85|$89,857.52|  
|Spokane|$204,203.37|(null)|(null)|$114,345.85|$89,857.52|  
|99202|$204,203.37|(null)|(null)|$114,345.85|$89,857.52|  
|Seattle Metro Agg|$2,383,545.69|$291,248.93|$763,557.02|$915,832.36|$412,907.37|  
  
 Nei risultati sopra riportati i valori aggregati per [All Geographies], [United States], [Oregon] e [Washington] provengono dall'aggregazione sui discendenti di &[Portland]&[OR] e &[Spokane]&[WA]. Nulla proviene dal membro calcolato.  
  
### <a name="remarks"></a>Commenti  
 Solo i membri calcolati globali o della sessione sono consentiti nelle espressioni di sub-SELECT o sottocubi. La presenza di membri calcolati di query nell'espressione MDX genererà un errore durante la valutazione dell'espressione di sub-SELECT o sottocubo.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>   
 [Sub-SELECT nelle query](subselects-in-queries.md)   
 [Proprietà XMLA supportate &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties)  
  
  
