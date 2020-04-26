---
title: 'Lezione 3: elaborazione della struttura di data mining Bike Buyer | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e748c2cd-339d-4e82-82f1-be2d0fc41b61
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2e3f85016b32884b9a6b809e28d20d9985f97cd9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/25/2020
ms.locfileid: "62655800"
---
# <a name="lesson-3-processing-the-bike-buyer-mining-structure"></a>Lezione 3: Elaborazione della struttura di data mining Bike Buyer
  In questa lezione verrà utilizzata l'istruzione INSERT INTO e la vista vTargetMail del database di [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] esempio per elaborare le strutture e i modelli di data mining creati nella [lezione 1: creazione della struttura di data mining Bike Buyer](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md) e [lezione 2: aggiunta di modelli di data mining alla struttura di data mining Bike Buyer](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md).  
  
 Quando si elabora una struttura di data mining, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] legge i dati di origine e compila le strutture che supportano i modelli di data mining. Quando si elabora un modello di data mining, i dati definiti dalla struttura di data mining vengono elaborati tramite l'algoritmo di data mining selezionato. L'algoritmo ricerca tendenze e schemi e quindi archivia queste informazioni nel modello di data mining. Il modello di data mining non contiene pertanto i dati di origine effettivi, bensì le informazioni individuate dall'algoritmo. Per ulteriori informazioni sull'elaborazione dei modelli di data mining, vedere [requisiti e considerazioni sull'elaborazione &#40;&#41;di data mining ](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).  
  
 Una struttura di data mining deve essere rielaborata solo se si modifica una colonna della struttura o i dati di origine. Se si aggiunge un modello di data mining a una struttura di data mining già elaborata, è possibile utilizzare l'istruzione INSERT INTO MINING MODEL per eseguire il training del nuovo modello di data mining.  
  
## <a name="train-structure-template"></a>Training del modello di struttura  
 Per eseguire il training della struttura di data mining e dei modelli di data mining associati, utilizzare l'istruzione [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) . Il codice nell'istruzione può essere suddiviso nelle parti seguenti:  
  
-   Identificazione della struttura di data mining  
  
-   Creazione di un elenco delle colonne nella struttura di data mining  
  
-   Definizione dei dati di training  
  
 Di seguito è riportato un esempio generico dell'istruzione INSERT INTO:  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
)  
OPENQUERY([<datasource>],'<SELECT statement>')  
```  
  
 La prima riga del codice identifica la struttura di data mining di cui si eseguirà il training:  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 La riga successiva del codice specifica le colonne definite dalla struttura di data mining. È necessario che siano elencate tutte le colonne nella struttura di data mining e ogni colonna deve essere associata a una colonna nei dati della query di origine.  
  
```  
(  
   <mining structure columns>  
)  
```  
  
 L'ultima riga del codice definisce i dati che verranno utilizzati per il training della struttura di data mining.  
  
```  
OPENQUERY([<datasource>],'<SELECT statement>')  
```  
  
 In questa lezione si utilizzerà `OPENQUERY` per definire i dati di origine. Per informazioni su altri metodi di definizione della query di origine, vedere [&#60;query sui dati di origine&#62;](/sql/dmx/source-data-query).  
  
## <a name="lesson-tasks"></a>Argomenti della lezione  
 In questa lezione verrà eseguita l'attività seguente:  
  
-   Elaborazione della struttura di data mining Bike Buyer  
  
## <a name="processing-the-predictive-mining-structure"></a>Elaborazione della struttura di data mining predittiva  
  
#### <a name="to-process-the-mining-structure-by-using-insert-into"></a>Per elaborare la struttura di data mining mediante INSERT INTO  
  
1.  In **Esplora oggetti**fare clic con il pulsante destro del [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]mouse sull'istanza di, scegliere **nuova query**, quindi fare clic su **DMX**.  
  
     Verrà avviato l'editor di query con una nuova query vuota.  
  
2.  Copiare l'esempio generico dell'istruzione INSERT INTO nella query vuota.  
  
3.  Sostituire quanto segue:  
  
    ```  
    [<mining structure name>]   
    ```  
  
     con:  
  
    ```  
    Bike Buyer  
    ```  
  
4.  Sostituire quanto segue:  
  
    ```  
    <mining structure columns>  
    ```  
  
     con:  
  
    ```  
    [Customer Key],  
    [Age],  
    [Bike Buyer],  
    [Commute Distance],  
    [Education],  
    [Gender],  
    [House Owner Flag],  
    [Marital Status],  
    [Number Cars Owned],  
    [Number Children At Home],  
    [Occupation],  
    [Region],  
    [Total Children],  
    [Yearly Income]  
    ```  
  
5.  Sostituire quanto segue:  
  
    ```  
    OPENQUERY([<datasource>],'<SELECT statement>')  
    ```  
  
     con:  
  
    ```  
    OPENQUERY([Adventure Works DW],  
       'SELECT CustomerKey, Age, BikeBuyer,  
             CommuteDistance,EnglishEducation,  
             Gender,HouseOwnerFlag,MaritalStatus,  
             NumberCarsOwned,NumberChildrenAtHome,   
             EnglishOccupation,Region,TotalChildren,  
             YearlyIncome   
        FROM dbo.vTargetMail')  
    ```  
  
     L'istruzione OPENQUERY fa riferimento all'origine dati [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] per accedere alla vista vTargetMail in cui sono contenuti i dati di origine che verranno utilizzati per il training dei modelli di data mining.  
  
     L'istruzione completa dovrebbe risultare analoga alla seguente:  
  
    ```  
    INSERT INTO MINING STRUCTURE [Bike Buyer]  
    (  
       [Customer Key],  
       [Age],  
       [Bike Buyer],  
       [Commute Distance],  
       [Education],  
       [Gender],  
       [House Owner Flag],  
       [Marital Status],  
       [Number Cars Owned],  
       [Number Children At Home],  
       [Occupation],  
       [Region],  
       [Total Children],  
       [Yearly Income]     
    )  
    OPENQUERY([Adventure Works DW],  
       'SELECT CustomerKey, Age, BikeBuyer,  
             CommuteDistance,EnglishEducation,  
             Gender,HouseOwnerFlag,MaritalStatus,  
             NumberCarsOwned,NumberChildrenAtHome,   
             EnglishOccupation,Region,TotalChildren,  
             YearlyIncome   
        FROM dbo.vTargetMail')  
    ```  
  
6.  Scegliere **Salva DMXQuery1. DMX con nome**dal menu **file** .  
  
7.  Nella finestra di dialogo **Salva con** nome individuare la cartella appropriata e assegnare al file `Process Bike Buyer Structure.dmx`il nome.  
  
8.  Sulla barra degli strumenti fare clic sul pulsante **Esegui** .  
  
 Nella lezione successiva verrà esplorato il contenuto dei modelli di data mining aggiunti alla struttura di data mining in questa lezione.  
  
## <a name="next-lesson"></a>Lezione successiva  
 [Lezione 4: Esplorazione dei modelli di data mining Bike Buyer](../../2014/tutorials/lesson-4-browsing-the-bike-buyer-mining-models.md)  
  
  
