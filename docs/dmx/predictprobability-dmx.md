---
title: PredictProbability (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e2933700c24e34748d2c0d6593d5f34eb8e69bc2
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2020
ms.locfileid: "86970839"
---
# <a name="predictprobability-dmx"></a>PredictProbability (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Viene restituita la probabilità per uno stato specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
PredictProbability(<scalar column reference>, [<predicted state>])  
```  
  
## <a name="applies-to"></a>Si applica a  
 Colonna scalare.  
  
## <a name="return-type"></a>Tipo restituito  
 Valore scalare.  
  
## <a name="remarks"></a>Osservazioni  
 Se lo stato stimato viene omesso, verrà utilizzato lo stato con la probabilità più alta, escludendo il bucket degli stati mancanti. Per includere il bucket degli stati mancanti, impostare \<predicted state> su **INCLUDE_NULL**. Per restituire la probabilità per gli stati mancanti, impostare \<predicted state> su null.  
  
> [!NOTE]  
>  Alcuni modelli di data mining non forniscono i valori di probabilità e pertanto non possono utilizzare questa funzione. Inoltre, i valori di probabilità per un valore di destinazione specifico vengono calcolati in modo diverso o potrebbero essere interpretati in modo diverso a seconda del tipo di modello su cui si esegue la query. Per ulteriori informazioni sul modo in cui viene calcolata la probabilità per un particolare tipo di modello, vedere l'argomento singolo algoritmo nel [contenuto dei modelli di data mining &#40;Analysis Services-Data mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/mining-model-content-analysis-services-data-mining).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato un natural prediction join per determinare la probabilità che un individuo sia un acquirente di biciclette sulla base del modello di data mining TM Decision Tree e la probabilità per la stima. In questo esempio sono presenti due funzioni PredictProbability, una per ogni valore possibile. Se si omette questo argomento, la funzione restituisce la probabilità per il valore più probabile.  
  
```  
SELECT  
  [Bike Buyer],  
  PredictProbability([Bike Buyer], 1) AS [Bike Buyer = Yes],  
  PredictProbability([Bike Buyer], 0) AS [Bike Buyer = No]  
FROM [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
 Risultati dell'esempio:  
  
|Bike Buyer|Bike Buyer = Yes|Bike Buyer = No|  
|----------------|-----------------------|----------------------|  
|1|0.867074195848097|0.132755556974282|  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento alle funzioni DMX&#41; &#40;di Data Mining Extensions](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Funzioni &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [Funzioni di stima generali &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
