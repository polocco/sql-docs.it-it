---
title: Aggregazione (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6c75ab71456dc8b7ffc3efdf6bd157693de14881
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "68017175"
---
# <a name="aggregate-mdx"></a>Aggregate (MDX)


  Restituisce un numero che viene calcolato mediante aggregazione sulle celle restituite dall'espressione set. Se non si specifica un'espressione numerica, questa funzione consente di aggregare ogni misura nel contesto di query corrente utilizzando l'operatore di aggregazione predefinito specificato per ogni misura. Se viene specificata un'espressione numerica, questa funzione innanzitutto valuta e quindi somma l'espressione numerica per ogni cella nel set specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Aggregate(Set_Expression [ ,Numeric_Expression ])  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Numeric_Expression*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
## <a name="remarks"></a>Osservazioni  
 Se è specificato un set di tuple vuote o un set vuoto, la funzione restituisce un valore vuoto.  
  
 Nella tabella seguente viene descritto il comportamento della funzione di **aggregazione** con funzioni di aggregazione diverse.  
  
|Operatore di aggregazione|Risultato|  
|--------------------------|------------|  
|SUM|Restituisce la somma dei valori all'interno del set.|  
|Conteggio|Restituisce il conteggio dei valori all'interno del set.|  
|Max|Restituisce il valore massimo all'interno del set.|  
|Min|Restituisce il valore minimo all'interno del set.|  
|Funzioni di aggregazione semiadditive|Restituisce il calcolo delle funzioni semiadditive all'interno del set dopo la proiezione della forma sull'asse dei tempi.|  
|Distinct Count|Aggrega i dati della tabella dei fatti che contribuiscono al sottocubo quando l'asse di sezionamento include un set.<br /><br /> Restituisce la misura Distinct Count per ogni membro del set. Il risultato dipende dalla sicurezza delle celle aggregate e non dalla sicurezza delle celle necessarie per il calcolo. La sicurezza delle celle all'interno del set genera un errore, mentre la sicurezza delle celle al di sotto della granularità del set specificato viene ignorata. I calcoli sul set generano un errore. I calcoli al di sotto della granularità del set vengono ignorati. L'operatore Distinct Count su un set che include un membro e uno o più dei relativi figli restituisce la misura Distinct Count per i fatti che contribuiscono al membro figlio.|  
|Attributi che non possono essere aggregati|Restituisce la somma dei valori.|  
|Funzioni di aggregazione miste|Non supportate. Viene generato un errore.|  
|Operatori unari|Non rispettati. I valori vengono aggregati tramite somma.|  
|Misure calcolate|L'ordine di valutazione viene impostato in modo da garantire l'applicazione della misura calcolata.|  
|Membri calcolati|Vengono applicate le regole normali, ovvero l'ultimo ordine di valutazione ha la precedenza.|  
|Assegnazioni|L'aggregazione delle assegnazioni viene eseguita in base alla funzione di aggregazione delle misure. Se la funzione di aggregazione delle misure è Distinct Count, l'assegnazione viene sommata.|  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituita la somma `Measures.[Order Quantity]` del membro, aggregata nei primi otto mesi dell'anno di calendario 2003 contenuti nella `Date` dimensione, dal cubo **Adventure Works** .  
  
```  
WITH MEMBER [Date].[Calendar].[First8Months2003] AS  
    Aggregate(  
        PeriodsToDate(  
            [Date].[Calendar].[Calendar Year],   
            [Date].[Calendar].[Month].[August 2003]  
        )  
    )  
SELECT   
    [Date].[Calendar].[First8Months2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 Nell'esempio seguente i dati vengono aggregati sui primi due mesi del secondo semestre dell'anno di calendario 2003.  
  
```  
WITH MEMBER [Date].[Calendar].[First2MonthsSecondSemester2003] AS  
    Aggregate(  
        PeriodsToDate(  
            [Date].[Calendar].[Calendar Semester],   
            [Date].[Calendar].[Month].[August 2003]  
        )  
    )  
SELECT   
    [Date].[Calendar].[First2MonthsSecondSemester2003] ON COLUMNS,  
    [Product].[Category].Children ON ROWS  
FROM  
    [Adventure Works]  
WHERE  
    [Measures].[Order Quantity]  
```  
  
 Nell'esempio seguente viene restituito il numero dei rivenditori le cui vendite sono diminuite nel periodo di tempo precedente, in base ai valori del membro State-Province selezionati dall'utente valutati tramite la funzione di aggregazione. Le funzioni **Hierarchize** e **DrilldownLevel** vengono utilizzate per restituire i valori per le vendite in calo per le categorie di prodotti nella dimensione Product.  
  
```  
WITH MEMBER Measures.[Declining Reseller Sales] AS   
   Count(  
      Filter(  
         Existing(Reseller.Reseller.Reseller),   
            [Measures].[Reseller Sales Amount] < ([Measures].[Reseller Sales Amount],  
            [Date].Calendar.PrevMember)  
            )  
         )  
MEMBER [Geography].[State-Province].x AS   
   Aggregate (   
      {[Geography].[State-Province].&[WA]&[US],   
      [Geography].[State-Province].&[OR]&[US] }   
         )  
SELECT NON EMPTY Hierarchize (  
   AddCalculatedMembers (  
      {DrillDownLevel({[Product].[All Products]})}  
         )  
   )  
        DIMENSION PROPERTIES PARENT_UNIQUE_NAME ON COLUMNS   
FROM [Adventure Works]  
WHERE ([Geography].[State-Province].x,   
    [Date].[Calendar].[Calendar Quarter].&[2003]&[4],  
    [Measures].[Declining Reseller Sales])  
```  
  
## <a name="see-also"></a>Vedere anche  
 [PeriodsToDate &#40;&#41;MDX](../mdx/periodstodate-mdx.md)   
 [Elementi figlio &#40;&#41;MDX](../mdx/children-mdx.md)   
 [Hierarchize &#40;&#41;MDX](../mdx/hierarchize-mdx.md)   
 [Conteggio &#40;set&#41; &#40;MDX&#41;](../mdx/count-set-mdx.md)   
 [Filtrare &#40;&#41;MDX](../mdx/filter-mdx.md)   
 [AddCalculatedMembers &#40;&#41;MDX](../mdx/addcalculatedmembers-mdx.md)   
 [DrilldownLevel &#40;&#41;MDX](../mdx/drilldownlevel-mdx.md)   
 [Proprietà &#40;&#41;MDX](../mdx/properties-mdx.md)   
 [PrevMember &#40;&#41;MDX](../mdx/prevmember-mdx.md)   
 [Guida di riferimento alle funzioni MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
