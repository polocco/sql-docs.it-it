---
title: 3D, Bevel, and Other Effects in a Chart (Report Builder and SSRS) (Effetti 3D, smussature e altri effetti in un grafico (Generatore report e SSRS)) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10156"
ms.assetid: 18ef2119-2931-43ae-9078-f39b460462dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7ae056d72d3966a9787ac2d52f89689ae9f6a799
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66106301"
---
# <a name="3d-bevel-and-other-effects-in-a-chart-report-builder-and-ssrs"></a>Effetti 3D, smussature e altri effetti in un grafico (Generatore report e SSRS)
  Gli effetti tridimensionali (3D) possono essere utilizzati per fornire profondità e aggiungere un impatto visivo al grafico. Ad esempio, se si desidera evidenziare una particolare sezione di un grafico a torta esplosa, è possibile ruotare e modificare la prospettiva del grafico in modo che si noti prima di tutto tale sezione. Quando al grafico vengono applicati effetti 3D, tutti i colori delle sfumature e gli stili di tratteggio vengono disabilitati.  
  
 Gli effetti tridimensionali possono essere applicati a singoli grafici ed è possibile visualizzare grafici 2D e 3D nello stesso report.  
  
 Per tutti i tipi di grafico, è possibile aggiungere effetti tridimensionali a un'area del grafico nella finestra di dialogo **Proprietà area grafico** selezionando **Abilita 3D**. Per altre informazioni, vedere [Aggiungere effetti 3D a un grafico &#40;Generatore report e SSRS&#41;](chart-effects-add-3d-effects-report-builder.md).  
  
 Per aumentare l'impatto visivo dei grafici, è anche possibile aggiungere gli stili smussato, rilievo e trama nei grafici a barre, a torta e ad anello, nonché negli istogrammi. Per altre informazioni, vedere [Aggiungere stili smussato, rilievo e trama a un grafico &#40;Generatore report e SSRS&#41;](chart-effects-add-bevel-emboss-or-texture-report-builder.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="coordinate-based-three-dimensional-charts"></a>Grafici tridimensionali basati su coordinate  
 Quando si utilizzano i tipi di grafico basati su coordinate (istogramma, a barre, ad area, a punti, a linee e con intervalli), tramite gli effetti 3D viene visualizzato un terzo asse, noto come "asse Z". L'introduzione di questo terzo asse consente di applicare un'ampia varietà di miglioramenti visivi al grafico.  
  
### <a name="changing-the-white-space-in-a-3d-chart"></a>Modifica dello spazio vuoto in un grafico 3D  
 Quando si visualizza un'area del grafico in modalità tridimensionale, ogni serie è indicata in una riga distinta lungo l'asse Z. Per variare la quantità di spazio tra ogni serie, modificare la profondità gap punti del grafico cambiando la proprietà **Point Gap Depth** nella finestra di dialogo Effetti 3D.  
  
### <a name="changing-the-projection-of-a-3d-chart"></a>Modifica della proiezione di un grafico 3D  
 Esistono due tipi di proiezioni 3D: obliqua e prospettiva. Una proiezione obliqua aggiunge a un grafico bidimensionale una dimensione di profondità. L'asse Z viene disegnato ad angoli uguali rispetto agli assi orizzontale e verticale, che rimangono perpendicolari tra loro come nei grafici bidimensionali.  
  
 La proiezione prospettiva trasforma il grafico stimando un piano visivo e ridisegnando il grafico come se venisse visualizzato da tale punto. Il valore **Rotazione** sposta verticalmente il campo visivo dal livello 0 verso l'alto al livello 90. Il valore **Inclinazione** sposta l'angolo di visualizzazione a sinistra o a destra. Il valore 0 equivale a una visualizzazione bidimensionale del grafico. Il valore **Prospettiva** definisce la percentuale di distorsione che verrà usata durante la visualizzazione della proiezione. Con questo tipo di proiezione, le proporzioni del grafico vengono mantenute, ma l'aspetto diventa distorto. Per questo motivo, l'utilizzo di un grado inferiore di prospettiva risulta più efficace.  
  
> [!NOTE]  
>  Le proiezioni oblique e prospettive sono tipi distinti di proiezioni, quindi non possono essere utilizzate insieme nello stesso grafico.  
  
### <a name="clustering-data"></a>Clustering dei dati  
 Nel grafici 2D vengono visualizzate più serie di dati affiancate. Con il clustering le singole serie vengono visualizzate in righe distinte in un grafico 3D. Se ad esempio un grafico contiene tre serie di punti dati, con il clustering ognuna di esse verrà visualizzata in una riga distinta lungo l'asse Z. Per impostazione predefinita, tutti i tipi di grafico visualizzati in 3D sono in cluster.  
  
 È possibile disabilitare il clustering per i grafici a barre e gli istogrammi. In questo caso, più serie di barre e colonne vengono visualizzate affiancate in un'unica riga.  
  
## <a name="shape-based-three-dimensional-charts"></a>Grafici tridimensionali basati su forma  
 Per i tipi di grafico basati su forma (a torta, ad anello, a imbuto e a piramide) sono disponibili meno effetti tridimensionali. Quando si utilizzano questi tipi di grafico, è possibile modificare solo i valori relativi a rotazione e inclinazione.  
  
## <a name="rotations"></a>Rotazioni  
 È possibile ruotare i grafici in orizzontale e in verticale da -90 a 90 gradi. Un angolo orizzontale positivo ruoterà il grafico in senso antiorario lungo l'asse X, mentre un angolo verticale positivo lo ruoterà in senso orario lungo l'asse Y.  
  
## <a name="highlighting-3d-effects"></a>Evidenziazione degli effetti 3D  
 È possibile aggiungere stili di evidenziazione a un grafico 3D tramite la proprietà **Shading** visualizzata sotto Area3DStyle nel riquadro Proprietà quando si seleziona l'area del grafico. Un semplice stile di illuminazione applica la stessa tonalità agli elementi dell'area del grafico. Uno stile realistico modifica le tonalità degli elementi dell'area del grafico a seconda di un angolo di illuminazione specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Formattazione delle etichette degli assi in un grafico &#40;Generatore report e SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Formattazione di un grafico &#40;Generatore report e SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Aggiungere effetti 3D a un grafico &#40;Generatore report e SSRS&#41;](chart-effects-add-3d-effects-report-builder.md)  
  
  
