---
description: Levels (MDX)
title: Livelli (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f3b0a7eaea166fdefbfd947faf95b58f74bdb8be
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429873"
---
# <a name="levels-mdx"></a>Levels (MDX)


  Restituisce il livello la cui posizione all'interno di una dimensione o gerarchia è specificata da un'espressione numerica oppure il cui nome è specificato da un'espressione stringa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Numeric expression syntax  
Hierarchy_Expression.Levels( Level_Number )  
  
String expression syntax  
Hierarchy_Expression.Levels( Level_Name )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Hierarchy_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una gerarchia.  
  
 *Level_Number*  
 Espressione numerica valida che specifica il numero di un livello.  
  
 *Level_Name*  
 Espressione stringa valida che specifica il nome di un livello.  
  
## <a name="remarks"></a>Osservazioni  
 Se viene specificato un numero di livello, **la funzione Levels restituisce il livello** associato alla posizione in base zero specificata.  
  
 Se viene specificato un nome di livello, **la funzione Levels restituisce il livello** specificato.  
  
> [!NOTE]  
>  Utilizzare la sintassi delle espressioni stringa per le funzioni definite dall'utente.  
  
## <a name="examples"></a>Esempi  
 Gli esempi seguenti illustrano ogni sintassi della funzione **levels** .  
  
### <a name="numeric"></a>Numeric  
 Nell'esempio seguente viene restituito il livello Country:  
  
```  
SELECT [Geography].[Geography].Levels(1) ON 0  
FROM [Adventure Works]  
```  
  
### <a name="string"></a>string  
 Nell'esempio seguente viene restituito il livello Country:  
  
```  
SELECT [Geography].[Geography].Levels('Country') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento alle funzioni MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
