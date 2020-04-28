---
title: Istruzione CASE (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 756300f1efc93e47a7af3913b34d9318cbe5e559
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "68016830"
---
# <a name="case-statement-mdx"></a>Istruzione CASE (MDX)


  Consente di restituire valori specifici da più confronti in base a condizioni specifiche. Esistono due tipi di istruzioni CASE:  
  
-   Un'istruzione CASE semplice che esegue un confronto tra un'espressione e un set di espressioni semplici per restituire valori specifici.  
  
-   Un'istruzione CASE avanzata che valuta un set di espressioni booleane per restituire valori specifici.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Simple Case Statement  
CASE [input_expression]  
WHEN when_expression THEN when_true_result_expression  
[...n]  
[ELSE else_result_expression]  
END  
  
Search Case Statement  
CASE   
WHEN Boolean_expression THEN when_true_result_expression  
[...n]  
[ELSE else_result_expression]  
END  
```  
  
## <a name="arguments"></a>Argomenti  
 *input_expression*  
 Espressione MDX (Multidimensional Expression) che viene risolta in valore scalare.  
  
 *when_expression*  
 Valore scalare specificato rispetto al quale viene valutata la *input_expression* , che, quando viene valutata true, restituisce il valore scalare del *else_result_expression*.  
  
 *when_true_result_expression*  
 Valore scalare restituito quando la clausola WHEN restituisce true.  
  
 *else_result_expression*  
 Valore scalare restituito quando nessuna delle clausole WHEN restituisce true.  
  
 *Boolean_expression*  
 Espressione MDX che restituisce un valore scalare.  
  
## <a name="remarks"></a>Osservazioni  
 Se non ci sono clausole ELSE e tutte le clausole WHEN restituiscono False, il risultato sarà una cella vuota.  
  
## <a name="simple-case-expression"></a>Espressione CASE semplice  
 MDX valuta una semplice espressione case risolvendo il *input_expression* in un valore scalare. Questo valore scalare viene quindi confrontato con il valore scalare del *when_expression*. Se i due valori scalari corrispondono, l'istruzione CASE restituisce il valore della *when_true_expression*. Se i due valori scalari non corrispondono, viene valutata la clausola WHEN successiva. Se tutte le clausole WHEN restituiscono false, viene restituito il valore di *else_result_expression* dalla clausola else.  
  
 Nell'esempio seguente, la misura Reseller Order Count viene valutata in base a diverse clausole WHEN e restituisce un risultato basato sul valore della misura Reseller Order Count per ogni anno. Per i valori dei conteggi degli ordini dei rivenditori che non corrispondono a un valore scalare specificato in un *when_expression* in una clausola When, viene restituito il valore scalare del *else_result_expression* .  
  
```  
WITH MEMBER [Measures].x AS   
CASE [Measures].[Reseller Order Count]  
   WHEN 0 THEN 'NONE'  
   WHEN 1 THEN 'SMALL'  
   WHEN 2 THEN 'SMALL'  
   WHEN 3 THEN 'MEDIUM'  
   WHEN 4 THEN 'MEDIUM'  
   WHEN 5 THEN 'LARGE'  
   WHEN 6 THEN 'LARGE'  
      ELSE 'VERY LARGE'  
END  
SELECT Calendar.[Calendar Year] on 0  
, NON EMPTY [Geography].[Postal Code].Members ON 1  
FROM [Adventure Works]  
WHERE [Measures].x  
```  
  
## <a name="searched-case-expression"></a>Espressione CASE avanzata  
 Per utilizzare l'espressione CASE per eseguire valutazioni più complesse, utilizzare l'espressione CASE avanzata. Questa variante dell'espressione di ricerca consente di valutare se un'espressione di input è compresa in un intervallo di valori. Nel linguaggio MDX le clausole WHEN vengono valutate nell'ordine in cui si presentano nell'istruzione CASE.  
  
 Nell'esempio seguente, la misura Reseller Order Count viene valutata in base al *Boolean_expression* specificato per ognuna delle diverse clausole When. Viene restituito un risultato basato sul valore della misura Reseller Order Count per ogni anno. Poiché le clausole WHEN sono valutate nell'ordine in cui vengono visualizzate, è possibile assegnare a tutti i valori superiori a 6 il valore "VERY LARGE" senza dover specificare ogni valore in modo esplicito. Per i valori dei conteggi degli ordini dei rivenditori non specificati in una clausola WHEN, viene restituito il valore scalare del *else_result_expression* .  
  
```  
WITH MEMBER [Measures].x AS   
CASE   
   WHEN [Measures].[Reseller Order Count] > 6 THEN 'VERY LARGE'  
   WHEN [Measures].[Reseller Order Count] > 4 THEN 'LARGE'  
   WHEN [Measures].[Reseller Order Count] > 2 THEN 'MEDIUM'  
   WHEN [Measures].[Reseller Order Count] > 0 THEN 'SMALL'  
   ELSE "NONE"  
END  
SELECT Calendar.[Calendar Year] on 0,  
NON EMPTY [Geography].[Postal Code].Members on 1  
FROM [Adventure Works]  
WHERE [Measures].x  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni di scripting MDX &#40;MDX&#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
