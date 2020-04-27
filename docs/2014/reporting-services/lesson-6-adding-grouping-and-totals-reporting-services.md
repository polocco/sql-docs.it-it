---
title: 'Lezione 6: Aggiunta di gruppi e totali (Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e3d61228-2aa4-42cc-955e-602dbf3406a7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5607dfb046e7f50eb3a015e1f4f13711256435a8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108409"
---
# <a name="lesson-6-adding-grouping-and-totals-reporting-services"></a>Lezione 6: Aggiunta di gruppi e totali (Reporting Services)
  È possibile aggiungere gruppi e totali al report per organizzare e riepilogare i dati.  
  
 Per informazioni sull'aggiunta dei totali in esecuzione ai report, vedere: [aggiunta di totali ai report di Reporting Services (SSRS)](https://www.tutorialgateway.org/add-total-and-subtotal-to-ssrs-report/).  
  
 **Contenuto dell'argomento:**  
  
-   [Per raggruppare i dati in un report](#bkmk_groupdata)  
  
-   [Per aggiungere totali a un report](#bkmk_addtotals)  
  
-   [Per aggiungere un totale giornaliero a un report](#bkmk_adddailytotal)  
  
-   [Per aggiungere un totale complessivo a un report](#bkmk_addgrandtotal)  
  
-   [Per pubblicare il report nel server di report (facoltativo)](#bkmk_publishreport)  
  
##  <a name="to-group-data-in-a-report"></a><a name="bkmk_groupdata"></a>Per raggruppare i dati in un report  
  
1.  Fare clic sulla scheda **Progettazione** .  
  
2.  Se il riquadro **gruppi di righe** non è visualizzato, fare clic con il pulsante destro del mouse sull'area di progettazione e scegliere **Visualizza** , quindi fare clic su **raggruppamento**.  
  
3.  Dal riquadro **Dati report** trascinare il campo `Date` nel riquadro **Gruppi di righe**. Posizionarlo al di sopra della riga **(Dettagli)**.  
  
     L'handle di riga contiene ora una parentesi quadra per mostrare un gruppo. La tabella presenta ora due colonne Date, una su ogni lato di una linea verticale tratteggiata.  
  
     ![](../../2014/tutorials/media/rs-basictablegroups1design.gif "rs_BasicTableGroups1Design")  
  
4.  Dal riquadro **Dati report** trascinare il campo `Order` nel riquadro **Gruppi di righe**. Posizionarlo al di sotto di Date e al di sopra di **(Dettagli)**.  
  
     L'handle di riga contiene ora due parentesi quadre per mostrare due gruppi. La tabella include ora anche `Order` due colonne.  
  
5.  Eliminare le colonne Date e Order originali a **destra** della linea doppia. Verranno rimossi i singoli valori dei record in modo da visualizzare solo il valore del gruppo. Selezionare gli handle delle due colonne, fare clic con il pulsante destro del mouse e scegliere **Elimina colonne**.  
  
     ![Selezione colonne da eliminare](../../2014/tutorials/media/rs-basictablegroupsdeletecols.gif "Selezione colonne da eliminare")  
  
     È possibile formattare nuovamente le intestazioni di colonna e la data.  
  
6.  Per visualizzare un'anteprima del report, passare alla scheda **Anteprima** . Il risultato dovrebbe essere simile a quanto illustrato nella figura seguente:  
  
     ![Tabella raggruppata per data e quindi per numero di ordine](../../2014/tutorials/media/rs-basictablegroupspreview.gif "Tabella raggruppata per data e quindi per numero di ordine")  
  
##  <a name="to-add-totals-to-a-report"></a><a name="bkmk_addtotals"></a>Per aggiungere totali a un report  
  
1.  Passare alla Visualizzazione della struttura.  
  
2.  Fare clic con il pulsante destro del mouse sulla cella dell'area dati contenente il campo `[LineTotal]`e fare clic su **Aggiungi totale**.  
  
     Verrà aggiunta una riga con una somma degli importi di tutti gli ordini.  
  
3.  Fare clic con il pulsante destro del mouse sulla cella contenente il campo `[Qty]`e fare clic su **Aggiungi totale**.  
  
     Verrà aggiunta una somma delle quantità di tutti gli ordini alla riga dei totali.  
  
4.  Nella cella vuota a sinistra di `Sum[Qty]`digitare l'etichetta "**Order Total"**.  
  
5.  È possibile aggiungere un colore di sfondo alla riga dei totali. Selezionare le due celle della somma e la cella dell'etichetta.  
  
6.  Nel menu **Formato** selezionare **Colore di sfondo**, fare clic su **Grigio chiaro**e scegliere **OK**.  
  
     ![Visualizzazione Progettazione: tabella di base con totale degli ordini](../../2014/tutorials/media/rs-basictablesumlinetotaldesign.gif "Visualizzazione Progettazione: tabella di base con totale degli ordini")  
  
##  <a name="to-add-a-daily-total-to-a-report"></a><a name="bkmk_adddailytotal"></a>Per aggiungere un totale giornaliero a un report  
  
1.  Fare clic con il pulsante destro del mouse sulla cella Order , scegliere **Aggiungi totale**e quindi fare clic su **Dopo**.  
  
     Viene aggiunta una nuova riga contenente le somme della quantità e del dollaro per ogni giorno e l'etichetta "**Total**" nella colonna Order.  
  
2.  Digitare la parola **Daily** prima della parola **Total** nella stessa cella in modo da definire la frase **Daily Total**.  
  
3.  Selezionare la cella **Daily Total** , le due celle **Sum** e la cella vuota compresa tra di esse.  
  
4.  Nel menu **Formato** selezionare **Colore di sfondo**, fare clic su **Arancione**e scegliere **OK**.  
  
     ![](../../2014/tutorials/media/rs-basictablesumdaytotaldesign.gif "rs_BasicTableSumDayTotalDesign")  
  
##  <a name="to-add-a-grand-total-to-a-report"></a><a name="bkmk_addgrandtotal"></a>Per aggiungere un totale complessivo a un report  
  
1.  Fare clic con il pulsante destro del mouse sulla cella Date, scegliere **Aggiungi totale**e quindi fare clic su **Dopo**.  
  
     Viene aggiunta una nuova riga contenente le somme della quantità e del dollaro per l'intero report e l'etichetta **Total** nella `Date` colonna.  
  
2.  Digitare la parola **Grand** prima della parola **Total** nella stessa cella in modo da definire la frase **Grand Total**.  
  
3.  Selezionare la cella **Grand Total** , le due celle **Sum** e le celle vuote comprese tra di esse.  
  
4.  Nel menu **Formato** selezionare **Colore di sfondo**, fare clic su **Azzurro**e scegliere **OK**.  
  
     ![Visualizzazione Progettazione: totale complessivo in una tabella di base](../../2014/tutorials/media/rs-basictablesumgrandtotaldesign.gif "Visualizzazione Progettazione: totale complessivo in una tabella di base")  
  
5.  Fare clic su Anteprima.  
  
     L'ultima pagina dovrebbe essere simile alla seguente:  
  
     ![Anteprima: tabella di base con totale complessivo](../../2014/tutorials/media/rs-basictablesumgrandtotalpreview.gif "Anteprima: tabella di base con totale complessivo")  
  
##  <a name="to-publish-the-report-to-the-report-server-optional"></a><a name="bkmk_publishreport"></a>Per pubblicare il report nel server di report (facoltativo)  
  
1.  Un passaggio facoltativo consiste nel pubblicare il report completato nel server di report in modalità nativa in modo che sia possibile visualizzare il report da Gestione report.  
  
2.  Sulla barra degli strumenti fare clic su **Progetto** , quindi scegliere **Proprietà tutorial**.  
  
3.  In **TargetServerURL** Digitare il nome del server di report, ad esempio **http://\<nomeserver>/ReportServer**  
  
4.  Fare clic su **OK**.  
  
5.  Sulla barra degli strumenti fare clic su **Compila** , quindi scegliere **Distribuisci Tutorial**.  
  
     Se viene visualizzato un messaggio simile al seguente nella finestra di output, la distribuzione è stata completata correttamente.  
  
    > ------ Compilazione avviata - Progetto: tutorial, Configurazione: Debug ------'Sales Orders.rdl' verrà ignorato. L'elemento è aggiornato. Compilazione completata--0 errori, 0 avvisi------distribuzione avviata: progetto: esercitazione, configurazione: debug------distribuzione nel\<nome del server http://> report/reportserverDeploying '/tutorial/Sales Orders '. Distribuzione completata--0 errori, 0 avvisi = = = = = = = = = = = compilazione: 1 riuscite o aggiornate, 0 non riuscite, 0 ignorate = = = = = = = = = = = = = = = = = = = = = = = = = = = =  
  
     Se viene visualizzato un messaggio di errore simile al seguente, verificare di disporre delle autorizzazione per il server di report e di aver avviato [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] con privilegi di amministratore.  
  
    > "Le autorizzazioni concesse all'utente ' XXXXXXXX\\<il nome\>utente ' non sono sufficienti per eseguire questa operazione"  
  
6.  Avviare Gestione report con privilegi di amministratore, ad esempio, fare clic con il pulsante destro del mouse sull'icona di Internet Explorer e scegliere **Esegui come amministratore**.  
  
     Selezionare l'URL Gestione report, ad esempio `http://<server name>/reports`.  
  
7.  Selezionare la cartella contenente il report e fare clic sul nome del report `Sales Orders` per visualizzare il report visualizzabile nel browser.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Questo passaggio conclude l'esercitazione relativa alla creazione di un report tabella semplice.  
  
## <a name="see-also"></a>Vedi anche  
 [Filtro, raggruppamento e ordinamento di dati &#40;Generatore report e SSRS&#41;](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
