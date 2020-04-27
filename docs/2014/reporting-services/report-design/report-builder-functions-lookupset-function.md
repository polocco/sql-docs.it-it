---
title: Funzione LookupSet (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7685acfd-1c8d-420c-993c-903236fbe1ff
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5f24c78e82d437ab7e2147122c5065f0b7274d5e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66105225"
---
# <a name="lookupset-function-report-builder-and-ssrs"></a>Funzione LookupSet (Generatore report e SSRS)
  Viene restituito il set di valori corrispondenti per il nome specificato da un set di dati contenente coppie nome/valore.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
LookupSet(source_expression, destination_expression, result_expression, dataset)  
```  
  
#### <a name="parameters"></a>Parametri  
 *source_expression*  
 (`Variant`) Espressione valutata nell'ambito corrente che specifica il nome o la chiave da ricercare, Ad esempio: `=Fields!ID.Value`.  
  
 *destination_expression*  
 (`Variant`) Espressione valutata per ogni riga in un set di dati che specifica il nome o la chiave con cui eseguire la corrispondenza, Ad esempio: `=Fields!CustomerID.Value`.  
  
 *result_expression*  
 (`Variant`) Espressione valutata per la riga nel set di dati in cui *source_expression* = *destination_expression*e che specifica il valore da recuperare. Ad esempio: `=Fields!PhoneNumber.Value`.  
  
 *set di dati*  
 Costante che specifica il nome di un set di dati nel report, ad esempio "InformazioniDiContatto".  
  
## <a name="return"></a>Return  
 Restituisce `VariantArray` o `Nothing` se non viene rilevata alcuna corrispondenza.  
  
## <a name="remarks"></a>Osservazioni  
 Usare la funzione `LookupSet` per recuperare un set di valori dal set di dati specificato per una coppia nome/valore in cui è presente una relazione uno-a-molti. Per un identificatore di cliente in una tabella, ad esempio, è possibile usare la funzione `LookupSet` per recuperare tutti i numeri di telefono relativi al cliente da un set di dati non associato all'area dati.  
  
 Tramite la funzione `LookupSet` vengono effettuate le operazioni seguenti:  
  
-   Valuta l'espressione di origine nell'ambito corrente.  
  
-   Valuta l'espressione di destinazione per ogni riga del set di dati specificato dopo che sono stati applicati i filtri, in base alle regole di confronto del set di dati specificato.  
  
-   Per ogni corrispondenza dell'espressione di origine e di destinazione, valuta l'espressione di risultato per quella riga nel set di dati.  
  
-   Restituisce il set di valori dell'espressione di risultato.  
  
 Per recuperare un singolo valore da un set di dati con coppie nome/valore per un nome specificato in cui è presente una relazione uno-a-uno, usare la [Funzione Lookup &#40;Generatore report e SSRS&#41;](report-builder-functions-lookup-function.md). Per chiamare `Lookup` un set di valori, usare la [funzione multilookup &#40;Generatore report e SSRS&#41;](report-builder-functions-multilookup-function.md).  
  
 Si applicano le restrizioni seguenti:  
  
-   La funzione `LookupSet` viene valutata dopo l'applicazione di tutte le espressioni di filtro.  
  
-   È supportato solo un livello di ricerca. Un'espressione di origine, destinazione o risultato non può includere un riferimento a una funzione di ricerca.  
  
-   Le espressioni di origine e di destinazione devono restituire lo stesso tipo di dati.  
  
-   Le espressioni di origine, di destinazione e di risultato non possono includere riferimenti a variabili di report o di gruppo.  
  
-   La funzione `LookupSet` non può essere utilizzata come espressione per gli elementi del report seguenti:  
  
    -   Stringhe di connessione dinamiche per un'origine dati.  
  
    -   Campi calcolati in un set di dati.  
  
    -   Parametri di query in un set di dati.  
  
    -   Filtri in un set di dati.  
  
    -   Parametri di report.  
  
    -   Proprietà Report.Language.  
  
 Per altre informazioni, vedere [Riferimento a funzioni di aggregazione &#40;Generatore report e SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) e [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente, si supponga che la tabella sia associata a un set di dati che include un identificatore del territorio di vendita TerritoryGroupID. Un set di dati separato denominato "Stores" contiene l'elenco di tutti i negozi di un territorio e include l'ID dell'identificatore del territorio e il nome del negozio StoreName.  
  
 Nell'espressione seguente, `LookupSet` confronta il valore TerritoryGroupID con ID per ogni riga nel set di dati denominato "Stores". Per ogni corrispondenza, il valore del campo StoreName per quella riga viene aggiunto al set di risultati.  
  
```  
=LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores")  
```  
  
## <a name="example"></a>Esempio  
 Poiché tramite `LookupSet` viene restituita una raccolta di oggetti, non è possibile visualizzare direttamente l'espressione di risultato in una casella di testo. È possibile concatenare il valore di ogni oggetto nella raccolta come stringa.  
  
 Usare la funzione `Join` di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] per creare una stringa delimitata da un set di oggetti. Usare una virgola come separatore per combinare gli oggetti in un'unica riga. In alcuni renderer, è possibile usare un avanzamento riga di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] (`vbCrLF`) come separatore per elencare ogni valore su una nuova riga.  
  
 L'espressione seguente, quando viene usata come proprietà Value per una casella di testo, USA `Join` per creare un elenco.  
  
```  
=Join(LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores"),",")  
```  
  
## <a name="example"></a>Esempio  
 Per caselle di testo che eseguono il rendering solo poche volte, è possibile scegliere di aggiungere un codice personalizzato per generare HTML per visualizzare i valori in una casella di testo. HTML in una casella di testo richiede altri processi di elaborazione, pertanto non è consigliabile per una casella di testo che viene sottoposta a rendering molte volte.  
  
 Copiare le seguenti funzioni di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] in un blocco di codice di una definizione del report. **MakeList** accetta la matrice di oggetti restituita in *result_expression* e compila un elenco non ordinato usando tag HTML. **Length** restituisce il numero di elementi della matrice di oggetti.  
  
```  
Function MakeList(ByVal items As Object()) As String  
   If items Is Nothing Then  
      Return Nothing  
   End If  
  
   Dim builder As System.Text.StringBuilder =   
      New System.Text.StringBuilder()  
   builder.Append("<ul>")  
  
   For Each item As Object In items  
      builder.Append("<li>")  
      builder.Append(item)  
   Next  
   builder.Append("</ul>")  
  
   Return builder.ToString()  
End Function  
  
Function Length(ByVal items as Object()) as Integer  
   If items is Nothing Then  
      Return 0  
   End If  
   Return items.Length  
End Function  
```  
  
## <a name="example"></a>Esempio  
 Per generare HTML, è necessario chiamare la funzione. Incollare l'espressione seguente nella proprietà Value per la casella di testo e impostare il tipo di markup per il testo su HTML. Per altre informazioni, vedere [Aggiungere codice HTML a un report &#40;Generatore report e SSRS&#41;](add-html-into-a-report-report-builder-and-ssrs.md).  
  
```  
=Code.MakeList(LookupSet(Fields!TerritoryGroupID.Value, Fields!ID.Value, Fields!StoreName.Value, "Stores"))  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle espressioni nei report &#40;Generatore report e SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40;Generatore report e SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Tipi di dati nelle espressioni &#40;Generatore report e SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
