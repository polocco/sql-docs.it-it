---
title: Istruzione DROP SET (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f4e31a687597e454b9afe38d6c6dd1c15af486d0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "68893720"
---
# <a name="mdx-data-definition---drop-set"></a>Definizione dei dati MDX - DROP SET


  Rimuove un set denominato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP [SESSION] SET   
   <Cube_Reference>.Set_Name   
               [,<Cube_Reference>.Set_Name ...n]  
  
<Cube_Reference> ::= {CURRENTCUBE | Cube_Name}  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *Cube_Name*  
 Espressione stringa valida che specifica il nome del cubo.  
  
 *Set_Name*  
 Espressione stringa valida che specifica il nome del set denominato da eliminare.  
  
## <a name="remarks"></a>Osservazioni  
 Per altre informazioni sui set denominati, vedere [Compilazione di set denominati in MDX &#40;MDX&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-named-sets-building-named-sets).  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni MDX per la definizione dei dati &#40;&#41;MDX](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
