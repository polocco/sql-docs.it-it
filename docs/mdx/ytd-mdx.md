---
title: YTD (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2e3fcd823dea5d651cd7be9295fa4c6bba25380c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "68125757"
---
# <a name="ytd-mdx"></a>Ytd (MDX)


  Restituisce un set di membri di pari livello dallo stesso livello di un membro specificato, a partire dal primo elemento di pari livello e terminando con il membro dato, in base a quanto vincolato dal livello *anno* nella dimensione temporale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Ytd( [ Member_Expression ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Osservazioni  
 Se non viene specificata un'espressione di membro, l'impostazione predefinita è il membro corrente della prima gerarchia con un livello di tipo *years* nella prima dimensione di tipo *Time* del gruppo di misure.  
  
 La funzione **YTD** è una funzione di collegamento per la funzione [PeriodsToDate](../mdx/periodstodate-mdx.md) in cui la proprietà Type della gerarchia dell'attributo su cui si basa il livello è impostata su *years*. In altre parole, `Ytd(Member_Expression)` equivale a `PeriodsToDate(Year_Level_Expression,Member_Expression)`. Si noti che questa funzione non funzionerà quando la proprietà Type è impostata su *FiscalYears*.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituita la somma `Measures.[Order Quantity]` del membro, aggregata nei primi otto mesi dell'anno di calendario 2003 contenuti nella `Date` dimensione, dal cubo **Adventure Works** .  
  
```  
WITH MEMBER [Date].[Calendar].[First8MonthsCY2003] AS  
    Aggregate(  
        YTD([Date].[Calendar].[Month].[August 2003])  
    )  
SELECT   
    [Date].[Calendar].[First8MonthsCY2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 **YTD** viene spesso utilizzato in combinazione con nessun parametro specificato, ovvero la funzione [CurrentMember &#40;MDX&#41;](../mdx/currentmember-mdx.md) visualizzerà un totale cumulativo in esecuzione da anno a data in un report, come illustrato nella query seguente:  
  
 `WITH MEMBER MEASURES.YTDDEMO AS`  
  
 `AGGREGATE(YTD(), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount], MEASURES.YTDDEMO} ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento alle funzioni MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
