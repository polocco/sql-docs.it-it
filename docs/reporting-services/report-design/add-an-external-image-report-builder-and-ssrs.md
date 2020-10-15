---
title: Aggiungere un'immagine esterna (Generatore report) | Microsoft Docs
description: Informazioni su come aggiungere un'immagine al report da un'origine esterna con la verifica e le autorizzazioni appropriate in Generatore report.
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 81fd4a1f-79a9-4967-86d6-6229413c0995
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b61f3a4fea633045ba064a79243a6e6c7f66149a
ms.sourcegitcommit: fe59f8dc27fd633f5dfce54519d6f5dcea577f56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91934809"
---
# <a name="add-an-external-image-report-builder-and-ssrs"></a>Aggiungere un'immagine esterna (Generatore report e SSRS)
  Le immagini esterne possono trovarsi in un server di report in modalità nativa o in modalità integrata SharePoint oppure in qualsiasi altro sito Web. Quando si includono immagini esterne nel report, è necessario verificare che l'immagine esista e che il lettore del report disponga delle autorizzazioni per accedervi. Per altre informazioni, vedere [Immagini &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/images-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-external-image"></a>Per aggiungere un'immagine esterna  
  
1.  Nella visualizzazione di progettazione report fare clic su **Immagine** nella scheda **Inserisci**.  
  
2.  Nell'area di progettazione fare clic su una casella, quindi trascinarla fino a raggiungere le dimensioni desiderate per l'immagine.  
  
3.  Nella scheda **Generale** della finestra di dialogo **Proprietà immagine** digitare un nome nella casella di testo **Nome** o accettare quello predefinito.  
  
4.  (Facoltativo) Nella casella di testo **Descrizione comando** digitare il testo da visualizzare quando il puntatore del mouse viene posizionato sull'immagine in un report sottoposto a rendering per HTML.  
  
5.  In **Selezionare l'origine dell'immagine**selezionare **Esterna**.  
  
     Per un'immagine in un server di report in modalità nativa, digitare il percorso relativo dell'immagine nella casella **Usare questa immagine**, ad esempio ../images/image1.jpg.  
  
     Per un'immagine in un server di report in modalità integrata SharePoint o in qualsiasi altro sito Web, digitare l'URL completo nella casella **Usare questa immagine**, ad esempio https://\<SharePointservername>/\<site>/Documenti/images/image1.jpg.  
  
     Per altre informazioni, vedere [Specifica di percorsi di elementi esterni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md).  
  
6.  (Facoltativo) Fare clic su **Dimensioni**, **Visibilità**, **Azione**o **Bordo** per impostare ulteriori proprietà per l'elemento del report immagine.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Incorporare un'immagine in un report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/embed-an-image-in-a-report-report-builder-and-ssrs.md)   
 [Aggiungere un'immagine di sfondo &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-a-background-image-report-builder-and-ssrs.md)   
 [Finestra di dialogo Proprietà immagine, Generale &#40;Generatore report e SSRS&#41;](./images-report-builder-and-ssrs.md)  
  
