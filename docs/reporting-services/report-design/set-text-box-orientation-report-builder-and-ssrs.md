---
title: Impostare l'orientamento della casella di testo (Generatore report) | Microsoft Docs
description: Informazioni su come ruotare una casella di testo in direzioni diverse nei report impaginati in Generatore report.
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 64bd53f4-2f31-4732-8c2e-64c7b54b6972
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 058da26bfe4fc5bf8ae5d777a35d0356b463ca11
ms.sourcegitcommit: 02b22274da4a103760a376c4ddf26c4829018454
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2020
ms.locfileid: "84681380"
---
# <a name="set-text-box-orientation-report-builder-and-ssrs"></a>Impostare l'orientamento della casella di testo (Generatore report e SSRS)
In un report impaginato di [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] è possibile ruotare una casella di testo in varie direzioni:   
* Orizzontalmente   
* Verticalmente (rotazione di 90 gradi, con testo leggibile dall'alto verso il basso, ad eccezione dei caratteri dell'Asia orientale)

* Con rotazione di 270 gradi (testo leggibile dal basso verso l'alto).   
  
Essendo applicata sulla casella di testo e non sul testo, la rotazione interessa tutto il testo della casella. Non è possibile specificare direzioni diverse per le parti del testo. Per adattare il testo ruotato ridimensionare manualmente la larghezza della colonna e l'altezza della riga.  
  
 La proprietà WritingMode, che consente di specificare l'orientamento del testo, non è disponibile nella finestra di dialogo **Proprietà casella di testo** . È possibile impostarla invece nel riquadro Proprietà.   
  
## <a name="to-rotate-text"></a>Per ruotare il testo  
  
1.  Creare un nuovo report o aprire un report esistente e [aggiungere una casella di testo](../../reporting-services/report-design/add-move-or-delete-a-text-box-report-builder-and-ssrs.md) all'area di progettazione.  
  
3.  Selezionare la casella di testo che si vuole ruotare.  
  
2.  Se il riquadro Proprietà non è visualizzato, selezionare la casella di controllo **Proprietà** nella scheda **Vista** .  
  
4.  Trovare la proprietà WritingMode nel riquadro Proprietà e selezionare l'orientamento del testo da applicare alla casella di testo.  
  
    > [!NOTE]  
    >  Se le proprietà nel riquadro Proprietà sono organizzate in categorie, WritingMode si trova nella categoria **Localizzazione** .  
  
5.  Nella casella di riepilogo selezionare **Horizontal**, **Vertical**o **Rotate270**.  
  
## <a name="see-also"></a>Vedere anche  
 [Caselle di testo &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/text-boxes-report-builder-and-ssrs.md)   
 [Esercitazione: Formattazione di testo &#40;Generatore report&#41;](../../reporting-services/tutorial-format-text-report-builder.md)  
  
  
