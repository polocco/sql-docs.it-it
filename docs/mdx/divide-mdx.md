---
title: Divisione (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6184aa9d932355cd935a9131848ec27895faea5f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "68049303"
---
# <a name="divide-mdx"></a>Divisione (MDX)


  Esegue una divisione e restituisce il risultato alternativo o BLANK() della divisione per 0.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Divide (<numerator>, <denominator> [,<alternateresult>])  
```  
  
## <a name="arguments"></a>Argomenti  
 *numeratore*  
 Dividendo o numero da dividere.  
  
 *denominatore*  
 Divisore o numero per cui dividere.  
  
 *alternateresult*  
 (Facoltativo) Il valore restituito se la divisione per zero genera un errore. Se non viene fornito, il valore predefinito è BLANK().  
  
## <a name="remarks"></a>Osservazioni  
 Il risultato alternativo nelle divisione per 0 deve essere una costante.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento alle funzioni MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
