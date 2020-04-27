---
title: 'Esercitazione: Introduzione alle espressioni | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2d05ef4c-5f91-48b2-8795-f0a201a0b3cc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 79563abac2c6a9ed64dff93667ff3d3966b70bc5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66098853"
---
# <a name="tutorial-introducing-expressions"></a>Esercitazione: Introduzione alle espressioni
  Le espressioni consentono di creare report potenti e flessibili. In questa esercitazione verrà illustrato come creare e implementare espressioni in cui vengono utilizzati operatori e funzioni comuni. Si utilizzerà la finestra di dialogo **espressione** per scrivere espressioni che concatenano i valori dei nomi, ricercare valori in un set di dati separato, visualizzare immagini diverse in base ai valori dei campi e così via.  
  
 Il report è a barre con righe alternate in bianco e in un altro colore che può essere selezionato tramite un parametro incluso nel report.  
  
 Nell'immagine seguente viene illustrato un report simile a quello che verrà creato.  
  
 ![rs_ExpressionsTutorial](../../2014/tutorials/media/rs-expressionstutorial.gif "rs_ExpressionsTutorial")  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a>Cosa si apprenderà  
 In questa esercitazione verranno illustrate le operazioni seguenti:  
  
1.  [Creare un report tabella e un set di dati dalla Creazione guidata tabella o matrice](#Setup)  
  
2.  [Aggiornare i nomi predefiniti dell'origine dati e del set di dati](#UpdateNames)  
  
3.  [Visualizzare il nome, l'iniziale e il cognome](#Concatenate)  
  
4.  [Utilizzare immagini per visualizzare il sesso](#Gender)  
  
5.  [Cercare il nome CountryRegion](#Lookup)  
  
6.  [Contare i giorni dall'ultimo acquisto](#Count)  
  
7.  [Utilizzare un indicatore per mostrare il confronto vendite](#Indicator)  
  
8.  [Rendere il report un report "barra verde"](#GreenBar)  
  
### <a name="other-optional-steps"></a>Altri passaggi facoltativi  
  
-   [Formattare la colonna della data](#DateFormat)  
  
-   [Aggiungere un titolo al report](#Title)  
  
-   [Salva il report](#Save)  
  
 Tempo previsto per il completamento di questa esercitazione: 30 minuti.  
  
## <a name="requirements"></a>Requisiti  
 Per informazioni sui requisiti, vedere [Prerequisiti per le esercitazioni &#40;Generatore report&#41;](../reporting-services/report-builder-tutorials.md).  
  
##  <a name="1-create-a-table-report-and-dataset-from-the-table-or-matrix-wizard"></a><a name="Setup"></a>1. creare un report tabella e un set di dati dalla creazione guidata tabella o matrice  
 Creare un report tabella, un'origine dati e un set di dati. Durante la disposizione della tabella verranno inclusi solo pochi campi. Dopo aver completato la procedura guidata, si aggiungeranno manualmente colonne. La procedura guidata consente di disporre la tabella e di applicare uno stile facilmente.  
  
> [!NOTE]  
>  Nella query di questa esercitazione sono contenuti i valori dei dati in modo che non sia necessaria un'origine dati esterna. Tale condizione rende tuttavia la query piuttosto lunga. In una query di un ambiente aziendale non sarebbe incluso alcun dato. Questo esempio è solo a scopo illustrativo.  
  
> [!NOTE]  
>  In questa esercitazione, i passaggi per la procedura guidata sono consolidati in un'unica procedura. Per istruzioni dettagliate su come selezionare un server di report, come scegliere un'origine dati e come creare un set di dati, vedere la prima esercitazione di questa serie: [Esercitazione: Creazione di un report tabella semplice &#40;Generatore report&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md).  
  
#### <a name="to-create-a-new-table-report"></a>Per creare un nuovo report tabella  
  
1.  Fare clic sul pulsante **Start**, scegliere **programmi**, fare clic su [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **Generatore report**e quindi su **Generatore report**.  
  
     Verrà visualizzata la finestra di dialogo **Introduzione** .  
  
    > [!NOTE]  
    >  Se la finestra di dialogo **Introduzione** non viene visualizzata, dal pulsante **Generatore report** fare clic su **nuovo**.  
  
    > [!NOTE]  
    >  Se si preferisce utilizzare la versione ClickOnce di Generatore report, aprire Gestione report e fare clic su **Generatore report**oppure accedere a un sito di SharePoint in cui sono abilitati i tipi di contenuto di Reporting Services, ad esempio i report, quindi fare clic su **Generatore report report** dal menu **nuovo documento** nella scheda **documenti** di una raccolta documenti condivisa.  
  
2.  Nel riquadro sinistro verificare che sia selezionata l'opzione **Nuovo report** .  
  
3.  Nel riquadro destro fare clic su **Creazione guidata tabella o matrice**.  
  
4.  Nella pagina **Scegliere un set di dati** fare clic su **Crea un set di dati**.  
  
5.  Fare clic su **Avanti**.  
  
6.  Nella pagina **Scegliere una connessione a un'origine dei dati** selezionare un'origine dati che sia del tipo **SQL Server**. Selezionare un'origine dati dall'elenco o passare al server di report per selezionarne una.  
  
7.  Fare clic su **Avanti**.  
  
8.  Nella pagina **Progetta query** fare clic su **Modifica come testo**.  
  
9. Incollare la query seguente nel relativo riquadro:  
  
    ```  
    SELECT 'Lauren' AS FirstName,'Johnson' AS LastName, 'American Samoa' AS StateProvince, 1 AS CountryRegionID,'Unknown' AS Gender, CAST(9996.60 AS money) AS YTDPurchase, CAST('2010-6-10' AS date) AS LastPurchase  
    UNION SELECT'Warren' AS FirstName, 'Pal' AS LastName, 'New South Wales' AS StateProvince, 2 AS CountryRegionID, 'Male' AS Gender, CAST(5747.25 AS money) AS YTDPurchase, CAST('2010-7-3' AS date) AS LastPurchase  
    UNION SELECT 'Fernando' AS FirstName, 'Ross' AS LastName, 'Alberta' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(9248.15 AS money) AS YTDPurchase, CAST('2010-10-17' AS date) AS LastPurchase  
    UNION SELECT 'Rob' AS FirstName, 'Caron' AS LastName, 'Northwest Territories' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(742.50 AS money) AS YTDPurchase, CAST('2010-4-29' AS date) AS LastPurchase  
    UNION SELECT 'James' AS FirstName, 'Bailey' AS LastName, 'British Columbia' AS StateProvince, 3 AS CountryRegionID, 'Male' AS Gender, CAST(1147.50 AS money) AS YTDPurchase, CAST('2010-6-15' AS date) AS LastPurchase  
    UNION SELECT  'Bridget' AS FirstName, 'She' AS LastName, 'Hamburg' AS StateProvince, 4 AS CountryRegionID, 'Female' AS Gender, CAST(7497.30 AS money) AS YTDPurchase, CAST('2010-5-10' AS date) AS LastPurchase  
    UNION SELECT 'Alexander' AS FirstName, 'Martin' AS LastName, 'Saxony' AS StateProvince, 4 AS CountryRegionID, 'Male' AS Gender, CAST(2997.60 AS money) AS YTDPurchase, CAST('2010-11-19' AS date) AS LastPurchase  
    UNION SELECT 'Yolanda' AS FirstName, 'Sharma' AS LastName ,'Micronesia' AS StateProvince, 5 AS CountryRegionID, 'Female' AS Gender, CAST(3247.95 AS money) AS YTDPurchase, CAST('2010-8-23' AS date) AS LastPurchase  
    UNION SELECT 'Marc' AS FirstName, 'Zimmerman' AS LastName, 'Moselle' AS StateProvince, 6 AS CountryRegionID, 'Male' AS Gender, CAST(1200.00 AS money) AS YTDPurchase, CAST('2010-11-16' AS date) AS LastPurchase  
    UNION SELECT 'Katherine' AS FirstName, 'Abel' AS LastName, 'Moselle' AS StateProvince, 6 AS CountryRegionID, 'Female' AS Gender, CAST(2025.00 AS money) AS YTDPurchase, CAST('2010-12-1' AS date) AS LastPurchase  
    UNION SELECT 'Nicolas' as FirstName, 'Anand' AS LastName, 'Seine (Paris)' AS StateProvince, 6 AS CountryRegionID, 'Male' AS Gender, CAST(1425.00 AS money) AS YTDPurchase, CAST('2010-12-11' AS date) AS LastPurchase  
    UNION SELECT 'James' AS FirstName, 'Peters' AS LastName, 'England' AS StateProvince, 12 AS CountryRegionID, 'Male' AS Gender, CAST(887.50 AS money) AS YTDPurchase, CAST('2010-8-15' AS date) AS LastPurchase  
    UNION SELECT 'Alison' AS FirstName, 'Nath' AS LastName, 'Alaska' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(607.50 AS money) AS YTDPurchase, CAST('2010-10-13' AS date) AS LastPurchase  
    UNION SELECT 'Grace' AS FirstName, 'Patterson' AS LastName, 'Kansas' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(1215.00 AS money) AS YTDPurchase, CAST('2010-10-18' AS date) AS LastPurchase  
    UNION SELECT 'Bobby' AS FirstName, 'Sanchez' AS LastName, 'North Dakota' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(6191.00 AS money) AS YTDPurchase, CAST('2010-9-17' AS date) AS LastPurchase  
    UNION SELECT 'Charles' AS FirstName, 'Reed' AS LastName, 'Nebraska' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(8772.00 AS money) AS YTDPurchase, CAST('2010-8-27' AS date) AS LastPurchase  
    UNION SELECT 'Orlando' AS FirstName, 'Romeo' AS LastName, 'Texas' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(8578.00 AS money) AS YTDPurchase, CAST('2010-7-29' AS date) AS LastPurchase  
    UNION SELECT 'Cynthia' AS FirstName, 'Randall' AS LastName, 'Utah' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(7218.10 AS money) AS YTDPurchase, CAST('2010-1-11' AS date) AS LastPurchase  
    UNION SELECT 'Rebecca' AS FirstName, 'Roberts' AS LastName, 'Washington' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(8357.80 AS money) AS YTDPurchase, CAST('2010-10-28' AS date) AS LastPurchase  
    UNION SELECT 'Cristian' AS FirstName, 'Petulescu' AS LastName, 'Wisconsin' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(3470.00 AS money) AS YTDPurchase, CAST('2010-11-30' AS date) AS LastPurchase  
    UNION SELECT 'Cynthia' AS FirstName, 'Randall' AS LastName, 'Utah' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(7218.10 AS money) AS YTDPurchase, CAST('2010-1-11' AS date) AS LastPurchase  
    UNION SELECT 'Rebecca' AS FirstName, 'Roberts' AS LastName, 'Washington' AS StateProvince, 7 AS CountryRegionID, 'Female' AS Gender, CAST(8357.80 AS money) AS YTDPurchase, CAST('2010-10-28' AS date) AS LastPurchase  
    UNION SELECT 'Cristian' AS FirstName, 'Petulescu' AS LastName, 'Wisconsin' AS StateProvince, 7 AS CountryRegionID, 'Male' AS Gender, CAST(3470.00 AS money) AS YTDPurchase, CAST('2010-11-30' AS date) AS LastPurchase  
    ```  
  
     Nella query vengono specificati nomi di colonne tra cui data di nascita, nome, cognome, stato o provincia, identificatore di paese/regione, sesso e acquisti da inizio anno.  
  
10. Sulla barra degli strumenti Progettazione query fare clic su **Esegui** (**!**). Nel set di risultati vengono visualizzate 20 righe di dati e sono incluse le colonne seguenti: FirstName, LastName, StateProvince, CountryRegionID, Gender, YTDPurchase e LastPurchase.  
  
11. Fare clic su **Avanti**.  
  
12. Nella pagina **Disponi campi** trascinare i campi seguenti nell'ordine specificato, dall'elenco **Campi disponibili** all'elenco **Valori** .  
  
    -   StateProvince  
  
    -   CountryRegionID  
  
    -   LastPurchase  
  
    -   YTDPurchase  
  
     Dal momento che in CountryRegionID e YTDPurchase sono contenuti dati numerici, per impostazione predefinita a tali campi viene applicata l'aggregazione SUM.  
  
    > [!NOTE]  
    >  I campi FirstName e LastName non sono inclusi. Verranno aggiunti in un passaggio successivo.  
  
13. Nell'elenco **valori** fare clic con il pulsante `CountryRegionID` destro del mouse e scegliere l'opzione **Sum** .  
  
     Al campo CountryRegionID non viene più applicata la somma.  
  
14. Nell'elenco **Valori** fare clic con il pulsante destro del mouse su **YTDPurchase** e sull'opzione **Somma** .  
  
     Al campo YTDPurchase non viene più applicata la somma.  
  
15. Fare clic su **Avanti**.  
  
16. Nella pagina **Scegliere il layout** fare clic su **Avanti**.  
  
17. Nella pagina **scegliere uno stile** fare clic su **Slate**, quindi fare clic su **fine**.  
  
##  <a name="2-update-default-names-of-the-data-source-and-dataset"></a><a name="UpdateNames"></a>2. aggiornare i nomi predefiniti dell'origine dati e del set di dati  
  
#### <a name="to-update-the-default-name-of-the-data-source"></a>Per aggiornare il nome predefinito dell'origine dati  
  
1.  Nel riquadro Dati report espandere **Origini dati**.  
  
2.  Fare clic con il pulsante destro del mouse su **DataSource1** e scegliere **Proprietà origine dati.**  
  
3.  Nella casella **Nome** digitare **ExpressionsDataSource**  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-update-the-default-name-of-the-dataset"></a>Per aggiornare il nome predefinito del set di dati  
  
1.  Nel riquadro Dati report espandere **Set di dati**.  
  
2.  Fare clic con il pulsante destro del mouse su **DataSet1** e scegliere **Proprietà set di dati.**  
  
3.  Nella casella **Nome** digitare **Expressions**  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="3-display-first-name-initial-and-last-name"></a><a name="Concatenate"></a>3. visualizzare il nome, l'iniziale e il cognome  
 Usare la funzione **Left** e l'operatore di **concatenazione**(**&**) in un'espressione tramite cui viene restituito un nome con un'iniziale e un cognome. È possibile compilare l'espressione passaggio dopo passaggio oppure andare avanti nella procedura e copiare e incollare l'espressione dall'esercitazione nella finestra di dialogo **Espressione** .  
  
#### <a name="to-add-the-name-column"></a>Per aggiungere la colonna Name  
  
1.  Fare clic con il pulsante destro del mouse sulla colonna **StateProvince** , scegliere **Inserisci colonna**e fare clic su **A sinistra**.  
  
     Una nuova colonna verrà aggiunta a sinistra della colonna **StateProvince** .  
  
2.  Fare clic sul titolo della nuova colonna e digitare **Name**  
  
3.  Fare clic con il pulsante destro del mouse sulla cella di dati per la colonna **Name** e scegliere **Espressione**.  
  
4.  Nella finestra di dialogo **Espressione** espandere **Funzioni comuni**e fare clic su **Text**.  
  
5.  Nell'elenco **Elemento** fare doppio clic su **Left**.  
  
     La funzione **Left** viene aggiunta all'espressione.  
  
6.  Nell'elenco **Categoria** fare clic su **Fields (Expressions)**.  
  
7.  Nell'elenco **Valori** fare doppio clic su **FirstName**.  
  
8.  Digitare **, 1)**  
  
     Questa espressione consente di estrarre un carattere dal valore **FirstName** , a partire da sinistra.  
  
9. Digitare **&" "&**  
  
10. Nell'elenco **Valori** fare doppio clic su **LastName**.  
  
     L'espressione completa è: `=Left(Fields!FirstName.Value, 1) &" "& Fields!LastName.Value`  
  
11. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
12. Fare clic su **Esegui** per visualizzare l'anteprima del report.  
  
##  <a name="4-use-images-to-display-gender"></a><a name="Gender"></a>4. utilizzare le immagini per visualizzare il sesso  
 Utilizzare immagini per visualizzare il sesso di una persona e identificare i valori sconosciuti relativi al sesso utilizzando una terza immagine. Si aggiungeranno al report tre immagini nascoste e una nuova colonna per visualizzare le immagini, quindi si stabilirà l'immagine che verrà visualizzata nella colonna in base al valore del campo Gender.  
  
 Per applicare un colore alla cella della tabella in cui è contenuta l'immagine durante la creazione di un report a barre, verrà aggiunto un rettangolo in cui verrà inserita successivamente l'immagine. È necessario utilizzare un rettangolo perché consente, a differenza di un'immagine, l'applicazione di un colore di sfondo.  
  
 Nell'esercitazione vengono utilizzate immagini che vengono installate con Windows, ma è possibile utilizzare qualsiasi immagine disponibile. Verranno utilizzate immagini incorporate che non è necessario siano installate nel computer locale o nel server di report.  
  
#### <a name="to-add-images-to-the-report-body"></a>Per aggiungere immagini al corpo del report  
  
1.  Fare clic su **Progettazione** per tornare alla visualizzazione Struttura.  
  
2.  Nella scheda **Inserisci** della barra multifunzione selezionare **Immagine** e fare clic nel corpo del report, sotto la tabella.  
  
     Verrà visualizzata la finestra di dialogo **Proprietà immagine**.  
  
3.  Fare clic su **Importa** e passare a C:\Users\Public\Immagini pubbliche\Immagini campione.  
  
4.  Fare clic sul file Penguins.JPG e scegliere **Apri**.  
  
     Nella finestra di dialogo **Proprietà immagine** fare clic su **Visibilità** e scegliere l'opzione **Nascondi**.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  Ripetere i passaggi da 2 a 5, ma scegliere il file Koala.JPG.  
  
7.  Ripetere i passaggi da 2 a 5, ma scegliere il file Tulips.JPG.  
  
#### <a name="to-add-the-gender-column"></a>Per aggiungere la colonna Gender  
  
1.  Fare clic con il pulsante destro del mouse sulla colonna **Name**, scegliere **Inserisci colonna** e fare clic su **A destra**.  
  
     Una nuova colonna verrà aggiunta a destra della colonna **Name**.  
  
2.  Fare clic sul titolo della nuova colonna e digitare **Gender**  
  
#### <a name="to-add-a-rectangle"></a>Per aggiungere un rettangolo  
  
-   Nella scheda **Inserisci** della barra multifunzione selezionare **Rettangolo** e fare clic nella cella di dati della colonna **Gender**.  
  
     Verrà aggiunto un rettangolo alla cella.  
  
#### <a name="to-add-an-image-to-the-rectangle"></a>Per aggiungere un'immagine al rettangolo  
  
1.  Fare clic con il pulsante destro del mouse nel rettangolo, scegliere **Inserisci** e fare clic su **Immagine**.  
  
2.  Nella finestra di dialogo **Proprietà immagine** fare clic sulla freccia a discesa accanto a **Usare questa immagine** e selezionare una delle immagini aggiunte, ad esempio Penguins.JPG.  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-use-images-to-show-gender"></a>Per utilizzare immagini per mostrare il sesso  
  
1.  Fare clic con il pulsante destro del mouse sull'immagine nella cella di dati nella colonna **Gender** e scegliere **Proprietà immagine**.  
  
2.  Nella finestra di dialogo **Proprietà immagine** fare clic sul pulsante dell'espressione **fx** accanto alla casella di testo **Usare questa immagine**.  
  
3.  Nella finestra di dialogo **Espressione** espandere **Funzioni comuni** e fare clic su **Program Flow**.  
  
4.  Nell'elenco **Elemento** fare doppio clic su **Switch**.  
  
5.  Nell'elenco **Categoria** fare clic su **Fields (Expressions)**.  
  
6.  Nell'elenco **Valori** fare doppio clic su **Gender**.  
  
7.  Digitare **="Male", "Koala",**  
  
8.  Nell'elenco **Valori** fare doppio clic su **Gender**.  
  
9. Digitare **="Female", "Penguins",**  
  
10. Nell'elenco **Valori** fare doppio clic su **Gender**.  
  
11. Digitare **="Unknown", "Tulips")**  
  
     L'espressione completa è: `=Switch(Fields!Gender.Value ="Male", "Koala",Fields!Gender.Value ="Female","Penguins",Fields!Gender.Value ="Unknown","Tulips")`  
  
12. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
13. Scegliere di nuovo **OK** per chiudere la finestra di dialogo **Proprietà immagine**.  
  
14. Fare clic su **Esegui** per visualizzare l'anteprima del report.  
  
##  <a name="5-look-up-countryregion-name"></a><a name="Lookup"></a>5. cercare il nome CountryRegion  
 Creare il set di dati CountryRegion e usare la funzione **Lookup** per visualizzare il nome di un paese o di una regione anziché il relativo identificatore.  
  
#### <a name="to-create-the-countryregion-dataset"></a>Per creare un set di dati CountryRegion  
  
1.  Fare clic su **Progettazione** per tornare alla visualizzazione Struttura.  
  
2.  Nel riquadro dei dati del report fare clic su **nuovo** , quindi su **set**di dati.  
  
3.  Fare clic su **Usare un set di dati incorporato nel report**.  
  
4.  Selezionare ExpressionsDataSource nell'elenco **Origine dati** .  
  
5.  Nella casella **Nome** digitare **CountryRegion**  
  
6.  Verificare che sia selezionato il tipo di query **Testo** e fare clic su **Progettazione query**.  
  
7.  Fare clic su **Modifica come testo**.  
  
8.  Copiare e incollare la query seguente nel relativo riquadro:  
  
    ```  
    SELECT 1 AS ID, 'American Samoa' AS CountryRegion  
    UNION SELECT 2 AS CountryRegionID, 'Australia' AS CountryRegion  
    UNION SELECT 3 AS ID, 'Canada' AS CountryRegion  
    UNION SELECT 4 AS ID, 'Germany' AS CountryRegion  
    UNION SELECT 5 AS ID, 'Micronesia' AS CountryRegion  
    UNION SELECT 6 AS ID, 'France' AS CountryRegion  
    UNION SELECT 7 AS ID, 'United States' AS CountryRegion  
    UNION SELECT 8 AS ID, 'Brazil' AS CountryRegion  
    UNION SELECT 9 AS ID, 'Mexico' AS CountryRegion  
    UNION SELECT 10 AS ID, 'Japan' AS CountryRegion  
    UNION SELECT 10 AS ID, 'Australia' AS CountryRegion  
    UNION SELECT 12 AS ID, 'United Kingdom' AS CountryRegion  
    ```  
  
9. Fare clic su **Esegui** (**!**) per eseguire la query.  
  
     I risultati query sono i nomi e gli identificatori di paesi.  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. Scegliere di nuovo **OK** per chiudere la finestra di dialogo **Proprietà set di dati** .  
  
#### <a name="to-look-up-values-in-the-countryregion-dataset"></a>Per cercare valori nel set di dati CountryRegion  
  
1.  Fare clic sul titolo della colonna **Country Region ID** ed eliminare il testo ID.  
  
2.  Fare clic con il pulsante destro del mouse sulla cella di dati per la colonna **Country Region** e scegliere **Espressione**.  
  
3.  Eliminare l'espressione eccetto il segno iniziale di uguale (=).  
  
     L'espressione rimanente è: `=`  
  
4.  Nella finestra di dialogo **Espressione** espandere **Funzioni comuni** e fare clic su **Miscellaneous**.  
  
5.  Nell'elenco **Elemento** fare doppio clic su **Lookup**.  
  
6.  Nell'elenco **Categoria** fare clic su **Fields (Expressions)**.  
  
7.  Nell'elenco **valori** fare doppio clic su `CountryRegionID`.  
  
8.  Se il cursore non si trova già subito dopo `CountryRegionID.Value`, posizionarlo in tale punto.  
  
9. Eliminare la parentesi chiusa e digitare **,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")**  
  
     L'espressione completa è: `=Lookup(Fields!CountryRegionID.Value,Fields!ID.value, Fields!CountryRegion.value, "CountryRegion")`  
  
     La sintassi della funzione **Lookup** consente di specificare una ricerca tra CountryRegionID e ID nel set di dati CountryRegion tramite cui viene restituito il valore CountryRegion, che si trova anche nel set di dati CountryRegion.  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. Fare clic su **Esegui** per visualizzare l'anteprima del report.  
  
##  <a name="6-count-days-since-last-purchase"></a><a name="Count"></a>6. contare i giorni dall'ultimo acquisto  
 Aggiungere una colonna e quindi usare la funzione **Now** o la `ExecutionTime` variabile globale incorporata per calcolare il numero di giorni trascorsi dall'ultimo acquisto di una persona.  
  
#### <a name="to-add-the-days-ago-column"></a>Per aggiungere la colonna Days Ago  
  
1.  Fare clic su **Progettazione** per tornare alla visualizzazione Struttura.  
  
2.  Fare clic con il pulsante destro del mouse sulla colonna **Last Purchase** , scegliere **Inserisci colonna**e fare clic su **A destra**.  
  
     Una nuova colonna verrà aggiunta a destra della colonna **Last Purchase** .  
  
3.  Nell'intestazione di colonna digitare **Days Ago**  
  
4.  Fare clic con il pulsante destro del mouse sulla cella di dati per la colonna **Days Ago** e scegliere **Espressione**.  
  
5.  Nella finestra di dialogo **Espressione** espandere **Funzioni comuni** e fare clic su **Date & Time**.  
  
6.  Nell'elenco **Elemento** fare doppio clic su **DateDiff**.  
  
7.  Se il cursore non si trova già subito dopo `DateDiff(`, posizionarlo in tale punto.  
  
8.  Digitare **"d",**  
  
9. Nell'elenco **Categoria** fare clic su **Fields (Expressions)**.  
  
10. Nell'elenco **Valori** fare doppio clic su **LastPurchase**.  
  
11. Se il cursore non si trova già subito dopo `Fields!LastPurchase.Value`, posizionarlo in tale punto.  
  
12. Digitare **,**  
  
13. Nell' elenco **Categoria**, fare di nuovo clic su **Date & Time**.  
  
14. Nell'elenco **Elemento** fare doppio clic su **Now**.  
  
    > [!WARNING]  
    >  Nei report di produzione non è consigliabile usare la funzione **Now** in espressioni valutate più volte quando si esegue il rendering del report, ad esempio nelle righe di dettaglio di un report. Il valore di **Now** cambia da riga a riga e i valori diversi influiscono sui risultati della valutazione delle espressioni, generando risultati leggermente incoerenti. È consigliabile invece ricorrere alla variabile globale `ExecutionTime` di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
15. Se il cursore non si trova già subito dopo `Now(`, posizionarlo in tale punto.  
  
16. Eliminare la parentesi aperta e digitare **)**  
  
     L'espressione completa è: `=DateDiff("d", Fields!LastPurchase.Value, Now)`  
  
17. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="7-use-an-indicator-to-show-sales-comparison"></a><a name="Indicator"></a>7. utilizzare un indicatore per mostrare il confronto delle vendite  
 Aggiungere una nuova colonna e usare un indicatore per indicare se gli acquisti da inizio anno (YTD) di una persona sono al di sopra o al di sotto degli acquisti YTD medi. La funzione **Round** consente di rimuovere i decimali dai valori.  
  
 Per la configurazione dell'indicatore e dei relativi stati sono necessari numerosi passaggi. Se si desidera, nella procedura "per configurare l'indicatore", è possibile ignorare e copiare e incollare le espressioni complete da questa esercitazione nella finestra di dialogo **espressione** .  
  
#### <a name="to-add-the--or---avg-sales-column"></a>Per aggiungere la colonna + or - AVG Sales  
  
1.  Fare clic con il pulsante destro del mouse sulla colonna **YTD Purchase** , scegliere **Inserisci colonna**e fare clic su **A destra**.  
  
     Una nuova colonna verrà aggiunta a destra della colonna **YTD Purchase** .  
  
2.  Fare clic sul titolo della nuova colonna e digitare **+ or - AVG Sales**  
  
#### <a name="to-add-an-indicator"></a>Per aggiungere un indicatore  
  
1.  Nella scheda **Inserisci** della barra multifunzione selezionare **Indicatore** e fare clic nella cella di dati della colonna **+ or - AVG Sales**.  
  
     Verrà visualizzata la finestra di dialogo **Seleziona tipo indicatore** .  
  
2.  Nel gruppo **Direzionale** di set di icone selezionare il set di tre frecce grigie.  
  
3.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-configure-the-indicator"></a>Per configurare l'indicatore  
  
1.  Fare clic con il pulsante destro del mouse sull'indicatore, selezionare **Proprietà indicatore**e scegliere **Valore e stati**.  
  
2.  Fare clic sul pulsante dell'espressione **fx** accanto alla casella di testo **Valore** .  
  
3.  Nella finestra di dialogo **Espressione** espandere **Funzioni comuni**e fare clic su **Math**.  
  
4.  Nell'elenco **Elemento** fare doppio clic su **Round**.  
  
5.  Nell'elenco **Categoria** fare clic su **Fields (Expressions)**.  
  
6.  Nell'elenco **Valori** fare doppio clic su **YTDPurchase**.  
  
7.  Se il cursore non si trova già subito dopo `Fields!YTDPurchase.Value`, posizionarlo in tale punto.  
  
8.  Tipo**-**  
  
9. Espandere di nuovo **Funzioni comuni** e fare clic su **Aggregate**.  
  
10. Nell'elenco **Elemento** fare doppio clic su **Avg**.  
  
11. Nell'elenco **Categoria** fare clic su **Fields (Expressions)**.  
  
12. Nell'elenco **Valori** fare doppio clic su **YTDPurchase**.  
  
13. Se il cursore non si trova già subito dopo `Fields!YTDPurchase.Value`, posizionarlo in tale punto.  
  
14. Digitare **, "Expressions"))**  
  
     L'espressione completa è: `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions"))`  
  
15. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
16. Nella casella **Unità di misura stati** selezionare **Numerico**.  
  
17. Nella riga con la freccia rivolta verso il basso fare clic sul pulsante **fx** a destra della casella di testo per il valore **Iniziale** .  
  
18. Nella finestra di dialogo **Espressione** espandere **Funzioni comuni**e fare clic su **Math**.  
  
19. Nell'elenco **Elemento** fare doppio clic su **Round**.  
  
20. Nell'elenco **Categoria** fare clic su **Fields (Expressions)**.  
  
21. Nell'elenco **Valori** fare doppio clic su **YTDPurchase**.  
  
22. Se il cursore non si trova già subito dopo `Fields!YTDPurchase.Value`, posizionarlo in tale punto.  
  
23. Tipo**-**  
  
24. Espandere di nuovo **Funzioni comuni** e fare clic su **Aggregate**.  
  
25. Nell'elenco **Elemento** fare doppio clic su **Avg**.  
  
26. Nell'elenco **Categoria** fare clic su **Fields (Expressions)**.  
  
27. Nell'elenco **Valori** fare doppio clic su **YTDPurchase**.  
  
28. Se il cursore non si trova già subito dopo `Fields!YTDPurchase.Value`, posizionarlo in tale punto.  
  
29. Digitare **, "Expressions")) < 0**  
  
     L'espressione completa è: `=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) < 0`  
  
30. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
31. Nella casella di testo per il valore **Finale** digitare **0**  
  
32. Fare clic sulla riga con la freccia orizzontale e scegliere **Elimina**.  
  
33. Nella riga con la freccia rivolta verso l'alto, nella casella **Inizio** digitare **0**  
  
34. Fare clic sul pulsante **fx** a destra della casella di testo per il valore **Finale** .  
  
35. Nella finestra di dialogo **espressione** creare l'espressione:`=Round(Fields!YTDPurchase.Value - Avg(Fields!YTDPurchase.Value, "Expressions")) >0`  
  
36. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
37. Scegliere di nuovo **OK** per chiudere la finestra di dialogo **Proprietà indicatore** .  
  
38. Fare clic su **Esegui** per visualizzare l'anteprima del report.  
  
##  <a name="8-make-the-report-a-green-bar-report"></a><a name="GreenBar"></a>8. rendere il report un report "barra verde"  
 Utilizzare un parametro per specificare il colore da applicare alle righe alternate nel report, rendendolo a barre.  
  
#### <a name="to-add-a-parameter"></a>Per aggiungere un parametro  
  
1.  Fare clic su **Progettazione** per tornare alla visualizzazione Struttura.  
  
2.  Nel riquadro **Dati report** fare clic con il pulsante destro del mouse su **Parametri** e scegliere **Aggiungi parametro**.  
  
     Verrà visualizzata la finestra di dialogo **Proprietà parametri report** .  
  
3.  In **Messaggio di richiesta**digitare **Choose color**  
  
4.  Nella casella **Nome**digitare **RowColor**  
  
5.  Nel riquadro di sinistra scegliere **Valori disponibili**.  
  
6.  Fare clic su **Imposta valori**.  
  
7.  Fare clic su **Aggiungi**.  
  
8.  Nella casella **Etichetta** digitare: **Yellow**  
  
9. Nella casella **Valore** digitare **Yellow**  
  
10. Fare clic su **Aggiungi**.  
  
11. Nella casella **Etichetta** digitare **Green**  
  
12. Nella casella **Valore** digitare **PaleGreen**  
  
13. Fare clic su **Aggiungi**.  
  
14. Nella casella **Etichetta** digitare **Blue**  
  
15. Nella casella **Valore** digitare **LightBlue**  
  
16. Fare clic su **Aggiungi**.  
  
17. Nella casella **Etichetta** digitare **Pink**  
  
18. Nella casella **Valore** digitare **Pink**  
  
19. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="to-apply-alternating-colors-to-detail-rows"></a>Per applicare colori alternati alle righe di dettaglio  
  
1.  Fare clic sulla scheda **Visualizza** sulla barra multifunzione e verificare che l'opzione **Proprietà** sia selezionata.  
  
2.  Fare clic sulla cella di dati per la colonna **Name** e premere MAIUSC.  
  
3.  Fare clic sulle altre celle nella riga singolarmente.  
  
4.  Nel riquadro Proprietà fare clic su **BackgroundColor**.  
  
     Se le proprietà nel riquadro Proprietà sono elencate per categoria, **BackgroundColor** sarà disponibile nella categoria **Fill**.  
  
5.  Fare clic sulla freccia a discesa e scegliere **Espressione**.  
  
6.  Nella finestra di dialogo **Espressione** espandere **Funzioni comuni**e fare clic su **Program Flow**.  
  
7.  Nell'elenco **Elemento** fare doppio clic su **IIf**.  
  
8.  Espandere **Funzioni comuni** e fare clic su **Aggregate**.  
  
9. Nell'elenco **Elemento** fare doppio clic su **RunningValue**.  
  
10. Nell'elenco **Categoria** fare clic su **Fields (Expressions)**.  
  
11. Nell'elenco **Valori** fare doppio clic su **FirstName**.  
  
12. Se il cursore non si trova già subito dopo `Fields!FirstName.Value`, posizionarlo in tale punto e digitare **,**  
  
13. Espandere **Funzioni comuni** e fare clic su **Aggregate**.  
  
14. Nell'elenco **Elemento** fare doppio clic su **Count**.  
  
15. Se il cursore non si trova già subito dopo `Count(`, posizionarlo in tale punto.  
  
16. Eliminare la parentesi aperta e digitare **, "Expressions")**  
  
    > [!NOTE]  
    >  Expressions è il nome del set di dati in cui contare le righe di dati.  
  
17. Espandere **Operatori** e fare clic su **Aritmetici**.  
  
18. Nell'elenco **Elemento** fare doppio clic su **Mod**.  
  
19. Se il cursore non si trova già subito dopo `Mod`, posizionarlo in tale punto.  
  
20. Digitare **2 =0,**  
  
    > [!IMPORTANT]  
    >  Assicurarsi di includere uno spazio prima di digitare il numero 2.  
  
21. Fare clic su **Parametri** e nell'elenco **Valori** fare doppio clic su **RowColor**.  
  
22. Se il cursore non si trova già subito dopo `Parameters!RowColor.Value`, posizionarlo in tale punto.  
  
23. Digitare **, "white")**  
  
     L'espressione completa è: `=IIf(RunningValue(Fields!FirstName.Value,Count, "Expressions") Mod 2 =0, Parameters!RowColor.Value, "White")`  
  
24. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
#### <a name="run-the-report"></a>Eseguire il report  
  
1.  Se non è visualizzata la scheda **Home** fare clic su **Home** per tornare alla visualizzazione della struttura.  
  
2.  Fare clic su **Esegui**.  
  
3.  Nell'elenco a discesa **Scegli colore** selezionare il colore delle barre che non sono bianche nel report.  
  
4.  Fare clic su **Visualizza rapporto**.  
  
     Viene eseguito il rendering del report e nelle righe alternate verrà visualizzato lo sfondo scelto.  
  
##  <a name="optional-format-date-column"></a><a name="DateFormat"></a>opzionale Formattare la colonna della data  
 Formattare la colonna **Last Purchase** in cui sono contenute le date.  
  
#### <a name="to-format-date-column"></a>Per formattare la colonna della data  
  
1.  Fare clic su **Progettazione** per tornare alla visualizzazione Struttura.  
  
2.  Fare clic con il pulsante destro del mouse sulla cella di dati per la colonna **Last Purchase** e fare clic su **Proprietà casella di testo**.  
  
3.  Nella finestra di dialogo **Proprietà casella di testo** fare clic su **Numero**, selezionare **Data** e fare clic sul tipo **\*1/31/2000**.  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="optional-add-a-report-title"></a><a name="Title"></a>opzionale Aggiungere un titolo al report  
 Aggiungere un titolo al report.  
  
#### <a name="to-add-a-report-title"></a>Per aggiungere il titolo di un report  
  
1.  Nell'area di progettazione fare clic su **Fare clic per aggiungere il titolo**.  
  
2.  Digitare **Sales Comparison Summary** e fare clic all'esterno della casella di testo.  
  
3.  Fare clic con il pulsante destro del mouse sulla casella di testo che contiene **Sales Comparison Summary** e fare clic su **Proprietà casella di testo**.  
  
4.  Nella finestra di dialogo **Proprietà casella di testo** fare clic su **Carattere**.  
  
5.  Nell'elenco **Dimensione** selezionare **18pt**.  
  
6.  Nell'elenco **Colore** selezionare **Grigio**.  
  
7.  Selezionare **Grassetto** e **Corsivo**.  
  
8.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="optional-save-the-report"></a><a name="Save"></a>opzionale Salva il report  
 È possibile salvare i report in un server di report, in una raccolta di SharePoint o nel computer locale. Per altre informazioni, vedere [Salvataggio di report &#40;Generatore report&#41;](report-builder/saving-reports-report-builder.md).  
  
 In questa esercitazione il report verrà salvato in un server di report. Se non si dispone dell'accesso a un server di report, sarà possibile salvare il report nel computer locale.  
  
#### <a name="to-save-the-report-to-a-report-server"></a>Per salvare il report in un server di report  
  
1.  Fare clic sul pulsante **Generatore report** , quindi su **Salva con nome**.  
  
2.  Fare clic su **Siti e server recenti**.  
  
3.  Selezionare o digitare il nome del server di report per il quale si dispone delle autorizzazioni di salvataggio dei report.  
  
     Verrà visualizzato il messaggio "Connessione al server di report". Al termine della connessione, verrà visualizzato il contenuto della cartella di report specificata dall'amministratore del server di report come posizione predefinita per i report.  
  
4.  In **Nome** sostituire il nome predefinito con **Sales Comparison Summary**.  
  
5.  Fare clic su **Save**.  
  
 Il report verrà salvato sul server di report. Il nome del server di report al quale si è connessi verrà visualizzato sulla barra di stato nella parte inferiore della finestra.  
  
#### <a name="to-save-the-report-to-your-computer"></a>Per salvare il report nel computer  
  
1.  Fare clic sul pulsante **Generatore report** , quindi su **Salva con nome**.  
  
2.  Fare clic su **Desktop**, **Documenti**o **Risorse del computer**, quindi selezionare la cartella in cui si desidera salvare il report.  
  
3.  In **Nome** sostituire il nome predefinito con **Sales Comparison Summary**.  
  
4.  Fare clic su **Save**.  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni &#40;Generatore report e SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40;Generatore report e SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md)   
 [Indicatori &#40;Generatore report e SSRS&#41;](report-design/indicators-report-builder-and-ssrs.md)   
 [Immagini, caselle di testo, rettangoli e linee &#40;Generatore report e SSRS&#41;](report-design/rectangles-and-lines-report-builder-and-ssrs.md)   
 [Tabelle &#40;Generatore report e SSRS&#41;](report-design/tables-report-builder-and-ssrs.md)   
 [Aggiungere dati a un report &#40;Generatore report e SSRS&#41;](report-data/report-datasets-ssrs.md)  
  
  
