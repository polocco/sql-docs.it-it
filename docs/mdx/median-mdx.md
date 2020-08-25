---
title: Mediana (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b6f941e269bb9948dd39ba52db0ea4d0961c029a
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/25/2020
ms.locfileid: "68033849"
---
# <a name="median-mdx"></a>Median (MDX)


  Restituisce la mediana di un'espressione numerica valutata su un set.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Median(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Numeric_Expression*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
## <a name="remarks"></a>Commenti  
 Se si specifica un'espressione numerica, questa viene valutata sull'intero set e restituisce il valore mediano di tale valutazione. Se non viene specificata un'espressione numerica, il set specificato viene valutato nel contesto corrente dei membri del set e viene restituito il valore mediano di tale valutazione.  
  
 Il valore mediano è il valore centrale di un set di numeri ordinati ed è diverso dal valore medio. Mentre il valore medio corrisponde alla somma di un set di numeri divisa per il conteggio dei numeri del set, il valore mediano corrisponde al valore più piccolo rispetto ad almeno metà dei valori del set. Se il numero di valori del set è dispari, il valore mediano corrisponde a un singolo valore. Se invece il numero di valori del set è pari, corrisponde alla somma dei due valori centrali divisa per due.  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ignora i valori Null durante il calcolo del valore medio di un set di numeri ordinati.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituito il valore mediano mensile delle vendite per ogni trimestre, sottocategoria e paese del cubo Adventure Works.  
  
```  
WITH MEMBER Measures.x AS Median   
   ([Date].[Calendar].CurrentMember.Children  
      , [Measures].[Reseller Order Quantity]  
   )  
SELECT Measures.x ON 0  
,NON EMPTY [Date].[Calendar].[Calendar Quarter]*   
   [Product].[Product Categories].[Subcategory].members *  
   [Geography].[Geography].[Country].Members  
ON 1  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento alle funzioni MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
