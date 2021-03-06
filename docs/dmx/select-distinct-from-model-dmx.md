---
description: Selezionare DISTINCT FROM &lt; Model &gt; (DMX)
title: Selezionare DISTINCT FROM &lt; Model &gt; (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: caefcdc2e081c0e8d0e7bee329d4dc5d4d5cfa22
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/05/2020
ms.locfileid: "91727652"
---
# <a name="select-distinct-from-ltmodel-gt-dmx"></a>Selezionare DISTINCT FROM &lt; Model &gt; (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Restituisce tutti gli stati possibili della colonna selezionata nel modello. I valori restituiti variano a seconda che la colonna specificata contenga valori discreti, valori numerici discretizzati o valori numerici continui.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SELECT [FLATTENED] DISTINCT [TOP <n>] <expression list> FROM <model>   
[WHERE <condition list>][ORDER BY <expression>]  
```  
  
## <a name="arguments"></a>Argomenti  
 *n*  
 Facoltativo. Valore intero che specifica il numero di righe da restituire.  
  
 *elenco di espressioni*  
 Elenco delimitato da virgole contenente espressioni o identificatori di colonne correlate (derivati dal modello).  
  
 *model*  
 Identificatore del modello.  
  
 *Elenco condizioni*  
 Condizione per limitare i valori restituiti dall'elenco di colonne.  
  
 *expression*  
 Facoltativo. Espressione che restituisce un valore scalare.  
  
## <a name="remarks"></a>Osservazioni  
 L'istruzione **SELECT DISTINCT from** funziona solo con una singola colonna o con un set di colonne correlate. Non è possibile utilizzare questa clausola con un set di colonne non correlate.  
  
 L'istruzione **SELECT DISTINCT from** consente di fare riferimento direttamente a una colonna all'interno di una tabella nidificata. Ad esempio:  
  
```  
<model>.<table column reference>.<column reference>  
```  
  
 I risultati dell'istruzione **SELECT DISTINCT FROM \<model> ** variano a seconda del tipo di colonna. Nella tabella seguente sono descritti i tipi di colonna supportati e l'output dell'istruzione.  
  
|Tipo di colonna|Output|  
|-----------------|------------|  
|Discrete|Valori univoci nella colonna.|  
|Discretizzato|Punto medio di ogni bucket discretizzato nella colonna.|  
|Continua|Punto medio dei valori nella colonna.|  
  
## <a name="discrete-column-example"></a>Esempio con una colonna discreta  
 L'esempio di codice seguente si basa sul `[TM Decision Tree]` modello creato nell' [esercitazione di base sul data mining](/previous-versions/sql/sql-server-2016/ms167167(v=sql.130)). La query restituisce i valori univoci presenti nella colonna discreta `Gender`.  
  
```  
SELECT DISTINCT [Gender]  
FROM [TM Decision Tree]  
```  
  
 Risultati dell'esempio:  
  
|Sesso|  
|------------|  
||  
|F|  
|M|  
  
 Per le colonne che contengono valori discreti, i risultati includono sempre lo stato Missing, mostrato come valore null.  
  
## <a name="continuous-column-example"></a>Esempio con una colonna continua  
 L'esempio di codice seguente restituisce il punto medio e l'età massima e minima per tutti i valori nella colonna.  
  
```  
SELECT DISTINCT [Age] AS [Midpoint Age],   
    RangeMin([Age]) AS [Minimum Age],   
    RangeMax([Age]) AS [Maximum Age]  
FROM [TM Decision Tree]  
```  
  
 Risultati dell'esempio:  
  
|Midpoint Age|Minimum Age|Maximum Age|  
|------------------|-----------------|-----------------|  
||||  
|62|26|97|  
  
 La query restituisce inoltre una singola riga di valori null per rappresentare valori mancanti.  
  
## <a name="discretized-column-example"></a>Esempio con una colonna discretizzata  
 L'esempio di codice seguente restituisce i valori medio, massimo e minimo per ogni bucket creato dall'algoritmo per la colonna [`Yearly Income]`. Per riprodurre i risultati per questo esempio è necessario creare una nuova struttura di data mining che corrisponde a `[Targeted Mailing]`. Nella procedura guidata, modificare il tipo di contenuto della `Yearly Income` colonna da **continuo** a **discretizzazione**.  
  
> [!NOTE]  
>  È inoltre possibile modificare anche il modello di data mining creato nell'esercitazione di base sul data mining per discretizzare la colonna della struttura di data mining [`Yearly Income]`. Per informazioni su come eseguire questa operazione, vedere [modificare la discretizzazione di una colonna in un modello di data mining](/analysis-services/data-mining/change-the-discretization-of-a-column-in-a-mining-model). Tuttavia, quando si modifica la discretizzazione della colonna, viene forzata la rielaborazione della struttura di data mining modificando i risultati degli altri modelli compilati utilizzando tale struttura.  
  
```  
SELECT DISTINCT [Yearly Income] AS [Bucket Average],   
    RangeMin([Yearly Income]) AS [Bucket Minimum],   
    RangeMax([Yearly Income]) AS [Bucket Maximum]  
FROM [TM Decision Tree]  
```  
  
 Risultati dell'esempio:  
  
|Bucket Average|Bucket Minimum|Bucket Maximum|  
|--------------------|--------------------|--------------------|  
||||  
|24610,7|10000|39221,41|  
|55115,73|39221,41|71010,05|  
|84821,54|71010,05|98633,04|  
|111633,9|98633,04|124634,7|  
|147317,4|124634,7|170000|  
  
 È possibile notare che i valori della colonna [Yearly Income] sono stati discretizzati in cinque bucket, più una riga aggiuntiva di valori null per rappresentare i valori mancanti.  
  
 Il numero di posizioni decimali nei risultati dipende dal client utilizzato per l'esecuzione delle query. Nell'esempio i risultati sono stati arrotondati a due posizioni decimali, sia per semplicità che per riflettere i valori visualizzati in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 Ad esempio, se si esplora il modello mediante il visualizzatore Microsoft Decision Trees e si seleziona un nodo contenente i clienti raggruppati in base al reddito, nella descrizione comandi vengono visualizzate le seguenti proprietà del nodo:  
  
 Age >= 69 e Annual Income < 39221,41  
  
> [!NOTE]  
>  Il valore minimo del bucket minimo e il valore massimo del bucket massimo rappresentano i valori minimo e massimo osservati. Tutti i valori che non rientrano in questo intervallo osservato vengono considerati appartenenti ai bucket minimo e massimo.  
  
## <a name="see-also"></a>Vedere anche  
 [SELEZIONARE &#40;DMX&#41;](../dmx/select-dmx.md)   
 [Le estensioni di data mining &#40;DMX&#41; le istruzioni di manipolazione dei dati](../dmx/dmx-statements-data-manipulation.md)   
 [Guida di riferimento alle istruzioni DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
