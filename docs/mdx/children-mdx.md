---
title: Elementi figlio (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0af4d7b97777002dc5683c075f82531ccc8df86e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "68016801"
---
# <a name="children-mdx"></a>Children (MDX)


  Restituisce il set di membri figlio di un membro specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Member_Expression.Children  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Osservazioni  
 La funzione **Children** restituisce un set ordinato in modo naturale che contiene gli elementi figlio di un membro specificato. Se non esistono membri figlio del membro specificato, la funzione restituisce un set vuoto.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono restituiti i figli del membro Stati Uniti della gerarchia Geography nella dimensione Geography.  
  
```  
SELECT [Geography].[Geography].[Country].&[United States].Children ON 0  
FROM [Adventure Works]  
```  
  
 Nell'esempio seguente vengono restituiti tutti i membri della dimensione **measures** sull'asse delle colonne, inclusi tutti i membri calcolati e il set di tutti gli `[Product].[Model Name]` elementi figlio della gerarchia dell'attributo sull'asse delle righe dal cubo **Adventure Works** .  
  
```  
SELECT  
    Measures.AllMembers ON COLUMNS,  
    [Product].[Model Name].Children ON ROWS  
FROM  
    [Adventure Works]  
  
```  
  
|Versione|Cronologia|  
|-------------|-------------|  
|[!INCLUDE[ssBOL2005_R03](../includes/ssbol2005-r03-md.md)]|**Contenuto modificato:**<br /> -Argomenti e sintassi aggiornati per migliorare la chiarezza.<br /><br /> -Sono stati aggiunti esempi aggiornati.|  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento alle funzioni MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
