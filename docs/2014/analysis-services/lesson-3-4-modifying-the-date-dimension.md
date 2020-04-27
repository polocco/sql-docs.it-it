---
title: Modifica della dimensione Date | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4689d780-4bf6-4cf8-8fde-eb3f15dd668a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 826d5b1079e9fcfd0d2ec7a9abd55937f2da1a22
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66078795"
---
# <a name="modifying-the-date-dimension"></a>Modifica della dimensione Date
  Nelle attività di questo argomento verrà creata una gerarchia definita dell'utente e verranno modificati i nomi dei membri visualizzati per gli attributi Date, Month, Calendar Quarter e Calendar Semester. Verranno inoltre definite chiavi composte per gli attributi, verrà controllato l'ordinamento dei membri di dimensione e verranno definite relazioni tra attributi.  
  
## <a name="adding-a-named-calculation"></a>Aggiunta di un calcolo denominato  
 È possibile aggiungere un calcolo denominato, ovvero un'espressione SQL rappresentata da una colonna calcolata, a una tabella in una vista origine dati. L'espressione ha lo stesso aspetto e funziona allo stesso modo di una colonna di una tabella. I calcoli denominati consentono di estendere lo schema relazionale delle tabelle esistenti in una vista origine dati senza modificare la tabella dell'origine dati sottostante. Per altre informazioni, vedere [Definire calcoli denominati in una vista origine dati &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
#### <a name="to-add-a-named-calculation"></a>Per aggiungere un calcolo denominato  
  
1.  Per aprire la vista origine dati **Adventure Works DW 2012** , selezionarla con doppio clic nella cartella **Viste origine dati** in Esplora soluzioni.  
  
2.  Nella parte inferiore del riquadro **tabelle** fare clic con il pulsante `Date`destro del mouse su, quindi scegliere **nuovo calcolo denominato**.  
  
3.  Nella finestra di dialogo **Crea calcolo denominato** Digitare `SimpleDate` nella casella **nome colonna** , quindi digitare o copiare e incollare l'istruzione seguente `DATENAME` nella casella **espressione** :  
  
    ```  
    DATENAME(mm, FullDateAlternateKey) + ' ' +  
    DATENAME(dd, FullDateAlternateKey) + ', ' +  
    DATENAME(yy, FullDateAlternateKey)  
    ```  
  
     L'istruzione `DATENAME` consente di estrarre i valori per l'anno, il mese e il giorno dalla colonna FullDateAlternateKey. Questa nuova colonna verrà utilizzata come nome visualizzato per l'attributo FullDateAlternateKey.  
  
4.  Fare clic su **OK**, quindi `Date` espandere nel riquadro **tabelle** .  
  
     Il `SimpleDate` calcolo denominato viene visualizzato nell'elenco di colonne della tabella Date, con un'icona che indica che si tratta di un calcolo denominato.  
  
5.  Scegliere **Salva tutti** dal menu **File**.  
  
6.  Nel riquadro **tabelle** fare clic con il pulsante `Date`destro del mouse su, quindi scegliere **Esplora dati**.  
  
7.  Scorrere verso destra per rivedere l'ultima colonna nella vista **Explore Date Table** (Esplora tabella Date).  
  
     Si noti che `SimpleDate` la colonna viene visualizzata nella vista origine dati, concatenando correttamente i dati di più colonne dall'origine dati sottostante, senza modificare l'origine dati originale.  
  
8.  Chiudere la vista **Explore Date Table** (Esplora tabella Date).  
  
## <a name="using-the-named-calculation-for-member-names"></a>Utilizzo del calcolo denominato per i nomi dei membri  
 Dopo aver creato un calcolo denominato nella vista origine dati, è possibile utilizzarlo come proprietà di un attributo.  
  
#### <a name="to-use-the-named-calculation-for-member-names"></a>Per utilizzare il calcolo denominato per i nomi dei membri  
  
1.  Aprire **Progettazione dimensioni** per la dimensione Date in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. A tale scopo, fare doppio clic sulla `Date` dimensione nel nodo **dimensioni** del **Esplora soluzioni**.  
  
2.  Nel riquadro **Attributi** della scheda **Struttura dimensione** fare clic sull'attributo **Date Key** .  
  
3.  Se la finestra Proprietà non è aperta, aprirla e fare clic sul pulsante **Nascondi automaticamente** sulla barra del titolo in modo che rimanga aperta.  
  
