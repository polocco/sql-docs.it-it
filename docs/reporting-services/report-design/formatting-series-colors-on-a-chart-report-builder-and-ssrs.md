---
title: Formattazione dei colori delle serie in un grafico (Generatore report) | Microsoft Docs
description: Informazioni su come usare le numerose tavolozze predefinite per i grafici o come definire una tavolozza personalizzata di propria ideazione in Generatore report.
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
f1_keywords:
- "10245"
- "10252"
- sql13.rtp.rptdesigner.serieslabelproperties.borders.f1
- sql13.rtp.rptdesigner.seriesproperties.borders.f1
ms.assetid: fe541501-cac5-47b1-b95f-c410db789190
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a8e099cb6660665ef36e287797e46c432615f1bf
ms.sourcegitcommit: 5c7634b007f6808c87094174b80376cb20545d5f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84880276"
---
# <a name="formatting-series-colors-on-a-chart-report-builder-and-ssrs"></a>Formattazione dei colori delle serie in un grafico (Generatore report e SSRS)
  In Reporting Services sono disponibili diverse tavolozze incorporate per i grafici o è possibile definirne di personalizzate. Per impostazione predefinita, nei grafici viene utilizzata la tavolozza dei colori **Pacific** incorporata per riempire ogni serie. Tali colori vengono visualizzati anche nella legenda. Quando al grafico vengono aggiunte più serie, a queste vengono assegnati i colori in base all'ordine dei colori definito nella tavolozza.  
  
 Se il numero di serie è maggiore di quello dei colori disponibili nella tavolozza, i colori verranno riutilizzati. In questo modo è possibile che due serie presentino lo stesso colore. Ciò si verifica di frequente nei casi in cui si utilizza un grafico con forme, in cui a ogni punto dati viene assegnato un colore della tavolozza. Per evitare confusione, definire una tavolozza personalizzata con almeno un numero di colori pari a quello delle serie presenti nel grafico.  
  
 È possibile selezionare una nuova tavolozza o definire una tavolozza personalizzata dal riquadro Proprietà. Per altre informazioni, vedere [Definire i colori in un grafico mediante la tavolozza &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="using-built-in-palettes"></a>Utilizzo di tavolozze incorporate  
 In Reporting Services è disponibile un elenco di tavolozze incorporate predefinite che è possibile utilizzare per definire un set di colori per le serie del grafico. Tutte le tavolozze incorporate contengono tra i 10 e i 16 valori di colori. Non è possibile estendere la tavolozza incorporata per includere più colori. Pertanto, se sono richiesti più di 16 colori, è necessario definire una tavolozza personalizzata.  
  
 Se si stampa un report, utilizzare la tavolozza con **scala di grigi** , che applica sfumature di nero e bianco per la rappresentazione delle serie di un grafico.  
  
 La tavolozza predefinita è stata utilizzata come tavolozza dei grafici predefinita nelle versioni precedenti di Reporting Services e viene tuttora utilizzata per una questione di coerenza. I grafici vengono aggiornati perfettamente con la tavolozza predefinita. Tuttavia, in seguito all'aggiornamento, la tavolozza può essere cambiata.  
  
## <a name="using-custom-palettes"></a>Utilizzo di tavolozze personalizzate  
 Se si desidera applicare colori diversi al grafico, utilizzare una tavolozza personalizzata. Una tavolozza personalizzata consente di aggiungere colori nell'ordine di visualizzazione desiderato nel grafico e risulta utile soprattutto se il numero di serie del grafico non è noto in fase di progettazione. Per altre informazioni, vedere [Definire i colori in un grafico mediante la tavolozza &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md).  
  
## <a name="using-a-color-fill-on-each-series"></a>Utilizzo di un colore di riempimento su ogni serie  
 Per definire colori personalizzati nel grafico è anche possibile specificare un colore per ogni serie. A tale scopo, aprire la finestra di dialogo **Proprietà serie** e impostare la proprietà **Color** per **Riempimento**. Questo approccio sostituisce tutte le tavolozze definite. Generalmente, è preferibile utilizzare una tavolozza personalizzata per definire i colori desiderati poiché il numero di serie nel set di dati non può essere noto fino a quando non viene eseguita l'elaborazione del report.  
  
 Questo approccio è adatto a situazioni in cui si desidera impostare in modo condizionale il colore della serie in base a un'espressione.  Per altre informazioni, vedere [Formattazione dei punti dati di un grafico &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Specificare i colori coerenti in più grafici con forme &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/specify-consistent-colors-across-multiple-shape-charts-report-builder-and-ssrs.md)  
  
 [Definire i colori in un grafico mediante la tavolozza &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs.md)  
  
 [Evidenziare i dati del grafico mediante l'aggiunta di strisce &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/highlight-chart-data-by-adding-strip-lines-report-builder-and-ssrs.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Formattazione di un grafico &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [Aggiungere stili smussato, rilievo e trama a un grafico &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/chart-effects-add-bevel-emboss-or-texture-report-builder.md)   
 [Grafici &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Formattazione della legenda in un grafico &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/chart-legend-formatting-report-builder.md)  
  
  
