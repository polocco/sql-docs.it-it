---
title: Salvare un report in una raccolta di SharePoint (Report Builder) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4daa1eee-78b7-43d0-8b22-4a98e8fa66ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ab4f9b06758d29ff1f988f37b95ce92206f34d39
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66107682"
---
# <a name="save-a-report-to-a-sharepoint-library-report-builder"></a>Salvataggio di un report in una raccolta di SharePoint (Generatore report)
  Per salvare un report in un server di report configurato per l'integrazione con SharePoint, è necessario accedere al server di SharePoint e stabilire una connessione con il server di report. Nella definizione del report tutti i riferimenti a elementi correlati al report devono utilizzare valori specifici di un server di report di SharePoint. Tra gli elementi correlati sono inclusi sottoreport, report drill-through e risorse quali immagini basate sul Web. Per altre informazioni, vedere [Specifica di percorsi di elementi esterni &#40;Generatore report e SSRS&#41;](../report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md).  
  
 Per impostare le proprietà del progetto, è necessario disporre dell'autorizzazione **Membro** o **Proprietario** per il sito di SharePoint.  
  
### <a name="to-save-a-report-to-a-sharepoint-site"></a>Per salvare un report in un sito di SharePoint  
  
1.  Dal pulsante Generatore report fare clic su **Salva**. Verrà visualizzata la finestra **di dialogo Salva come**_\<elemento del report>_ .  
  
    > [!NOTE]  
    >  Se si sta salvando di nuovo un report, questo viene automaticamente risalvato nel relativo percorso precedente. Usare l'opzione **Salva con nome** per modificare il percorso.  
  
2.  Facoltativamente, fare clic su **Siti e server recenti** per visualizzare un elenco di server di report e di siti di SharePoint usati di recente.  
  
3.  Passare al sito di SharePoint, quindi fare clic su **Salva**.  
  
    > [!NOTE]  
    >  Se si lascia un report modificato per più di 10 ore senza salvarlo, questo viene disconnesso dal server senza essere salvato. In questo caso, nella barra di stato in basso a destra fare clic su **Disconnetti**, quindi su **Connetti**. Il server più recente si troverà nell'elenco di server disponibili. Selezionarlo e il report verrà riconnesso.  
  
## <a name="see-also"></a>Vedi anche  
 [Ricerca, visualizzazione e gestione dei report &#40;Generatore report e SSRS&#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