4.  Fare clic sul campo proprietà **NameColumn** nella parte inferiore della finestra, quindi fare clic sul pulsante con i puntini di sospensione (**...**) per aprire la finestra di dialogo **colonna nome** .  
  
5.  Selezionare `SimpleDate` nella parte inferiore dell'elenco **colonna di origine** , quindi fare clic su **OK**.  
  
6.  Scegliere **Salva tutti** dal menu **File**.  
  
## <a name="creating-a-hierarchy"></a>Creazione di una gerarchia  
 È possibile creare una nuova gerarchia trascinando un attributo dal riquadro **Attributi** al riquadro **Gerarchie** .  
  
#### <a name="to-create-a-hierarchy"></a>Per creare una gerarchia  
  
1.  Nella **scheda Struttura dimensione** di Progettazione dimensioni per la `Date` dimensione trascinare l'attributo **Calendar Year** dal riquadro **attributi** al riquadro **gerarchie** .  
  
2.  Trascinare l'attributo **Calendar Semester** dal **riquadro attributi** al ** \<nuovo livello>** cella nel riquadro **gerarchie** , sotto il livello **Calendar Year** .  
  
3.  Trascinare l'attributo **Calendar Quarter** dal riquadro **attributi** al ** \<nuovo livello>** cella nel riquadro **gerarchie** , sotto il livello **Calendar Semester** .  
  
4.  Trascinare l'attributo **English Month Name** dal riquadro **attributi** alla ** \<nuova cella>Level** del riquadro **gerarchie** , sotto il livello **Calendar Quarter** .  
  
5.  Trascinare l'attributo **Date Key** dal riquadro **attributi** al ** \<nuovo livello>** cella nel riquadro **gerarchie** , sotto il livello **English Month Name** .  
  
6.  Nel riquadro **gerarchie** fare clic con il pulsante destro del mouse sulla barra del titolo della gerarchia **gerarchia** , scegliere **Rinomina**, `Calendar Date`quindi digitare.  
  
7.  Utilizzando il menu di scelta rapida `Calendar Date` , nella gerarchia rinominare il livello **English Month Name** in `Calendar Month`, quindi rinominare il livello di **chiave date** su. `Date`  
  
8.  Eliminare l'attributo **Full Date Alternate Key** dal riquadro **Attributi** , in quanto non verrà usato. Fare clic su **OK** nella finestra di conferma **Elimina oggetti** .  
  
9. Scegliere **Salva tutti** dal menu **File**.  
  
## <a name="defining-attribute-relationships"></a>Definizione di relazioni tra attributi  
 Se i dati sottostanti le supportano, è consigliabile definire relazioni tra gli attributi. La definizione di relazioni tra attributi consente di velocizzare l'elaborazione di dimensioni, partizioni e query.  
  
#### <a name="to-define-attribute-relationships"></a>Per definire relazioni tra attributi  
  
1.  In **Progettazione dimensioni** per la `Date` dimensione fare clic sulla scheda **relazioni tra attributi** .  
  
2.  Nel diagramma fare clic con il pulsante destro del mouse sull'attributo **English Month Name** e scegliere **Nuova relazione tra attributi**.  
  
3.  Nella finestra di dialogo **Crea relazione tra attributi** l'opzione **Attributo di origine** è impostata su **English Month Name**. Impostare **Attributo correlato** su **Calendar Quarter**.  
  
4.  Nell'elenco **Tipo di relazione** impostare il tipo di relazione su **Rigida**.  
  
     Il tipo di relazione è **Rigida** perché le relazioni tra i membri non cambieranno nel corso del tempo.  
  
5.  Fare clic su **OK**.  
  
6.  Nel diagramma fare clic con il pulsante destro del mouse sull'attributo **Calendar Quarter** e scegliere **Nuova relazione tra attributi**.  
  
7.  Nella finestra di dialogo **Crea relazione tra attributi** l'opzione **Attributo di origine** è impostata su **Calendar Quarter**. Impostare **Attributo correlato** su **Calendar Semester**.  
  
8.  Nell'elenco **Tipo di relazione** impostare il tipo di relazione su **Rigida**.  
  
9. Fare clic su **OK**.  
  
10. Nel diagramma fare clic con il pulsante destro del mouse sull'attributo **Calendar Semester** e scegliere **Nuova relazione tra attributi**.  
  
11. Nella finestra di dialogo **Crea relazione tra attributi** l'opzione **Attributo di origine** è impostata su **Calendar Semester**. Impostare **Attributo correlato** su **Calendar Year**.  
  
12. Nell'elenco **Tipo di relazione** impostare il tipo di relazione su **Rigida**.  
  
