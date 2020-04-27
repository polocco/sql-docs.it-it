---
title: Add 3D Effects to a Chart (Report Builder and SSRS) (Aggiungere effetti 3D a un grafico (Generatore report e SSRS)) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ab9625d8-6557-4a4d-8123-eefa7c066ff5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 07934e74138f17317eb0258e2b3ad0fa6d26254a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66106316"
---
# <a name="add-3d-effects-to-a-chart-report-builder-and-ssrs"></a>Aggiungere effetti 3D a un grafico (Generatore report e SSRS)
  Gli effetti tridimensionali (3D) possono essere utilizzati per fornire profondità e aggiungere un impatto visivo al grafico. Ad esempio, se si desidera evidenziare una particolare sezione di un grafico a torta esplosa, è possibile ruotare e modificare la prospettiva del grafico in modo che si noti prima di tutto tale sezione. Quando al grafico vengono applicati effetti 3D, tutti i colori delle sfumature e gli stili di tratteggio vengono disabilitati.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-apply-3d-effects-to-a-range-area-line-scatter-or-polar-chart"></a>Per applicare effetti 3D a un grafico a intervallo, ad area, a linee, a dispersione o polare  
  
1.  Fare clic con il pulsante destro del mouse in un punto qualsiasi nell'area del grafico e quindi scegliere **Effetti 3D**. Verrà visualizzata la finestra di dialogo **Proprietà area grafico** .  
  
2.  In **Opzioni 3D**selezionare l'opzione **Abilita 3D** .  
  
3.  (Facoltativo) In **Opzioni 3D**è possibile impostare un'ampia varietà di proprietà relative alle opzioni degli angoli e delle scene 3D. Per altre informazioni su queste proprietà, vedere [Effetti 3D, smussature e altri effetti in un grafico &#40;Generatore report e SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md).  
  
4.  Fare clic su **OK**.  
  
### <a name="to-apply-3d-effects-to-a-funnel-chart"></a>Per applicare effetti 3D a un grafico a imbuto  
  
1.  Fare clic con il pulsante destro del mouse in un punto qualsiasi nell'area del grafico e quindi scegliere **Effetti 3D**. Verrà visualizzata la finestra di dialogo **Proprietà area grafico** .  
  
2.  In **Opzioni 3D**selezionare l'opzione **Abilita 3D** . Fare clic su **OK**.  
  
3.  (Facoltativo) Per personalizzare l'aspetto visivo del grafico a imbuto, è possibile aprire il riquadro Proprietà e modificare le proprietà specifiche di questo tipo di grafico.  
  
    1.  Aprire il riquadro Proprietà.  
  
    2.  Nell'area di progettazione fare clic in un punto qualsiasi dell'imbuto. Le proprietà della serie del grafico a imbuto verranno visualizzate nel riquadro Proprietà.  
  
    3.  Nella sezione **Generale** espandere il nodo **CustomAttributes** .  
  
    4.  Per la proprietà **Funnel3DDrawingStyle** , selezionare se l'imbuto verrà visualizzato con una forma circolare o quadrata.  
  
    5.  Per la proprietà **Funnel3DRotationAngle** , impostare un valore compreso tra -10 e 10. Questa opzione determinerà il grado di inclinazione che verrà visualizzato nel grafico a imbuto 3D.  
  
### <a name="to-apply-3d-effects-to-a-pie-chart"></a>Per applicare effetti 3D a un grafico a torta  
  
1.  Fare clic con il pulsante destro del mouse in un punto qualsiasi nell'area del grafico, quindi scegliere Effetti 3D. Verrà visualizzata la finestra di dialogo **Proprietà area grafico** .  
  
2.  In **Opzioni 3D**selezionare l'opzione **Abilita 3D** . Fare clic su **OK**.  
  
3.  (Facoltativo) In **Rotazione**digitare un valore intero che rappresenta la rotazione orizzontale del grafico a torta.  
  
4.  (Facoltativo) In **Inclinazione**digitare un valore intero che rappresenta la rotazione di inclinazione verticale del grafico a torta.  
  
5.  Fare clic su **OK**.  
  
### <a name="to-apply-3d-effects-to-a-bar-or-column-chart"></a>Per applicare effetti 3D a un grafico a barre o a un istogramma  
  
1.  Fare clic con il pulsante destro del mouse in un punto qualsiasi nell'area del grafico e quindi scegliere **Effetti 3D**. Verrà visualizzata la finestra di dialogo **Proprietà area grafico** .  
  
2.  Selezionare l'opzione **Abilita 3D** . Fare clic su **OK**.  
  
3.  (Facoltativo) Selezionare l'opzione **Abilita clustering serie** . Se il grafico contiene più serie di barre o colonne, con questa opzione le serie verranno visualizzate come cluster. Per impostazione predefinita, più serie di barre o colonne vengono visualizzate affiancate.  
  
4.  Fare clic su **OK**.  
  
5.  (Facoltativo) Per aggiungere effetti di cilindro a un grafico a barre o a un istogramma, effettuare le operazioni seguenti:  
  
    1.  Aprire il riquadro Proprietà.  
  
    2.  Nell'area di progettazione fare clic su una delle barre della serie. Le proprietà della serie verranno visualizzate nel riquadro Proprietà.  
  
    3.  Nella sezione **Generale** espandere il nodo **CustomAttributes** .  
  
    4.  Per la proprietà **DrawingStyle** , specificare il valore **Cilindro** .  
  
## <a name="see-also"></a>Vedere anche  
 [Effetti 3D, smussature e altri effetti in un grafico &#40;Generatore report e SSRS&#41;](chart-effects-3d-bevel-and-other-report-builder.md)   
 [Formattazione di un grafico &#40;Generatore report e SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Grafici &#40;Generatore report e SSRS&#41;](charts-report-builder-and-ssrs.md)  
  
  
