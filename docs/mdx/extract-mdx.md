---
description: Extract (MDX)
title: Estrai (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0b168794a38a515d4ace97d576710041eac86195
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387517"
---
# <a name="extract-mdx"></a>Extract (MDX)


  Restituisce un set di tuple dagli elementi della gerarchia estratti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Extract(Set_Expression, Hierarchy_Expression1 [,Hierarchy_Expression2, ...n] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Hierarchy_Expression1*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una gerarchia.  
  
 *Hierarchy_Expression2*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una gerarchia.  
  
## <a name="remarks"></a>Osservazioni  
 La funzione **Extract** restituisce un set costituito da tuple dagli elementi della gerarchia estratti. Per ogni tupla nel set specificato, i membri delle gerarchie specificate vengono estratti in nuove tuple nel set dei risultati. Questa funzione rimuove sempre le tuple duplicate.  
  
 La funzione **Extract** esegue l'azione opposta della funzione [Crossjoin](../mdx/crossjoin-mdx.md) .  
  
## <a name="examples"></a>Esempi  
 Nella query seguente viene illustrato come utilizzare la funzione **Extract** su un set di Tuple restituito dalla funzione **NonEmpty** :  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `//Returns the distinct combinations of Customer and Date for all purchases`  
  
 `//of Bike Racks or Bike Stands`  
  
 `EXTRACT(`  
  
 `NONEMPTY(`  
  
 `[Customer].[Customer].[Customer].MEMBERS`  
  
 `*`  
  
 `[Date].[Date].[Date].MEMBERS`  
  
 `*`  
  
 `{[Product].[Product Categories].[Subcategory].&[26],[Product].[Product Categories].[Subcategory].&[27]}`  
  
 `*`  
  
 `{[Measures].[Internet Sales Amount]}`  
  
 `)`  
  
 `,  [Customer].[Customer], [Date].[Date])`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento alle funzioni MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
