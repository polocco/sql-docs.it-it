---
title: Esempi di espressioni di raggruppamento (Generatore report) | Microsoft Docs
description: Informazioni su come raggruppare i dati in base a un solo campo oppure su come creare espressioni più complesse che consentono di identificare i dati in base ai quali eseguire il raggruppamento in Generatore report.
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
helpviewer_keywords:
- data [Reporting Services], grouping
- grouping data
- expressions [Reporting Services], adding
- groups [Reporting Services], expressions
ms.assetid: 34cd0249-fc74-4cf2-ba11-7b072992bfd2
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ead7e4c893c667021770df4977244bb509c0d79c
ms.sourcegitcommit: f898aa83561e94626024916932568ab05e73b656
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2020
ms.locfileid: "84012419"
---
# <a name="group-expression-examples-report-builder-and-ssrs"></a>Esempi di espressioni di raggruppamento (Generatore report e SSRS)
  In un'area dati è possibile raggruppare i dati in base a un solo campo oppure creare espressioni più complesse che consentono di identificare i dati in base a quali eseguire il raggruppamento. Le espressioni complesse includono riferimenti a più campi o parametri, istruzioni condizionali o codice personalizzato. Quando si definisce un gruppo per un'area dati, queste espressioni vengono aggiunte alle proprietà del **gruppo**. Per altre informazioni, vedere [Aggiunta o eliminazione di un gruppo in un'area dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md).  
  
 Per unire due o più gruppi basati sulle espressioni di campo semplice, aggiungere ogni campo all'elenco delle espressioni di raggruppamento nella definizione del gruppo.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="examples-of-group-expressions"></a>Esempi di espressioni di raggruppamento  
 Nella tabella seguente sono disponibili esempi di espressioni di raggruppamento utilizzabili per la definizione di un gruppo.  
  
|Descrizione|Expression|  
|-----------------|----------------|  
|Raggruppamento in base al campo `Region` .|`=Fields!Region.Value`|  
|Raggruppamento in base a cognome e nome.|`=Fields!LastName.Value`<br /><br /> `=Fields!FirstName.Value`|  
|Raggruppamento in base alla prima lettera del cognome.|`=Fields!LastName.Value.Substring(0,1)`|  
|Raggruppamento per parametro, in base alla selezione dell'utente.<br /><br /> In questo esempio il parametro `GroupBy` deve essere basato su un elenco di valori disponibili che fornisce una scelta valida in base a cui eseguire il raggruppamento.|`=Fields(Parameters!GroupBy.Value).Value`|  
|Raggruppamento per tre intervalli di età separati:<br /><br /> "Under 21", "Tra 21 e 50" e "Over 50".|`=IIF(First(Fields!Age.Value)<21,"Under 21",(IIF(First(Fields!Age.Value)>=21 AND First(Fields!Age.Value)<=50,"Between 21 and 50","Over 50")))`|  
|Raggruppamento in base a molti intervalli di età. Questo esempio contiene codice personalizzato, scritto in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET, che restituisce una stringa per gli intervalli seguenti:<br /><br /> 25 o inferiore<br /><br /> Da 26 a 50<br /><br /> Da 51 a 75<br /><br /> Over 75|`=Code.GetRangeValueByAge(Fields!Age.Value)`<br /><br /> Codice personalizzato:<br /><br /> `Function GetRangeValueByAge(ByVal age As Integer) As String`<br /><br /> `Select Case age`<br /><br /> `Case 0 To 25`<br /><br /> `GetRangeValueByByAge = "25 or Under"`<br /><br /> `Case 26 To 50`<br /><br /> `GetRangeValueByByAge = "26 to 50"`<br /><br /> `Case 51 to 75`<br /><br /> `GetRangeValueByByAge = "51 to 75"`<br /><br /> `Case Else`<br /><br /> `GetRangeValueByByAge = "Over 75"`<br /><br /> `End Select`<br /><br /> `Return GetRangeValueByByAge`<br /><br /> `End Function`|  
  
## <a name="see-also"></a>Vedere anche  
 [Filtro, raggruppamento e ordinamento di dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Riferimenti a codice personalizzato e ad assembly in espressioni in Progettazione report &#40;SSRS&#41;](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)  
  
  
