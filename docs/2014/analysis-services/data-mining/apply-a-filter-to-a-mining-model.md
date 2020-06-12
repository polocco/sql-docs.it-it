---
title: Applicare un filtro a un modello di data mining | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- model filter [data mining]
- filters [data mining]
- filtering input rows [Analysis Services]
- filtering data [Analysis Services]
ms.assetid: 4d0abeb5-e939-46d3-9097-6e0358244300
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9a7f00e4d9ecbcc539b470cf5b2afe5864eb6114
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2020
ms.locfileid: "84525527"
---
# <a name="apply-a-filter-to-a-mining-model"></a>Applicare un filtro a un modello di data mining
  Se la struttura di data mining contiene una tabella nidificata, è possibile applicare un filtro alla tabella del case, alla tabella nidificata o a entrambe.  
  
 Nella procedura seguente viene illustrato come creare entrambi i tipi di filtro: filtri di case e filtri sulle righe della tabella nidificata.  
  
 La condizione sulla tabella del case restringe i clienti a quelli con il reddito compreso tra 30000 e 40000. La condizione sulla tabella nidificata restringe i clienti a quelli che non hanno acquistato un determinato articolo.  
  
 La condizione di filtro completa creata in questo esempio è la seguente:  
  
```  
[Income] > '30000'   
AND  [Income] < '40000'   
AND EXISTS (SELECT * FROM [<nested table name>]   
WHERE [Model] <> 'Water Bottle' )   
```  
  
### <a name="to-create-a-case-filter-on-a-mining-model"></a>Per creare un filtro di case su un modello di data mining  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in Esplora soluzioni, fare clic sulla struttura di data mining che contiene il modello di data mining da filtrare.  
  
2.  Fare clic sulla scheda **Modelli di data mining** .  
  
3.  Selezionare il modello, quindi fare clic con il pulsante destro del mouse per aprire il menu di scelta rapida.  
  
     -oppure-  
  
     Selezionare il modello. quindi scegliere **Imposta filtro modello** dal menu **Modello di data mining**.  
  
4.  Nella finestra di dialogo **Filtro modello** fare clic sulla riga superiore nella griglia della casella di testo **Colonna struttura di data mining** .  
  
5.  Se l'origine dati contiene una singola tabella flat, l'elenco a discesa visualizza solo i nomi delle colonne di tale tabella.  
  
     Se la struttura di data mining contiene più tabelle, l'elenco mostra i nomi delle tabelle di origine. I nomi delle colonne vengono visualizzati solo dopo la selezione di una tabella.  
  
     Se la struttura di data mining contiene una tabella del case e una tabella nidificata, l'elenco a discesa mostra le colonne dalla tabella del case e il nome della tabella nidificata.  
  
6.  Selezionare una colonna dall'elenco a discesa.  
  
     L'icona a sinistra della casella di testo cambierà per indicare che l'elemento selezionato è una tabella o una colonna.  
  
7.  Fare clic sulla casella di testo **Operatore** e selezionare un operatore dall'elenco. Gli operatori validi variano a seconda del tipo di dati della colonna selezionata.  
  
8.  Fare clic nella casella di testo **Valore** e digitare un valore.  
  
     Ad esempio, selezionare `Income` come colonna, selezionare l'operatore maggiore di (>), quindi digitare `30000` .  
  
9. Fare clic sulla riga successiva nella griglia.  
  
     La condizione di filtro creata viene aggiunta automaticamente nella casella di testo Espressione. Ad esempio, usare `[Income] > '30000'`  
  
10. Fare clic nella casella di testo **AND/OR** nella riga successiva della griglia per aggiungere una condizione.  
  
     Ad esempio, per creare una condizione BETWEEN, selezionare `AND` nell'elenco a discesa di operandi logici.  
  
11. Selezionare un operatore e digitare un valore come descritto nei passaggi 7 e 8.  
  
     Ad esempio, selezionare di `Income` nuovo come colonna, selezionare l'operatore minore di (<), quindi digitare `40000` .  
  
