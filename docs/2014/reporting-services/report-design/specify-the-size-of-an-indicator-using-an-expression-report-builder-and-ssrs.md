---
title: Specificare le dimensioni di un indicatore tramite un'espressione (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ab0b86f1-4882-4258-a2b6-c612faecfa4b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 862e0f5dbe9ef15c33aad13a7f5480ffb7b07150
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66104863"
---
# <a name="specify-the-size-of-an-indicator-using-an-expression-report-builder-and-ssrs"></a>Specificare le dimensioni di un indicatore tramite un'espressione (Generatore report e SSRS)
  Per migliorare l'impatto visivo degli indicatori, oltre al colore, alla direzione e alla forma è possibile usare anche le dimensioni.  
  
 Un indicatore dispone di una raccolta di stati dell'indicatore denominata IndicatorStates. La raccolta IndicatorStates dispone in genere di più stati. Ogni stato è un membro della raccolta e viene rappresentato da un'icona. Gli stati, insieme, formano la raccolta IndicatorsStates.  
  
 Per configurare dinamicamente le dimensioni delle icone, è possibile impostare le proprietà dei membri della raccolta IndicatorsStates nel riquadro Proprietà di Generatore report. Se il riquadro **Proprietà** non è visibile, selezionare **Proprietà** nella scheda **Visualizza**.  
  
> [!NOTE]  
>  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]usare la finestra **Proprietà** per impostare le proprietà dei membri. Se la finestra **Proprietà** non è aperta, premere il tasto F4.  
  
 Il riquadro **Proprietà** consente l'accesso alle proprietà della raccolta IndicatorStates di un indicatore. Le diverse dimensioni delle icone vengono configurate impostando la proprietà ScaleFactor dei membri raccolta IndicatorStates tramite un'espressione. Per altre informazioni, vedere [Espressioni &#40;Generatore report e SSRS&#41;](expressions-report-builder-and-ssrs.md).  
  
 L'espressione utilizzata in questa procedura è stata usata anche per generare il report con diverse dimensioni di indicatori, mostrato in [Indicatori &#40;Generatore report e SSRS&#41;](indicators-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-the-indicator-icon-size-using-an-expression"></a>Per specificare le dimensioni dell'icona dell'indicatore tramite un'espressione  
  
1.  Scegliere l'indicatore che si desidera modificare.  
  
2.  Nel riquadro Proprietà individuare la proprietà IndicatorStates.  
  
     Se il riquadro Proprietà è organizzato per categorie, IndicatorStates si trova nella categoria **Stati** .  
  
3.  Fare clic sul pulsante con i puntini di sospensione **(...)** accanto a IndicatorStates. Verrà visualizzata la finestra di dialogo **Editor raccolte IndicatorState** .  
  
     Selezionare tutti i membri della raccolta.  
  
4.  Nell'elenco **Proprietà a selezione multipla** fare clic sulla freccia in giù accanto a ScaleFactor, quindi su **Espressione**.  
  
5.  Nella finestra di dialogo **Espressione** scrivere l'espressione.  
  
     L'espressione di esempio seguente consente di modificare le dimensioni dell'icona in base al valore del campo **SalesYTD** .  
  
     `=IIF(Fields!SalesYTD.value = 0,0,Fields!SalesYTD.value/Max(Fields!SalesYTD.value,"Indicator"))`  
  
     Per altre informazioni, vedere [Esempi di espressioni &#40;Generatore report e SSRS&#41;](expression-examples-report-builder-and-ssrs.md).  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Indicatori &#40;Generatore report e SSRS&#41;](indicators-report-builder-and-ssrs.md)  
  
  
