---
title: IS (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: aaf4151d8291ccd4249892c6ef8fce8a3d280f6b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "67905986"
---
# <a name="is-mdx"></a>IS (MDX)


  Esegue un confronto logico tra due espressioni di oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Expression1 IS ( Expression2 | NULL )  
```  
  
#### <a name="parameters"></a>Parametri  
 *Expression1*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un riferimento a un oggetto MDX.  
  
 *Expression2*  
 Espressione MDX valida che restituisce un riferimento a un oggetto MDX.  
  
## <a name="return-value"></a>Valore restituito  
 Valore booleano che restituisce **true** se entrambi gli argomenti fanno riferimento allo stesso oggetto. in caso contrario, **false**. Se viene specificata la parola chiave **null** , l'operatore restituisce **true** se *expression1* è **null**. in caso contrario, **false**.  
  
## <a name="remarks"></a>Osservazioni  
 L'operatore **is** viene spesso usato per determinare se le tuple e i membri sono idempotente, vale a dire che sono esattamente equivalenti.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato come utilizzare l'operatore **is** per verificare se il membro corrente su un asse è un membro specifico:  
  
 `With`  
  
 `//Returns TRUE if the currentmember is Bikes`  
  
 `Member [Measures].[IsBikes?] AS`  
  
 `[Product].[Category].CurrentMember IS [Product].[Category].&[1]`  
  
 `SELECT`  
  
 `{[Measures].[IsBikes?]} ON 0,`  
  
 `[Product].[Category].[Category].Members ON 1`  
  
 `FROM`  
  
 `[Adventure Works]`  
  
## <a name="see-also"></a>Vedi anche  
 [Guida di riferimento agli operatori MDX &#40;&#41;MDX](../mdx/mdx-operator-reference-mdx.md)  
  
  
