---
title: Aggiungere percorsi personalizzati a una mappa (Generatore report) | Microsoft Docs
description: Informazioni su come aggiungere località personalizzate a una mappa aggiunta a un report impaginato in Generatore report.
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
f1_keywords:
- MICROSOFT.REPORTDESIGNER.MAPPOINT.POINTTEMPLATE
ms.assetid: 7d36faae-5bcc-446a-9eba-f42349cafacb
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: cf6610f1abb446d27825e8d2e95677100a69184d
ms.sourcegitcommit: 93e4fd75e8fe0cc85e7949c9adf23b0e1c275465
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/01/2020
ms.locfileid: "84255674"
---
# <a name="add-custom-locations-to-a-map-report-builder-and-ssrs"></a>Aggiungere percorsi personalizzati a una mappa (Generatore report e SSRS)
  Dopo avere aggiunto una mappa a un report impaginato di [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] , è possibile aggiungere percorsi punto personalizzati.  
  
 Le proprietà di visualizzazione per tutti i punti su un livello vengono controllate impostando le opzioni per le proprietà punto per il livello. Per un punto incorporato selezionato, è possibile ignorare le proprietà di visualizzazione.  
  
> [!NOTE]  
>  Quando si ignorano le proprietà di visualizzazione del livello per il punto incorporato, le modifiche apportate non sono reversibili.  
  
 Per altre informazioni, vedere [Variare la visualizzazione di poligoni, linee e punti in base a regole e dati analitici &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/vary-polygon-line-and-point-display-by-rules-and-analytical-data.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-add-a-point-layer"></a>Per aggiungere un livello punto  
  
1.  Nell'area di progettazione del report fare clic sulla mappa per selezionarla e visualizzare il riquadro mappa.  
  
2.  Sulla barra degli strumenti fare clic su **Aggiungi livello**.  
  
3.  Nell'elenco a discesa fare clic su **Aggiungi livello punto**. Alla mappa viene aggiunto un livello punto senza alcun punto. Per impostazione predefinita, il livello punto è pronto per i punti incorporati.  
  
## <a name="to-add-a-custom-point"></a>Per aggiungere un punto personalizzato  
  
1.  Nell'area di progettazione del report fare clic sulla mappa per selezionarla e visualizzare il riquadro mappa.  
  
2.  Nel riquadro mappa fare clic con il pulsante destro del mouse su un livello punto con il tipo **Incorporato**, quindi scegliere **Aggiungi punto**. Il cursore passa alla selezione di precisione.  
  
3.  Per aggiungere un punto fare clic su una posizione sulla mappa. Un punto incorporato viene aggiunto al livello selezionato nella posizione scelta.  
  
## <a name="to-customize-the-display-for-an-embedded-point"></a>Per personalizzare la visualizzazione per un punto incorporato  
  
1.  Fare clic con il pulsante destro del mouse sul punto, quindi scegliere **Proprietà punto**. Viene visualizzata la finestra di dialogo **Proprietà punto incorporato nella mappa** .  
  
2.  Fare clic su **Ignora opzioni punto per questo livello**. Nel riquadro sinistro vengono visualizzate più pagine delle proprietà.  
  
3.  Fare clic sulle pagine e impostare le proprietà di visualizzazione che si desidera applicare a questo punto.  
  
## <a name="see-also"></a>Vedere anche  
 [Mappe &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/maps-report-builder-and-ssrs.md)   
 [Variare la visualizzazione di poligoni, linee e punti in base a regole e dati analitici &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)  
  
  
