---
title: 'Attività 1 (prerequisito): rimozione dei dati fornitore in MDS | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6f0a4287-7fd4-4f18-b7e4-a5191a9d4a3c
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 0290f033be47bec61e9ccce8465892d8cc98608c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "81484631"
---
# <a name="task-1-prerequisite-removing-supplier-data-in-mds"></a>Attività 1 (prerequisito): Rimozione dei dati fornitore in MDS
  In questa attività vengono rimossi i dati fornitore archiviati in MDS. I dati sono stati caricati manualmente usando il **componente aggiuntivo di Excel di MDS** nella lezione precedente. Tramite il pacchetto SSIS creato durante questa lezione i dati vengono caricati automaticamente in MDS. Pertanto, prima di testare il pacchetto SSIS, è necessario rimuovere i dati fornitore da MDS, la gerarchia derivata, le entità Supplier e State e creare l'entità Supplier senza alcun dato.  
  
1.  Avviare **Gestione dati master** passando a `http://localhost/MDS` o al sito Web e all'applicazione specificati durante la configurazione di MDS. Se il **Gestione dati master** aperto, fare clic su **SQL Server 2012 Master Data Services** nella parte superiore per passare alla **Home page**.  
  
2.  Fare clic su **Amministrazione sistema** nella sezione **attività amministrative** .  
  
3.  Posizionare il puntatore del mouse su **Gestisci** nel menu e fare clic su **gerarchie derivate**. Prima di eliminare le entità nel modello **Suppliers** è necessario eliminare la gerarchia derivata **SuppliersInState** .  
  
4.  Selezionare **SuppliersInState** dall'elenco **gerarchia derivata** e fare clic sul pulsante **X (Elimina)** sulla barra degli strumenti.  
  
5.  Fare clic su **OK** per confermare l'eliminazione.  
  
6.  Posizionare il puntatore del mouse su **Gestisci** nel menu e fare clic su **entità**.  
  
7.  Fare clic su **Supplier** e fare clic sul pulsante **Elimina (X)** sulla barra degli strumenti per eliminare l'entità. Fare clic su **OK** nelle finestre di messaggio.  
  
8.  Ripetere il passaggio precedente per eliminare l'entità **stato** .  
  
9. Non chiudere **Gestione dati master**.  
  
10. Passare alla finestra di Excel in cui è stato aperto il file **cleaned and Matched Suppliers. xls** . Passare alla scheda **Sheet1** in basso.  
  
11. Selezionare solo la **prima riga con le intestazioni**. Non selezionare nessun'altra riga. Si desidera creare le entità in base alle colonne di Excel, ma non si desidera caricare i dati. Pertanto, selezionare solo la prima riga con le intestazioni.  
  
12. Fare clic su **dati master** sulla barra dei menu.  
  
13. Fare clic su **Crea entità** nella barra multifunzione.  
  
14. Nella finestra di dialogo **Gestisci connessioni** , se non si visualizza la connessione al **Server MDS locale** in **connessioni esistenti**, effettuare le seguenti operazioni:  
  
    1.  Selezionare **Crea una nuova connessione**e fare clic sul pulsante **nuovo** .  
  
    2.  Nella finestra di dialogo Aggiungi nuova connessione digitare **Server MDS locale** per **Descrizione** e **http:\//localhost/MDS** per **Indirizzo server MDS**, quindi fare clic su **OK** per chiudere la finestra di dialogo.  
  
15. Nella finestra di dialogo **Gestisci connessioni** selezionare **Server MDS locale** (`http://localhost/MDS`), fare clic su **test** per testare la connessione. Fare clic su **OK** nella finestra di messaggio.  
  
16. Fare clic su **Connetti** per stabilire una connessione al server MDS.  
  
17. Nella finestra di dialogo **Crea entità** eseguire le operazioni seguenti:  
  
    1.  Verificare che l' **intervallo** sia impostato su **$1: $1**.  
  
    2.  Selezionare **Suppliers** per **modello**.  
  
    3.  Selezionare **VERSION_1** per **versione**.  
  
    4.  Digitare **Supplier** per **nome nuova entità**.  
  
    5.  Selezionare **SupplierID** per **codice**.  
  
    6.  Selezionare **Supplier Name** per **nome**.  
  
    7.  Fare clic su **OK** per creare l'entità e chiudere la finestra di dialogo.  
  
18. Chiudere **Excel** e **non salvare** il file.  
  
19. In **Gestione dati master**aggiornare il browser Internet e verificare che l'entità **Supplier** sia visualizzata nell'elenco.  
  
20. Passare al **Home page** facendo clic **SQL Server Master Data Services 2012** nella parte superiore.  
  
21. Verificare che il modello **Suppliers** sia selezionato per **Model** e **VERSION_1** sia selezionato per **Version**.  
  
22. Fare clic su **Esplora**. Si noti che l'entità **Supplier** con tutti gli attributi viene creata **senza valori**.  
  
## <a name="next-step"></a>passaggio successivo  
 [Attività 2 &#40;&#41; facoltativo: creazione di una vista sottoscrizioni MDS tramite Gestione dati master](../../2014/tutorials/task-2-optional-creating-a-mds-subscription-view-using-master-data-manager.md)  
  
  
