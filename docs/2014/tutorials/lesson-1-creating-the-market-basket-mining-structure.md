---
title: 'Lezione 1: creazione della struttura di data mining Market basket | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a817c8d1-aff4-42b4-b194-ad9cc1c60f35
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a6a6e123e525512a72d70bcc8ca2eba549d1347e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62676258"
---
# <a name="lesson-1-creating-the-market-basket-mining-structure"></a>Lezione 1: Creazione della struttura di data mining Market Basket
  In questa lezione verrà creata una struttura di data mining che consente di stimare quali prodotti di [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] un cliente tende ad acquistare contemporaneamente. Se non si ha familiarità con le strutture di data mining e il relativo ruolo in data mining, vedere strutture di data mining [&#40;Analysis Services di data mining&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md).  
  
 La struttura di data mining Association che verrà creata in questa lezione supporta l'aggiunta di modelli di data mining basati sull' [algoritmo Microsoft Association](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md). Nelle lezioni successive si utilizzeranno i modelli di data mining per stimare il tipo di prodotti che un cliente tende ad acquistare contemporaneamente, ovvero per un'analisi di mercato sugli acquisti. Ad esempio, è possibile individuare la tendenza ad acquistare contemporaneamente mountain bike, pneumatici per bicicletta e caschi.  
  
 In questa lezione, la struttura di data mining viene definita utilizzando le tabelle nidificate. L'utilizzo delle tabelle nidificate è determinato dal fatto che il dominio dei dati che verrà definito dalla struttura è contenuto in due diverse tabelle di origine. Per ulteriori informazioni sulle tabelle nidificate, vedere [tabelle nidificate &#40;Analysis Services-&#41;di data mining ](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md).  
  
## <a name="create-mining-structure-statement"></a>Istruzione CREATE MINING STRUCTURE  
 Per creare una struttura di data mining contenente una tabella nidificata, utilizzare l'istruzione [create mining structure &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx) . Il codice nell'istruzione può essere suddiviso nelle parti seguenti:  
  
-   Denominazione della struttura  
  
-   Definizione della colonna chiave  
  
-   Definizione delle colonne di data mining  
  
-   Definizione delle colonne della tabella nidificata  
  
 Di seguito è riportato un esempio generico dell'istruzione CREATE MINING STRUCTURE:  
  
```  
CREATE MINING STRUCTURE [<Mining Structure Name>]  
(  
   <key column>,  
   <mining structure columns>,  
   <table columns>  
   (  <nested key column>,  
      <nested mining structure columns> )  
)  
  
```  
  
 La prima riga del codice definisce il nome della struttura:  
  
```  
CREATE MINING STRUCTURE [Mining Structure Name]  
```  
  
 Per informazioni sulla denominazione di un oggetto in DMX, vedere [identificatori &#40;&#41;DMX ](/sql/dmx/identifiers-dmx).  
  
 La riga successiva del codice definisce la colonna chiave per la struttura di data mining, che identifica in modo univoco un'entità nei dati di origine:  
  
```  
<key column>  
```  
  
 La riga successiva del codice è utilizzata per definire le colonne di data mining che verranno utilizzate dai modelli di data mining associati alla struttura di data mining:  
  
```  
<mining structure columns>  
```  
  
 Le righe successive del codice definiscono le colonne delle tabelle nidificate:  
  
```  
<table columns>  
(  <nested key column>,  
   <nested mining structure columns> )  
```  
  
 Per informazioni sui tipi di colonne della struttura di data mining che è possibile definire, vedere [colonne della struttura di data mining](../../2014/analysis-services/data-mining/mining-structure-columns.md).  
  
> [!NOTE]  
>  Per impostazione predefinita, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] crea un set di dati di controllo del 30% per ogni struttura di data mining; tuttavia, quando si utilizza DMX per creare una struttura di data mining, è necessario aggiungere manualmente il set di dati di controllo, se lo si desidera.  
  
## <a name="lesson-tasks"></a>Argomenti della lezione  
 In questa lezione verranno eseguite le attività seguenti:  
  
-   Creazione di una nuova query vuota  
  
-   Modifica della query per creare la struttura di data mining  
  
-   Esecuzione della query  
  
## <a name="creating-the-query"></a>Creazione della query  
 Il primo passaggio consiste nella connessione a un'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] e nella creazione di una nuova query DMX in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a>Per creare una nuova query DMX in SQL Server Management Studio  
  
1.  Aprire [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  Nella finestra di dialogo **Connetti al server** selezionare **Analysis Services**per **tipo di server**. In **nome server**, digitare `LocalHost`o il nome dell'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] a cui si desidera connettersi per questa lezione. Fare clic su **Connetti**.  
  
3.  In **Esplora oggetti**fare clic con il pulsante destro del [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]mouse sull'istanza di, scegliere **nuova query**, quindi fare clic su **DMX**.  
  
     Verrà avviato l'editor di query con una nuova query vuota.  
  
## <a name="altering-the-query"></a>Modifica della query  
 Il passaggio successivo consiste nella modifica dell'istruzione CREATE MINING STRUCTURE descritta in precedenza per creare la struttura di data mining Market Basket.  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a>Per personalizzare l'istruzione CREATE MINING STRUCTURE  
  
1.  Nell'editor di query copiare l'esempio generico dell'istruzione CREATE MINING STRUCTURE nella query vuota.  
  
2.  Sostituire quanto segue:  
  
    ```  
    [mining structure name]   
    ```  
  
     con:  
  
    ```  
    [Market Basket]  
    ```  
  
3.  Sostituire quanto segue:  
  
    ```  
    <key column>  
    ```  
  
     con:  
  
    ```  
    OrderNumber TEXT KEY  
    ```  
  
4.  Sostituire quanto segue:  
  
    ```  
    <table columns>  
    (  <nested key column>,  
       <nested mining structure columns> )  
    ```  
  
     con:  
  
    ```  
    [Products] TABLE (  
        [Model] TEXT KEY  
    )  
    ```  
  
     Il linguaggio TEXT KEY specifica che la colonna Model è la colonna chiave per la tabella nidificata.  
  
     L'istruzione della struttura di data mining completa dovrebbe essere la seguente:  
  
    ```  
    CREATE MINING STRUCTURE [Market Basket] (  
        OrderNumber TEXT KEY,  
        [Products] TABLE (  
            [Model] TEXT KEY  
        )  
    )  
    ```  
  
5.  Scegliere **Salva DMXQuery1. DMX con nome**dal menu **file** .  
  
6.  Nella finestra di dialogo **Salva con** nome individuare la cartella appropriata e assegnare al file `Market Basket Structure.dmx`il nome.  
  
## <a name="executing-the-query"></a>Esecuzione della query  
 Il passaggio conclusivo consiste nell'esecuzione della query. Dopo la creazione e il salvataggio di una query, per creare la struttura di data mining sul server è necessario che la query (l'istruzione) venga eseguita. Per ulteriori informazioni sull'esecuzione di query nell'editor di query, vedere [motore di database editor di query &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).  
  
#### <a name="to-execute-the-query"></a>Per eseguire la query  
  
-   Nell'editor di query fare clic su **Esegui**sulla barra degli strumenti.  
  
     Lo stato della query viene visualizzato nella scheda **messaggi** nella parte inferiore dell'editor di query al termine dell'esecuzione dell'istruzione. Dovrebbero essere visualizzati i messaggi seguenti:  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     Nel server esiste già una nuova struttura denominata **Market basket** .  
  
 Nella lezione successiva verranno aggiunti modelli di data mining alla struttura di data mining Market Basket appena creata.  
  
## <a name="next-lesson"></a>Lezione successiva  
 [Lezione 2: Aggiunta di modelli di data mining alla struttura di data mining Market Basket](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)  
  
  
