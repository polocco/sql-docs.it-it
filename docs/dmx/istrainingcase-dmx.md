---
description: IsTrainingCase (DMX)
title: IsTrainingCase (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5eb68d0aaa0d19fb903154b8d5c4d4135b57883e
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726149"
---
# <a name="istrainingcase-dmx"></a>IsTrainingCase (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Indica se un case viene utilizzato come case di training per il modello o la struttura di data mining specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
IsTrainingCase()  
```  
  
## <a name="result-type"></a>Tipo di risultato  
 Restituisce **true** se il case è una parte del set di dati di training. in caso contrario, **false**.  
  
## <a name="remarks"></a>Osservazioni  
 Se si utilizza la Creazione guidata modello di data mining per creare una struttura di data mining e il modello di data mining correlato, per impostazione predefinita il 30% dei case viene riservato per l'utilizzo come set di dati di test. I case rimanenti nell'origine dati specificata vengono utilizzati per eseguire il training del modello. Tuttavia, se si utilizza DMX per creare il modello di data mining, per impostazione predefinita tutti i dati vengono utilizzati per eseguire il training del modello e non viene creato alcun set di testing. Per abilitare la creazione di un set di dati di test, è necessario impostare i parametri della clausola WITH HOLDOUT.  
  
 È possibile determinare se i dati in una particolare struttura di data mining sono stati partizionati in set di training e set di testing visualizzando il valore delle proprietà <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxCases%2A> e <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxPercent%2A>.  
  
> [!NOTE]  
>  È necessario abilitare il drill-through nel modello se si desidera utilizzare le funzioni IsTrainingCase o IsTestCase per restituire i dettagli relativi ai case del modello. Per altre informazioni, vedere [Abilitazione del drill-through per un modello di data mining](/analysis-services/data-mining/enable-drillthrough-for-a-mining-model).  
  
 Per restituire i case che fanno parte del set di dati di test, utilizzare la funzione [IsTestCase &#40;DMX&#41;](../dmx/istestcase-dmx.md).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato il modello di data mining di clustering dello scenario di mailing diretto nell' [esercitazione di base sul data mining](/previous-versions/sql/sql-server-2016/ms167167(v=sql.130)). Nella query vengono restituiti solo i case utilizzati per il training del modello di data mining. Inoltre, i case di training sono limitati ai clienti di età inferiore a 40 anni.  
  
```  
SELECT *  
FROM [TM Clustering].CASES  
WHERE IsTrainingCase()  
AND [Age] <40  
```  
  
 Per altri esempi di come eseguire una query sui case usati in data mining, vedere [selezionare da &#60;modello&#62;. CASI &#40;&#41;DMX ](../dmx/select-from-model-cases-dmx.md) e [selezionare &#60;struttura&#62;. CASI](../dmx/select-from-structure-cases.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Set di dati di training e di testing](/analysis-services/data-mining/training-and-testing-data-sets)   
 [Funzioni &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Query di data mining](/analysis-services/data-mining/data-mining-queries)  
  