12. Fare clic sulla riga successiva nella griglia.  
  
13. La condizione di filtro nella casella di testo Espressione viene aggiornata automaticamente per includere la nuova condizione. L'espressione completa è la seguente: `[Income] > '30000'AND [Income] < '40000'`  
  
### <a name="to-add-a-filter-on-the-nested-table-in-a-mining-model"></a>Per aggiungere un filtro nella tabella nidificata in un modello di data mining  
  
1.  Nella finestra di dialogo ** \<name> filtro modello** fare clic su una riga vuota della griglia sotto **colonna struttura di data mining**.  
  
2.  Selezionare il nome della tabella nidificata dall'elenco a discesa.  
  
     L'icona a sinistra della casella di testo cambia per indicare che l'elemento selezionato è il nome di una tabella.  
  
3.  Fare clic nella casella di testo **Operatore** e selezionare **Contiene** o **Non contiene**.  
  
     Queste sono le uniche condizioni disponibili per la tabella nidificata nella finestra di dialogo **Filtro modello** , perché la tabella del case è stata limitata solo ai case che contengono un determinato valore nella tabella nidificata. Il valore per la condizione nella tabella nidificata verrà impostato nel passaggio successivo.  
  
4.  Fare clic sulla casella **valore** e quindi sul pulsante **(...)** per compilare un'espressione.  
  
     Verrà visualizzata la finestra di dialogo ** \<name> filtro** . Questa finestra di dialogo consente di impostare condizioni solo nella tabella corrente, che in questo caso è la tabella nidificata.  
  
5.  Fare clic sulla casella **Colonna struttura di data mining** e selezionare un nome di colonna dagli elenchi a discesa di colonne della tabella nidificata.  
  
6.  Fare clic su **Operatore** e selezionare un operatore dall'elenco di operatori validi per la colonna.  
  
7.  Fare clic su **Valore** e digitare un valore.  
  
     Ad esempio, per **colonna struttura di data mining** selezionare `Model` . Per **operator**selezionare `<>` e digitare il valore `Water Bottle` . Questa condizione crea l'espressione di filtro seguente:  
  
```  
EXISTS (SELECT * FROM [<nested table name>] WHERE [Model] <> 'Water Bottle' )   
```  
  
> [!NOTE]  
>  Poiché il numero di attributi della tabella nidificata è potenzialmente illimitato, in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] non viene fornito un elenco di valori possibili da cui effettuare una selezione. È necessario digitare il valore esatto. Inoltre, non è possibile utilizzare un operatore LIKE in una tabella nidificata.  
  
1.  Aggiungere altre condizioni in base alle esigenze, combinando le condizioni selezionando `AND` o `OR` nella casella **e/o** sul lato sinistro della griglia **condizioni** . [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
2.  Nella finestra di dialogo **Filtro modello** esaminare le condizioni create utilizzando la finestra di dialogo **Filtro** . Le condizioni per la tabella nidificata vengono aggiunte alle condizioni per la tabella del case e il set completo di condizioni di filtro viene visualizzato nella casella di testo **Espressione** .  
  
3.  È possibile fare clic su **Modifica query** per modificare manualmente l'espressione di filtro (facoltativo).  
  
    > [!NOTE]  
    >  Se si modifica manualmente una parte di un'espressione di filtro, la griglia verrà disabilitata e da quel momento sarà necessario utilizzare l'espressione di filtro solo in modalità di modifica di testo. Per ripristinare la modalità di modifica della griglia, è necessario cancellare l'espressione di filtro e ricominciare.  
  
  
## <a name="see-also"></a>Vedere anche  
 [Filtri per i modelli di data mining &#40;Analysis Services-&#41;di data mining](mining-models-analysis-services-data-mining.md)   
 [Attività e procedure relative al modello di data mining](mining-model-tasks-and-how-tos.md)   
 [Eliminare un filtro da un modello di data mining](delete-a-filter-from-a-mining-model.md)  
  
  
