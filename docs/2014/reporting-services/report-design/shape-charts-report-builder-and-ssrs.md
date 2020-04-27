---
title: Grafici con forme (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4b8404c1-aa89-4350-8bd6-203bc0446ee4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a7194147f60fa039caab1f9a712b9f6f75e2617d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66104943"
---
# <a name="shape-charts-report-builder-and-ssrs"></a>Grafici con forme (Generatore report e SSRS)
  In un grafico con forme i dati relativi ai valori vengono visualizzati come percentuali di un intero. I grafici con forme vengono solitamente utilizzati per indicare confronti proporzionali tra valori diversi in un set. Le categorie sono rappresentate da singoli segmenti della forma. Le dimensioni del segmento sono determinate dal valore. L'utilizzo dei grafici con forme è simile a quello dei grafici a torta, ad eccezione del fatto che le categorie vengono ordinate dal valore più alto a quello più basso.  
  
 In un grafico a imbuto i valori vengono visualizzati come proporzioni in decremento progressivo. Le dimensioni dell'area sono determinate dal valore delle serie espresso come percentuale del totale di tutti i valori. Ad esempio, è possibile utilizzare un grafico a imbuto per visualizzare le tendenze dei visitatori di un sito Web. Nel grafico a imbuto verrà visualizzata un'area ampia nella parte superiore, a indicare gli accessi dei visitatori alla home page, e altre aree più piccole in proporzione. Per altre informazioni sull'aggiunta di dati a un grafico a imbuto, vedere [Grafici &#40;Generatore report e SSRS&#41;](charts-report-builder-and-ssrs.md).  
  
 Nella figura seguente è illustrato un esempio di grafico a imbuto.  
  
 ![Grafico a imbuto](../media/rs-funnelchart.gif "Grafico a imbuto")  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a>Variazioni  
  
-   **Piramide**. In un grafico a piramide vengono visualizzati dati proporzionali in modo simile a una piramide.  
  
## <a name="data-considerations-for-shape-charts"></a>Considerazioni sui dati per i grafici con forme  
  
-   I grafici con forme vengono utilizzati di frequente nei report grazie al loro impatto visivo. Si tratta, tuttavia, di un tipo di grafico estremamente semplificato che potrebbe non rappresentare i dati nel modo più efficace possibile. Utilizzare un grafico con forme solo dopo che i dati sono stati aggregati a un massimo di sette punti dati. In generale, utilizzare questo tipo di grafico per visualizzare una sola categoria per ogni area dati.  
  
-   Nei grafici con forme ogni gruppo di dati viene visualizzato come segmento distinto. È necessario aggiungere almeno un campo dati e un campo categoria. Se viene aggiunto più di un campo dati, entrambi i campi dati verranno visualizzati nello stesso grafico.  
  
-   I grafici con forme sono particolarmente utili per visualizzare le percentuali proporzionali in maniera ordinata. Per garantire la coerenza, i valori del set di dati nel grafico non vengono tuttavia ordinati per impostazione predefinita. È possibile ordinare i valori dal più alto al più basso per rappresentare i dati sotto forma di imbuto o piramide e ottenere una maggiore precisione. Per altre informazioni, vedere [Filtro, raggruppamento e ordinamento di dati &#40;Generatore report e SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md).  
  
-   I valori Null, vuoti, negativi e zero non hanno effetto nel calcolo dei rapporti. Per questo motivo, tali valori non vengono visualizzati in un grafico con forme. Se si desidera indicare visivamente questi tipi di valori nel grafico, scegliere un tipo di grafico diverso dal grafico con forme. Per ulteriori informazioni sull'aggiunta di punti vuoti a un grafico senza forme, vedere [aggiungere punti vuoti al grafico &#40;Generatore report e SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md).  
  
-   Se i colori di un grafico con forme vengono definiti utilizzando una tavolozza personalizzata, assicurarsi che tale tavolozza contenga un numero di colori sufficiente per evidenziare ogni punto dati in un colore univoco. Per altre informazioni, vedere [Formattazione dei colori delle serie in un grafico &#40;Generatore report e SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md).  
  
-   A differenza di tutti gli altri tipi di grafico, nella legenda di un grafico con forme verranno visualizzati singoli punti dati, anziché singole serie.  
  
-   Le impostazioni per l'asse dei valori e delle categorie vengono ignorate per i grafici a imbuto. Se sono presenti più categorie o gruppi di serie, le etichette dei gruppi vengono visualizzate nella legenda del grafico.  
  
-   I tipi di grafico con forme non possono essere combinati con altri tipi di grafico nella stessa area del grafico. Per rappresentare i confronti tra i dati visualizzati in un grafico con forme e quelli visualizzati in un altro tipo di grafico, è necessario aggiungere una seconda area del grafico.  
  
-   L'aggiunta di effetti 3D consente di migliorare notevolmente l'aspetto complessivo di un tipo di grafico con forme.  
  
-   È possibile applicare stili di disegno aggiuntivi ai grafici a torta e ad anello per un maggiore impatto visivo. Vedere [Formattazione dei colori delle serie in un grafico &#40;Generatore report e SSRS&#41;](formatting-series-colors-on-a-chart-report-builder-and-ssrs.md) per altre informazioni.  
  
## <a name="see-also"></a>Vedi anche  
 [Grafici &#40;Generatore report e SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Formattazione di un grafico &#40;Generatore report e SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Punti dati vuoti e null nei grafici &#40;Generatore report e SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)   
 [Grafici a torta &#40;Generatore report e SSRS&#41;](pie-charts-report-builder-and-ssrs.md)  
  
  
