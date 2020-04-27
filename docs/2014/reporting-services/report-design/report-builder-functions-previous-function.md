---
title: Funzione Previous (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 403a9384-6ca4-42e8-97ca-ac3f6fe4316b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 540bf8367ba32fbebe4e27ee6e2cd3e1aa01ae0d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66105195"
---
# <a name="previous-function-report-builder-and-ssrs"></a>Funzione Previous (Generatore report e SSRS)
  Restituisce il valore o il valore di aggregazione specificato per l'istanza precedente di un elemento all'interno dell'ambito specificato.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Previous(expression, scope)  
```  
  
#### <a name="parameters"></a>Parametri  
 *expression*  
 (`Variant` o `Binary`) Espressione da utilizzare per identificare i dati e per cui recuperare il valore precedente, ad esempio `Fields!Fieldname.Value` o `Sum(Fields!Fieldname.Value)`.  
  
 *ambito*  
 (`String`) Facoltativo. Nome di un gruppo o di un'area dati oppure null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]) che specifica l'ambito da cui recuperare il valore precedente specificato da *Expression*.  
  
## <a name="return-type"></a>Tipo restituito  
 Restituisce un valore `Variant` o `Binary`.  
  
## <a name="remarks"></a>Osservazioni  
 La funzione `Previous` restituisce il valore precedente per l'espressione valutata nell'ambito specificato dopo l'applicazione di tutti i criteri di ordinamento e di filtro.  
  
 Se l' *espressione* non contiene un'aggregazione, `Previous` per impostazione predefinita la funzione viene impostata sull'ambito corrente per l'elemento del report.  
  
 In un gruppo di dettagli utilizzare `Previous` per specificare il valore di un riferimento di campo nell'istanza precedente della riga di dettaglio.  
  
> [!NOTE]  
>  La `Previous` funzione supporta solo i riferimenti ai campi nel gruppo dettagli. Ad esempio, per una casella di testo nel gruppo di dettagli, tramite `=Previous(Fields!Quantity.Value)` vengono restituiti i dati per il campo `Quantity` dalla riga precedente. Nella prima riga tramite questa espressione viene restituito un valore Null (`Nothing` in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]).  
  
 Se *Expression* contiene una funzione di aggregazione che usa un ambito `Previous` predefinito, aggrega i dati all'interno dell'istanza precedente dell'ambito specificato nella chiamata di funzione di aggregazione.  
  
 Se *Expression* contiene una funzione di aggregazione che specifica un ambito diverso da quello predefinito *scope* , il parametro scope `Previous` per la funzione deve essere un ambito contenitore per l'ambito specificato nella chiamata di funzione di aggregazione.  
  
 Le funzioni `Level`, `InScope` `Aggregate` e `Previous` non possono essere usate nel parametro *Expression*. Non è possibile specificare il parametro *recursive* per una funzione di aggregazione.  
  
 Per altre informazioni, vedere [Riferimento a funzioni di aggregazione &#40;Generatore report e SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) e [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="description"></a>Descrizione  
 L'esempio di codice seguente, se inserito nella riga di dati predefinita di un'area dati, fornisce il valore per il campo `LineTotal` nella riga precedente.  
  
### <a name="code"></a>Codice  
  
```  
=Previous(Fields!LineTotal.Value)  
```  
  
### <a name="description"></a>Descrizione  
 Nell'esempio seguente è illustrata un'espressione che calcola la somma delle vendite in un giorno del mese specifico e il valore precedente relativo allo stesso giorno del mese in un anno precedente. L'espressione viene aggiunta a una riga di una cella che appartiene al gruppo figlio `GroupbyDay`. Il gruppo padre è `GroupbyMonth`, che dispone di un gruppo padre `GroupbyYear`. L'espressione visualizza i risultati per GroupbyDay (ambito predefinito), quindi per `GroupbyYear` (elemento padre del gruppo padre `GroupbyMonth`).  
  
 Ad esempio, per un'area dati con un gruppo padre denominato `Year`che ha un gruppo figlio denominato `Month`che a sua volta ha un gruppo figlio denominato `Day` (3 livelli annidati). L'espressione `=Previous(Sum(Fields!Sales.Value,"Day"),"Year")` in una riga associata al gruppo `Day` restituisce il valore delle vendite per lo stesso giorno e mese dell'anno precedente.  
  
### <a name="code"></a>Codice  
  
```  
=Sum(Fields!Sales.Value) & " " & Previous(Sum(Fields!Sales.Value,"GroupbyDay"),"GroupbyYear")  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle espressioni nei report &#40;Generatore report e SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40;Generatore report e SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Tipi di dati nelle espressioni &#40;Generatore report e SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
