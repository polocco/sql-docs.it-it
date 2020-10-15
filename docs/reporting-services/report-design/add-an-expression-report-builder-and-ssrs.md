---
title: Aggiungere un'espressione (Generatore report) | Microsoft Docs
description: Informazioni su come usare le espressioni per definire le proprietà degli elementi del report, i filtri e i valori dei parametri in Generatore report.
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: a60ee091-b4ed-41e1-9b6a-032c316cd03f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b5fc151010d455bb3fee29b92bc86adf24da32f4
ms.sourcegitcommit: fe59f8dc27fd633f5dfce54519d6f5dcea577f56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91935146"
---
# <a name="add-an-expression-report-builder-and-ssrs"></a>Aggiungere un'espressione (Generatore report e SSRS)
  Le espressioni vengono usate in un report per definire proprietà, filtri, gruppi, criteri di ordinamento, stringhe di connessione e valori di parametri degli elementi del report. Le espressioni iniziano con il segno di uguale (=) e sono scritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]. Vengono valutate in fase di esecuzione dal componente Elaborazione report che combina i risultati della valutazione e gli elementi di layout del report.  
  
 Le espressioni possono essere semplici o complesse. Le espressioni semplici fanno riferimento a un solo elemento in una raccolta predefinita. Le espressioni complesse possono contenere costanti, operatori, elementi di raccolta globali e chiamate di funzioni. Per altre informazioni, vedere [Espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-expression-to-a-text-box"></a>Per aggiungere un'espressione a una casella di testo  
  
-   In visualizzazione **Progettazione** fare clic sulla casella di testo nell'area di progettazione in cui si desidera aggiungere un'espressione.  
  
    -   In caso di un'espressione semplice, digitare il testo visualizzato per l'espressione nella casella di testo. Per il campo del set di dati Sales, ad esempio, digitare `[Sales]`.  
  
    -   In caso di un'espressione complessa, fare clic con il pulsante destro del mouse sulla casella di testo e selezionare **Espressione**. Verrà visualizzata la finestra di dialogo **Espressione** . Digitare o creare in modo interattivo l'espressione dopo il segno '=' nel riquadro dell'espressione, quindi fare clic su OK.  
  
         L'espressione verrà visualizzata nell'area di progettazione come `<<Expr>>`.  
  
## <a name="see-also"></a>Vedere anche  
 [Formattazione di testo e segnaposto &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md)   
 [Caselle di testo &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/text-boxes-report-builder-and-ssrs.md)   
 [Utilizzo delle espressioni nei report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Esempi di equazioni di filtro &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/filter-equation-examples-report-builder-and-ssrs.md)   
 [Esempi di espressioni di raggruppamento &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/group-expression-examples-report-builder-and-ssrs.md)   
 [Finestra di dialogo Espressione &#40;Generatore report&#41;](./expressions-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Aggiungere codice a un report &#40;SSRS&#41;](../../reporting-services/report-design/add-code-to-a-report-ssrs.md)  
  