13. Fare clic su **OK**.  
  
14. Scegliere **Salva tutti** dal menu **File**.  
  
## <a name="providing-unique-dimension-member-names"></a>Impostazione di nomi univoci per i membri di dimensione  
 In questa attività si creeranno colonne con nomi descrittivi che verranno usate dagli attributi **EnglishMonthName**, **CalendarQuarter**e **CalendarSemester** .  
  
#### <a name="to-provide-unique-dimension-member-names"></a>Per impostare nomi univoci per i membri di dimensione  
  
1.  Per passare alla vista origine dati ** [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] DW 2012** , fare doppio clic su di essa nella cartella **viste origine dati** in Esplora soluzioni.  
  
2.  Nel riquadro **tabelle** fare clic con il pulsante `Date`destro del mouse su, quindi scegliere **nuovo calcolo denominato**.  
  
3.  Nella finestra di dialogo **Crea calcolo denominato** Digitare `MonthName` nella casella **nome colonna** , quindi digitare o copiare e incollare l'istruzione seguente nella casella **espressione** :  
  
    ```  
    EnglishMonthName+' '+ CONVERT(CHAR (4), CalendarYear)  
    ```  
  
     Questa istruzione consente di concatenare il mese e l'anno per ogni mese della tabella in una nuova colonna.  
  
4.  Fare clic su **OK**.  
  
5.  Nel riquadro **tabelle** fare clic con il pulsante `Date`destro del mouse su, quindi scegliere **nuovo calcolo denominato**.  
  
6.  Nella finestra di dialogo **Crea calcolo denominato** Digitare `CalendarQuarterDesc` nella casella **nome colonna** , quindi digitare o copiare e incollare lo script SQL seguente nella casella **espressione** :  
  
    ```  
    'Q' + CONVERT(CHAR (1), CalendarQuarter) +' '+ 'CY ' +  
    CONVERT(CHAR (4), CalendarYear)  
    ```  
  
     Questo script SQL consente di concatenare il trimestre e l'anno di calendario per ogni trimestre della tabella in una nuova colonna.  
  
7.  Fare clic su **OK**.  
  
8.  Nel riquadro **tabelle** fare clic con il pulsante `Date`destro del mouse su, quindi scegliere **nuovo calcolo denominato**.  
  
9. Nella finestra di dialogo **Crea calcolo denominato** Digitare `CalendarSemesterDesc` nella casella **nome colonna** , quindi digitare o copiare e incollare lo script SQL seguente nella casella **espressione** :  
  
    ```  
    CASE  
    WHEN CalendarSemester = 1 THEN 'H1' + ' ' + 'CY' + ' '   
           + CONVERT(CHAR(4), CalendarYear)  
    ELSE  
    'H2' + ' ' + 'CY' + ' ' + CONVERT(CHAR(4), CalendarYear)  
    END  
    ```  
  
     Questo script SQL consente di concatenare il semestre e l'anno di calendario per ogni semestre della tabella in una nuova colonna.  
  
10. Fare clic su **OK**.  
  
11. Scegliere **Salva tutti** dal menu **File**.  
  
## <a name="defining-composite-keycolumns-and-setting-the-name-column"></a>Definizione della proprietà KeyColumns composta e impostazione di NameColumn  
 La proprietà **KeyColumns** contiene la colonna o le colonne che rappresentano la chiave per l'attributo. In questa attività verrà definita la proprietà **KeyColumns**composta.  
  
#### <a name="to-define-composite-keycolumns-for-the-english-month-name-attribute"></a>Per definire la proprietà KeyColumns composta per l'attributo English Month Name  
  
1.  Aprire la scheda **Struttura dimensione** per la dimensione Date.  
  
2.  Nel riquadro **Attributi** fare clic sull'attributo **English Month Name** .  
  
3.  Nella finestra **Proprietà** fare clic nel campo **KeyColumns** e sul pulsante sfoglia (**..**).  
  
4.  Nell'elenco **colonne disponibili** della finestra di dialogo **colonne chiave** selezionare la colonna **CalendarYear**, quindi fare clic sul **>** pulsante.  
  
5.  Le colonne **EnglishMonthName** e **CalendarYear** sono ora visualizzate nell'elenco **Colonne chiave** .  
  
6.  Fare clic su **OK**.  
  
7.  Per impostare la proprietà **NameColumn** dell'attributo **EnglishMonthName** , fare clic nel campo **NameColumn** nella finestra Proprietà e fare clic sul pulsante sfoglia (**...**).  
  
