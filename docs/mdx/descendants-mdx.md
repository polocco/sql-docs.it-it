---
description: Descendants (MDX)
title: Discendenti (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: b883d1ce73a7259b285748e5a66f283a7d830424
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491440"
---
# <a name="descendants-mdx"></a>Descendants (MDX)


  Restituisce il set di discendenti di un membro al livello o alla distanza specificata, includendo o escludendo facoltativamente i discendenti in altri livelli.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Member expression syntax using a level expression  
Descendants(Member_Expression [ , Level_Expression [ ,Desc_Flag ] ] )  
  
Member expression syntax using a numeric expression  
Descendants(Member_Expression [ , Distance [ ,Desc_Flag ] ] )  
  
Set expression syntax using a level expression  
Descendants(Set_Expression [ , Level_Expression [ ,Desc_Flag ] ] )  
  
Member expression syntax using a numeric expression  
Descendants(Set_Expression [ , Distance [ ,Desc_Flag ] ] )  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Level_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un livello.  
  
 *Distanza*  
 Espressione numerica valida che specifica la distanza dal membro specificato.  
  
 *Desc_Flag*  
 Espressione stringa valida che specifica un flag descrittivo che distingue i possibili set di discendenti.  
  
## <a name="remarks"></a>Osservazioni  
 Se viene specificato un livello, la funzione **Descendants** restituisce un set contenente i discendenti del membro specificato o i membri del set specificato, a un livello specificato, modificato facoltativamente da un flag specificato in *Desc_Flag*.  
  
 Se si specifica *distance* , la funzione **Descendants** restituisce un set contenente i discendenti del membro specificato o i membri del set specificato che corrispondono al numero di livelli specificato nella gerarchia del membro specificato, modificato facoltativamente da un flag specificato in *Desc_Flag*. Questa funzione viene in genere utilizzata con l'argomento Distance per gestire gerarchie incomplete. Se la distanza specificata è zero (0), la funzione restituisce un set costituito soltanto dal membro specificato o dal set specificato.  
  
 Se viene specificata un'espressione set, la funzione **Descendants** viene risolta singolarmente per ogni membro del set e il set viene creato di nuovo. In altre parole, la sintassi utilizzata per la funzione **Descendants** è equivalente dal punto di vista funzionale alla funzione MDX [generate](../mdx/generate-mdx.md) .  
  
 Se non viene specificato alcun livello o distanza, il valore predefinito per il livello utilizzato dalla funzione viene determinato chiamando la funzione [Level](../mdx/level-mdx.md) (<\<Member>>. Livello) per il membro specificato (se viene specificato un membro) o chiamando la funzione **Level** per ogni membro del set specificato (se viene specificato un set). Se non si specifica un'espressione di livello o la distanza o non vengono specificati flag, la funzione viene eseguita come se fosse stata utilizzata la sintassi seguente:  
  
 `Descendants`  
  
 `(`  
  
 `Member_Expression ,`  
  
 `Member_Expression.Level ,`  
  
 `SELF_BEFORE_AFTER`  
  
 `)`  
  
 Se si specifica un livello e non viene specificato un flag descrittivo, la funzione viene eseguita come se fosse stata utilizzata la sintassi seguente:  
  
 `Descendants`  
  
 `(`  
  
 `Member_Expression ,`  
  
 `Level_Expression,`  
  
 `SELF`  
  
 `)`  
  
 Modificando il valore del flag descrittivo è possibile includere o escludere i discendenti alla distanza o al livello specificato, gli elementi figlio prima o dopo la distanza o il livello specificato (fino al nodo foglia) e tutti gli elementi figlio di tipo foglia indipendentemente dalla distanza o dal livello specificato. Nella tabella seguente vengono descritti i flag consentiti nell'argomento *Desc_Flag* .  
  
|Flag|Descrizione|  
|----------|-----------------|  
|SELF|Restituisce soltanto i membri discendenti alla distanza indicata o del livello specificato. La funzione include il membro specificato, se il livello specificato corrisponde al livello di tale membro.|  
|AFTER|Restituisce i membri discendenti di tutti i livelli subordinati alla distanza indicata o al livello specificato.|  
|BEFORE|Restituisce i membri discendenti di tutti i livelli tra il membro specificato e il livello specificato oppure alla distanza indicata. Include il membro specificato, ma non i membri della distanza indicata o del livello specificato.|  
|BEFORE_AND_AFTER|Restituisce i membri discendenti di tutti i livelli subordinati al livello del membro specificato. Include il membro specificato, ma non i membri del livello specificato o alla distanza indicata.|  
|SELF_AND_AFTER|Restituisce i membri discendenti del livello specificato o alla distanza indicata e di tutti i livelli subordinati al livello specificato oppure alla distanza indicata.|  
|SELF_AND_BEFORE|Restituisce i membri discendenti del livello specificato o alla distanza indicata e di tutti i livelli tra il membro specificato e il livello specificato oppure alla distanza indicata, includendo il membro specificato.|  
|SELF_BEFORE_AFTER|Restituisce i membri discendenti di tutti i livelli subordinati al livello del membro specificato, includendo tale membro.|  
|LEAVES|Restituisce i membri discendenti di tipo foglia tra il membro specificato e il livello specificato oppure alla distanza indicata.|  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituiti il membro specificato (Stati Uniti) e i membri tra il membro specificato (Stati Uniti) e i membri del livello che precede il livello specificato (City). Vengono quindi restituiti il membro specificato stesso (Stati Uniti) e i membri del livello State-Province, che precede il livello City. Nell'esempio sono inclusi argomenti impostati come commenti che consentono di testare facilmente altri argomenti per questa funzione.  
  
```  
SELECT Descendants  
   ([Geography].[Geography].[Country].&[United States]  
      //, [Geography].[Geography].[Country]  
   , [Geography].[Geography].[City]  
      //, [Geography].[Geography].Levels (3)  
      //, SELF   
      //, AFTER  
      , BEFORE  
      // BEFORE_AND_AFTER  
      //, SELF_AND_AFTER  
      //, SELF_AND_BEFORE  
      //,SELF_BEFORE_AFTER  
      //,LEAVES   
   ) ON 0  
FROM [Adventure Works]   
```  
  
 Nell'esempio seguente viene restituita la media giornaliera della `Measures.[Gross Profit Margin]` misura, calcolata nei giorni di ogni mese dell'anno fiscale 2003, dal cubo **Adventure Works** . La funzione **Descendants** restituisce un set di giorni determinato dal membro corrente della `[Date].[Fiscal]` gerarchia.  
  
```  
WITH MEMBER Measures.[Avg Gross Profit Margin] AS Avg  
   (  
      Descendants( [Date].[Fiscal].CurrentMember,   
           [Date].[Fiscal].[Date]  
          ),   
        Measures.[Gross Profit Margin]  
   )  
SELECT  
   Measures.[Avg Gross Profit Margin] ON COLUMNS,  
   [Date].[Fiscal].[Month].Members ON ROWS  
FROM [Adventure Works]  
WHERE ([Date].[Fiscal Year].&[2003])  
```  
  
 Nell'esempio seguente viene utilizzata un'espressione di livello e vengono restituiti l'importo delle vendite su Internet per ogni State-Province in Australia e la percentuale sul totale delle vendite su Internet per l'Australia per ogni State-Province. In questo esempio viene utilizzata la funzione Item per estrarre la prima e unica tupla dal set restituito dalla funzione **predecessori** .  
  
```  
WITH MEMBER Measures.x AS   
   [Measures].[Internet Sales Amount] /   
   ( [Measures].[Internet Sales Amount],  
      Ancestors   
         ( [Customer].[Customer Geography].CurrentMember,   
           [Customer].[Customer Geography].[Country]  
         ).Item (0)  
   ), FORMAT_STRING = '0%'  
SELECT {[Measures].[Internet Sales Amount], Measures.x} ON 0,  
{Descendants   
   ( [Customer].[Customer Geography].[Country].&[Australia],   
     [Customer].[Customer Geography].[State-Province], SELF   
   )    
} ON 1  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento alle funzioni MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
