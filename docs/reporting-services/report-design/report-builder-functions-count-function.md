---
title: Funzione Count (Generatore report) | Microsoft Docs
description: Informazioni sulla funzione Count, che restituisce il conteggio dei valori non Null specificati da un'espressione, che viene valutata nel contesto dell'ambito specificato.
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 7b50b101-daf8-4fb0-ae04-57384755779f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3e0213d580935112e48df2f8a774ac49202ee7af
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85044088"
---
# <a name="report-builder-functions---count-function"></a>Funzioni di Generatore report - Funzione Count
  Restituisce il conteggio dei valori non Null specificati dall'espressione, valutato nel contesto dell'ambito specificato.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Count(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a>Parametri  
 *expression*  
 (**Variant** o **Binary**) Espressione su cui eseguire l'aggregazione, ad esempio `=Fields!FieldName.Value`.  
  
 *ambito*  
 (**Stringa**) Nome di un set di dati, gruppo o area dati che contiene gli elementi del report a cui applicare la funzione di aggregazione. Se si omette *scope* , viene usato l'ambito corrente.  
  
 *ricorsivi*  
 (**Enumerated Type**) Facoltativo. **Simple** (impostazione predefinita) o **RdlRecursive**. Specifica se eseguire l'aggregazione in modo ricorsivo.  
  
## <a name="return-type"></a>Tipo restituito  
 Restituisce un valore **Integer**.  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di *scope* deve essere una costante di tipo stringa e non può essere un'espressione. Per aggregazioni o aggregazioni esterne che non specificano altre aggregazioni, *scope* deve fare riferimento all'ambito corrente o a un ambito contenitore. Per le aggregazioni di aggregazioni, le aggregazioni nidificate possono specificare un ambito figlio.  
  
 *Expression* può contenere chiamate alle funzioni di aggregazione nidificate con le eccezioni e le condizioni seguenti:  
  
-   *Scope* per le aggregazioni nidificate deve corrispondere o essere contenuto nell'ambito dell'aggregazione esterna. Per tutti gli ambiti distinti nell'espressione, un ambito deve essere in una relazione figlio con tutti gli altri ambiti.  
  
-   *Scope* per le aggregazioni nidificate non può essere il nome di un set di dati.  
  
-   *Expression* non deve contenere funzioni **First**, **Last**, **Previous**o **RunningValue** .  
  
-   *Expression* non deve contenere aggregazioni nidificate che specificano *recursive*.  
  
 Per altre informazioni, vedere [Riferimento a funzioni di aggregazione &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md) e [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Per altre informazioni sulle aggregazioni ricorsive, vedere [Creazione di gruppi di gerarchie ricorsive &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
 Esempio  
  
## <a name="description"></a>Descrizione  
 Nell'esempio di codice seguente è illustrata un'espressione che calcola il numero di valori non Null di `Size` per l'ambito predefinito e per un ambito di gruppo padre. L'espressione viene aggiunta a una riga di una cella che appartiene al gruppo figlio `GroupbySubcategory`. Il gruppo padre è `GroupbyCategory`. L'espressione visualizza i risultati per `GroupbySubcategory` (ambito predefinito) e quindi per `GroupbyCategory` (ambito del gruppo padre).  
  
> [!NOTE]  
>  Le espressioni non devono contenere ritorni a capo e interruzioni di riga, che sono inclusi nell'esempio per supportare i renderer della documentazione. Se si copia l'esempio seguente, rimuovere i ritorni a capo da ogni riga.  
  
## <a name="code"></a>Codice  
  
```  
="Count (Subcategory): " & Count(Fields!Size.Value) &   
"Count (Category): " & Count(Fields!Size.Value,"GroupbyCategory")  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle espressioni nei report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Tipi di dati nelle espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
