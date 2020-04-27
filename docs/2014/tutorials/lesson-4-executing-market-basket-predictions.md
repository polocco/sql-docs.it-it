---
title: 'Lezione 4: esecuzione di stime Market basket | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b3238f1b-ea04-4253-ade2-838a806b62fe
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3b49fc242eb8b2242269c5af33cc094937bbe0de
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "63312107"
---
# <a name="lesson-4-executing-market-basket-predictions"></a>Lezione 4: Esecuzione delle stime relative a Market Basket
  In questa lezione verrà utilizzata l'istruzione DMX `SELECT` per creare stime basate sui modelli di associazione creati nella [lezione 2: aggiunta di modelli di data mining alla struttura di data mining Market basket](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md). Una query della stima viene creata utilizzando l'istruzione DMX `SELECT` e aggiungendo una clausola `PREDICTION JOIN` Per ulteriori informazioni sulla sintassi di un prediction join, vedere [SELECT FROM &#60;model&#62; prediction join &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx).  
  
 Il modulo **Select \<from Model> prediction join** dell' `SELECT` istruzione contiene tre parti:  
  
-   Un elenco di colonne e funzioni di stima del modello di data mining restituite nel set di risultati. Può includere anche le colonne di input dall'origine dei dati.  
  
-   Una query di origine che definisce i dati utilizzati per la creazione di una stima, Ad esempio, se si stanno creando più stime in un batch, la query di origine è in grado di recuperare un elenco dei clienti.  
  
-   Un mapping tra le colonne del modello di data mining e i dati di origine. Se i nomi delle colonne corrispondono, è possibile utilizzare la sintassi `NATURAL PREDICTION JOIN` e omettere i mapping delle colonne.  
  
 Per migliorare la query, è possibile utilizzare le funzioni di stima che forniscono informazioni aggiuntive, quali la probabilità che una stima sia confermata dai fatti o supporto per una stima nel set di dati di training. Per ulteriori informazioni sulle funzioni di stima, vedere [funzioni &#40;&#41;DMX ](/sql/dmx/functions-dmx).  
  
 È inoltre possibile utilizzare il generatore delle query di stima in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] per creare query di stima.  
  
## <a name="singleton-prediction-join-statement"></a>Istruzione PREDICTION JOIN singleton  
 Il primo passaggio consiste nel creare una query singleton utilizzando la sintassi **Select from \<Model> prediction join** e specificando come input un singolo set di valori. Di seguito è riportato un esempio generico dell'istruzione singleton:  
  
```  
SELECT <select list>  
    FROM [<mining model>]   
[NATURAL] PREDICTION JOIN  
(SELECT '<value>' AS [<column>],   
    (SELECT 'value' AS [<nested column>] UNION  
        SELECT 'value' AS [<nested column>] ...)   
    AS [<nested table>])  
AS [<input alias>]  
```  
  
 La prima riga del codice definisce le colonne del modello di data mining restituite dalla query e specifica il nome del modello di data mining utilizzato per generare la stima:  
  
```  
SELECT <select list> FROM [<mining model>]   
```  
  
 La riga successiva del codice indica l'operazione da eseguire. Perché si specificheranno valori per ognuna delle colonne e si digiteranno i nomi delle colonne in modo che corrispondano al modello, è possibile utilizzare la sintassi `NATURAL PREDICTION JOIN`. Tuttavia, se i nomi della colonna sono diversi, è necessario specificare i mapping tra le colonne nel modello e le colonne nei nuovi dati aggiungendo una clausola `ON`.  
  
```  
[NATURAL] PREDICTION JOIN  
```  
  
 Le righe successive del codice definiscono i prodotti presenti nel carrello acquisti che verranno utilizzati per stimare i prodotti aggiuntivi che un cliente aggiungerà:  
  
```  
(SELECT '<value>' AS [<column>],   
    (SELECT 'value' AS [<nested column>] UNION  
        SELECT 'value' AS [<nested column>] ...)   
    AS [<nested table>])  
```  
  
## <a name="lesson-tasks"></a>Argomenti della lezione  
 In questa lezione verranno eseguite le attività seguenti:  
  
-   Creazione di una query che stima quali altri articoli è probabile che vengano acquistati da un cliente, sulla base degli articoli già inseriti nel carrello acquisti. Questa query verrà creata utilizzando il modello di data mining con il *MINIMUM_PROBABILITY*predefinito.  
  
-   Creazione di una query che stima quali altri articoli è probabile che vengano acquistati da un cliente, sulla base degli articoli già inseriti nel carrello acquisti. Questa query si basa su un modello diverso, in cui *MINIMUM_PROBABILITY* è stato impostato su 0,01. Poiché il valore predefinito per *MINIMUM_PROBABILITY* nei modelli di associazione è 0,3, la query su questo modello deve restituire più elementi possibili rispetto alla query sul modello predefinito.  
  
## <a name="create-a-prediction-by-using-a-model-with-the-default-minimum_probability"></a>Creazione di una stima utilizzando un modello con il valore predefinito per MINIMUM_PROBABILITY  
  
#### <a name="to-create-an-association-query"></a>Per creare una query di associazione  
  
1.  In **Esplora oggetti**fare clic con il pulsante destro del [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]mouse sull'istanza di, scegliere **nuova query**, quindi fare clic su **DMX** per aprire l'editor di query.  
  
2.  Copiare l'esempio generico dell'istruzione `PREDICTION JOIN` nella query vuota.  
  
3.  Sostituire quanto segue:  
  
    ```  
    <select list>   
    ```  
  
     con:  
  
    ```  
    PREDICT([Default Association].[Products],INCLUDE_STATISTICS,3)  
    ```  
  
     È sufficiente includere il nome di colonna [Products], ma utilizzando la funzione [Predict &#40;DMX&#41;](/sql/dmx/predict-dmx) , è possibile limitare il numero di prodotti restituiti dall'algoritmo a tre. È inoltre possibile utilizzare `INCLUDE_STATISTICS`, che restituisce il supporto, la probabilità e il valore della probabilità adattato per ciascun prodotto. Queste statistiche consentono di valutare l'accuratezza della stima.  
  
4.  Sostituire quanto segue:  
  
    ```  
    [<mining model>]   
    ```  
  
     con:  
  
    ```  
    [Default Association]  
    ```  
  
5.  Sostituire quanto segue:  
  
    ```  
    (SELECT '<value>' AS [<column>],   
        (SELECT 'value' AS [<nested column>] UNION  
            SELECT 'value' AS [<nested column>] ...)   
        AS [<nested table>])  
    ```  
  
     con:  
  
    ```  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
     Questa istruzione utilizza l'istruzione `UNION` per specificare tre prodotti che devono essere inclusi nel carrello acquisti insieme ai prodotti stimati. La colonna Model nell'istruzione `SELECT` corrisponde alla colonna del modello presente nella tabella dei prodotti nidificata.  
  
     L'istruzione completa dovrebbe risultare analoga alla seguente:  
  
    ```  
    SELECT  
      PREDICT([Default Association].[Products],INCLUDE_STATISTICS,3)  
    From  
      [Default Association]  
    NATURAL PREDICTION JOIN  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
6.  Scegliere **Salva DMXQuery1. DMX con nome**dal menu **file** .  
  
7.  Nella finestra di dialogo **Salva con** nome individuare la cartella appropriata e assegnare al file `Association Prediction.dmx`il nome.  
  
8.  Sulla barra degli strumenti fare clic sul pulsante **Esegui** .  
  
     La query restituisce una tabella che contiene tre prodotti: HL Mountain Tire, Fender Set – Mountain e ML Mountain Tire. Nella tabella vengono elencati questi prodotti restituiti in ordine di probabilità. Il prodotto restituito con la maggiore probabilità di essere incluso nello stesso carrello acquisti dei tre prodotti specificati nella query viene visualizzato all'inizio della tabella. I due prodotti che seguono sono quelli con la seconda maggiore probabilità di essere inclusi nel carrello acquisti. La tabella contiene anche le statistiche che descrivono l'accuratezza della stima.  
  
## <a name="create-a-prediction-by-using-a-model-with-a-minimum_probability-of-001"></a>Creazione di una stima utilizzando un modello con il valore 0,01 per MINIMUM_PROBABILITY  
  
#### <a name="to-create-an-association-query"></a>Per creare una query di associazione  
  
1.  In **Esplora oggetti**fare clic con il pulsante destro del [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]mouse sull'istanza di, scegliere **nuova query**, quindi fare clic su **DMX** per aprire l'editor di query.  
  
2.  Copiare l'esempio generico dell'istruzione `PREDICTION JOIN` nella query vuota.  
  
3.  Sostituire quanto segue:  
  
    ```  
    <select list>   
    ```  
  
     con:  
  
    ```  
    PREDICT([Modified Association].[Products],INCLUDE_STATISTICS,3)  
    ```  
  
4.  Sostituire quanto segue:  
  
    ```  
    [<mining model>]   
    ```  
  
     con:  
  
    ```  
    [Modified Association]  
    ```  
  
5.  Sostituire quanto segue:  
  
    ```  
    (SELECT '<value>' AS [<column>],   
        (SELECT 'value' AS [<nested column>] UNION  
            SELECT 'value' AS [<nested column>] ...)   
        AS [<nested table>])  
    ```  
  
     con:  
  
    ```  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
     Questa istruzione utilizza l'istruzione `UNION` per specificare tre prodotti che devono essere inclusi nel carrello acquisti insieme ai prodotti stimati. La colonna `[Model]` nell'istruzione `SELECT` corrisponde alla colonna della tabella dei prodotti nidificata.  
  
     L'istruzione completa dovrebbe risultare analoga alla seguente:  
  
    ```  
    SELECT  
      PREDICT([Modified Association].[Products],INCLUDE_STATISTICS,3)  
    From  
      [Modified Association]  
    NATURAL PREDICTION JOIN  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
6.  Scegliere **Salva DMXQuery1. DMX con nome**dal menu **file** .  
  
7.  Nella finestra di dialogo **Salva con** nome individuare la cartella appropriata e assegnare al file `Modified Association Prediction.dmx`il nome.  
  
8.  Sulla barra degli strumenti fare clic sul pulsante **Esegui** .  
  
     La query restituisce una tabella che contiene tre prodotti: HL Mountain Tire, Water Bottle e Fender Set – Mountain. Nella tabella vengono elencati questi prodotti in ordine di probabilità. Il prodotto visualizzato nella parte superiore della tabella è il prodotto con la maggiore probabilità di essere incluso nello stesso carrello acquisti dei tre prodotti specificati nella query. I due prodotti rimanenti sono quelli con la seconda maggiore probabilità di essere inclusi nel carrello acquisti. La tabella contiene anche le statistiche che descrivono l'accuratezza della stima.  
  
     Nei risultati di questa query è possibile osservare che il valore del parametro *MINIMUM_PROBABILITY* influiscono sui risultati restituiti dalla query.  
  
 Questo passaggio conclude l'esercitazione Market Basket. A questo punto si dispone di un set di modelli da utilizzare per stimare i prodotti che i clienti potrebbero acquistare contemporaneamente.  
  
 Per informazioni su come usare DMX in un altro scenario predittivo, vedere [esercitazione DMX Bike Buyer](../../2014/tutorials/bike-buyer-dmx-tutorial.md).  
  
## <a name="see-also"></a>Vedi anche  
 [Esempi di query sul modello di associazione](../../2014/analysis-services/data-mining/association-model-query-examples.md)   
 [Interfacce di query di data mining](../../2014/analysis-services/data-mining/data-mining-query-tools.md)  
  
  