8.  Nell'elenco **colonna di origine** della finestra di dialogo `MonthName` **colonna nome** selezionare, quindi fare clic su **OK**.  
  
9. Scegliere **Salva tutti** dal menu **File**.  
  
#### <a name="to-define-composite-keycolumns-for-the-calendar-quarter-attribute"></a>Per definire la proprietà KeyColumns composta per l'attributo Calendar Quarter  
  
1.  Nel riquadro **Attributi** fare clic sull'attributo **Calendar Quarter** .  
  
2.  Nella finestra **Proprietà** fare clic nel campo **KeyColumns** e sul pulsante sfoglia (**..**).  
  
3.  Nell'elenco **colonne disponibili** della finestra di dialogo **colonne chiave** selezionare la colonna **CalendarYear**, quindi fare clic sul **>** pulsante.  
  
     Le colonne **CalendarQuarter** e **CalendarYear** sono ora visualizzate nell'elenco **Colonne chiave** .  
  
4.  Fare clic su **OK**.  
  
5.  Per impostare la proprietà **NameColumn** dell'attributo **Calendar Quarter** , fare clic nel campo **NameColumn** nella finestra Proprietà e fare clic sul pulsante sfoglia (**...**).  
  
6.  Nell'elenco **colonna di origine** della finestra di dialogo `CalendarQuarterDesc` **colonna nome** selezionare, quindi fare clic su **OK**.  
  
7.  Scegliere **Salva tutti** dal menu **File**.  
  
#### <a name="to-define-composite-keycolumns-for-the-calendar-semester-attribute"></a>Per definire la proprietà KeyColumns composta per l'attributo Calendar Semester  
  
1.  Nel riquadro **Attributi** fare clic sull'attributo **Calendar Semester** .  
  
2.  Nella finestra **Proprietà** fare clic nel campo **KeyColumns** e sul pulsante sfoglia (**..**).  
  
3.  Nell'elenco **Colonne disponibili** della finestra di dialogo **Colonne chiave** selezionare la colonna **CalendarYear**e fare clic sul pulsante **>** .  
  
     Le colonne **CalendarSemester** e **CalendarYear** sono ora visualizzate nell'elenco **Colonne chiave** .  
  
4.  Fare clic su **OK**.  
  
5.  Per impostare la proprietà **NameColumn** dell'attributo **Calendar Semester** , fare clic nel campo **NameColumn** nella finestra delle proprietà e fare clic sul pulsante sfoglia (**...**).  
  
6.  Nell'elenco **colonna di origine** della finestra di dialogo `CalendarSemesterDesc` **colonna nome** selezionare, quindi fare clic su **OK**.  
  
7.  Scegliere **Salva tutti** dal menu **File**.  
  
## <a name="deploying-and-viewing-the-changes"></a>Distribuzione e visualizzazione delle modifiche  
 Dopo aver modificato gli attributi e le gerarchie, prima di visualizzare le modifiche è necessario distribuirle e rielaborare gli oggetti correlati.  
  
#### <a name="to-deploy-and-view-the-changes"></a>Per distribuire e visualizzare le modifiche  
  
1.  Scegliere **Distribuisci Analysis Services Tutorial** dal menu [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]Compila **di**.  
  
2.  Dopo aver ricevuto il messaggio **distribuzione completata** , fare clic sulla scheda **esplorazione** di **Progettazione dimensioni** per la `Date` dimensione e quindi fare clic sul pulsante Riconnetti sulla barra degli strumenti della finestra di progettazione.  
  
3.  Selezionare **Calendar Quarter** nell'elenco **Gerarchia** . Controllare i membri nella gerarchia dell'attributo **Calendar Quarter** .  
  
     Si noti che i nomi dei membri della gerarchia dell'attributo **Calendar Quarter** sono più chiari e semplici da usare in quanto è stato creato un calcolo denominato da usare come nome. I membri sono ora disponibili nella gerarchia dell'attributo **Calendar Quarter** per ogni trimestre in ogni anno. I membri non sono disposti in ordine cronologico. Sono invece ordinati per trimestre e quindi per anno. Nell'attività successiva di questo argomento verrà modificato tale funzionamento in modo da ordinare i membri di questa gerarchia dell'attributo per anno e quindi per trimestre.  
  
4.  Controllare i membri delle gerarchie degli attributi **English Month Name** e **Calendar Semester** .  
  
     È possibile notare che anche i membri di queste gerarchie non sono ordinati cronologicamente. Sono invece ordinati rispettivamente per mese o per semestre e quindi per anno. Nell'attività successiva di questo argomento verrà modificato tale funzionamento in modo da cambiare il tipo di ordinamento.  
  
