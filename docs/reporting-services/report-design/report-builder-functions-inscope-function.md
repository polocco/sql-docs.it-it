---
title: Funzione InScope (Generatore report) | Microsoft Docs
description: La funzione InScope indica se l'istanza corrente di un elemento è inclusa nell'ambito specificato in Generatore report.
ms.date: 03/08/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: a8cd209a-e5d3-4dce-ab2d-f271f6c54955
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 27d97226f0f81b89c5289fa94a4524205aa60f64
ms.sourcegitcommit: 5c7634b007f6808c87094174b80376cb20545d5f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84886528"
---
# <a name="report-builder-functions---inscope-function"></a>Funzioni di Generatore report - Funzione InScope
  Indica se l'istanza corrente di un elemento è inclusa nell'ambito specificato.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Sintassi  
  
```  
InScope(scope)  
```  
  
#### <a name="parameters"></a>Parametri  
 *ambito*  
 (**String**) Nome di un set di dati, area dati o gruppo che specifica un ambito.  
  
## <a name="return-type"></a>Tipo restituito  
 Viene restituito un valore **Boolean**.  
  
## <a name="remarks"></a>Osservazioni  
 La funzione **InScope** testa l'ambito dell'istanza corrente di un elemento del report per verificare l'appartenenza all'ambito specificato dal parametro *scope*.  
  
 *Scope* non può essere un'espressione.  
  
 La funzione **InScope** viene tipicamente usata nelle aree dati con ambito dinamico. È ad esempio possibile usare **InScope** in un collegamento drill-through nelle celle di un'area dati per specificare un nome di report diverso e set di parametri diversi a seconda della cella su cui si fa clic. Di seguito viene riportato un esempio:  
  
-   L'espressione seguente, usata come nome del report in un collegamento drill-through, apre il report `ProductDetail` se la cella su cui si fa clic si trova nel gruppo `Month` e il report `ProductSummary` in caso contrario.  
  
    ```  
    =Iif(InScope("Month"), "ProductDetail", "ProductSummary")  
    ```  
  
-   L'espressione seguente, usata nella proprietà **Omit** di un parametro di report drill-through, passerà il parametro al report di destinazione solo se la cella su cui si fa clic si trova nel gruppo `Product` .  
  
    ```  
    =Not(InScope("Product"))  
    ```  
  
 Per altre informazioni, vedere [Riferimento a funzioni di aggregazione &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md) e [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="example"></a>Esempio  
 Il codice di esempio seguente indica se l'istanza corrente dell'elemento si trova nell'ambito del set di dati, area dati o gruppo `Product` .  
  
```  
=InScope("Product")  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle espressioni nei report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Tipi di dati nelle espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