## <a name="changing-the-sort-order-by-modifying-composite-key-member-order"></a>Modifica del tipo di ordinamento tramite la modifica dell'ordine dei membri della chiave composta  
 In questa attività verrà modificato l'ordinamento cambiando l'ordine delle chiavi che costituiscono la chiave composta.  
  
#### <a name="to-modify-the-composite-key-member-order"></a>Per modificare l'ordine dei membri della chiave composta  
  
1.  Aprire la scheda **Struttura dimensione** di Progettazione dimensioni per la `Date` dimensione e quindi selezionare **Calendar Semester** nel riquadro **attributi** .  
  
2.  Nella finestra Proprietà controllare il valore della proprietà **OrderBy** . È impostato su **Chiave**.  
  
     I membri della gerarchia dell'attributo **Calendar Semester** vengono ordinati in base al valore della chiave. Con una chiave composta, l'ordinamento delle chiavi dei membri si basa innanzitutto sul valore della prima chiave del membro e quindi sul valore della seconda chiave. In altri termini, i membri della gerarchia dell'attributo **Calendar Semester** vengono ordinati prima in base al semestre, poi in base all'anno.  
  
3.  Nella finestra Proprietà fare clic sul pulsante con i puntini di sospensione (**...**) per cambiare il valore della proprietà **KeyColumns** .  
  
4.  Nell'elenco **Colonne chiave** della finestra di dialogo **Colonne chiave** verificare che **CalendarSemester** sia selezionato e fare clic sulla freccia a discesa per invertire l'ordine dei membri di questa chiave composta. Fare clic su **OK**.  
  
     I membri della gerarchia dell'attributo sono ora ordinati per anno e quindi per semestre.  
  
5.  Selezionare **Calendar Quarter** nel riquadro **Attributi** e fare clic sul pulsante con i puntini di sospensione (**...**) della proprietà **KeyColumns** nella finestra Proprietà.  
  
6.  Nell'elenco **Colonne chiave** della finestra di dialogo **Colonne chiave** verificare che **CalendarQuarter** sia selezionato e fare clic sulla freccia a discesa per invertire l'ordine dei membri di questa chiave composta. Fare clic su **OK**.  
  
     I membri della gerarchia dell'attributo sono ora ordinati per anno e quindi per trimestre.  
  
7.  Selezionare **English Month Name** nel riquadro **Attributi** e fare clic sul pulsante con i puntini di sospensione (**...**) della proprietà **KeyColumns** nella finestra Proprietà.  
  
8.  Nell'elenco **Colonne chiave** della finestra di dialogo **Colonne chiave** verificare che **EnglishMonthName** sia selezionato e fare clic sulla freccia a discesa per invertire l'ordine dei membri di questa chiave composta. Fare clic su **OK**.  
  
     I membri della gerarchia dell'attributo sono ora ordinati per anno e quindi per mese.  
  
9. Scegliere **Distribuisci Analysis Services Tutorial** dal menu [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]Compila **di**. Al termine della distribuzione, fare clic sulla scheda **esplorazione** in Progettazione dimensioni per la `Date` dimensione.  
  
10. Sulla barra degli strumenti della scheda **Esplorazione** fare clic sul pulsante Riconnetti.  
  
11. Controllare i membri delle gerarchie degli attributi **Calendar Quarter** e **Calendar Semester** .  
  
     Si noti che i membri di queste gerarchie sono ora ordinati cronologicamente per anno e quindi, rispettivamente, per trimestre o semestre.  
  
12. Controllare i membri della gerarchia dell'attributo **English Month Name** .  
  
     Si noti che i membri della gerarchia dell'attributo sono ora ordinati per anno e quindi alfabeticamente per mese. Questo avviene in quanto il tipo di dati per la colonna EnglishCalendarMonth nella vista origine dati è una colonna stringa basata sul tipo di dati nvarchar nel database relazionale sottostante. Per informazioni su come consentire l'ordinamento cronologico dei mesi in ogni anno, vedere [Ordinamento dei membri dell'attributo in base a un attributo secondario](lesson-4-5-sorting-attribute-members-based-on-a-secondary-attribute.md).  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Esplorazione di un cubo distribuito](lesson-3-5-browsing-the-deployed-cube.md)  
  
## <a name="see-also"></a>Vedi anche  
 [Dimensioni nei modelli multidimensionali](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
