---
title: Aggiungere funzionalità a un'istanza di SQL Server 2014 (programma di installazione) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- feature adding [SQL Server]
- SQL Server, features
- adding features to SQL Server
ms.assetid: 97931fdc-d943-48dd-81b9-ae8b8d2c6dad
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e84867e56a66a6f35c4de6c95d7cdbc0bfd72769
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84932812"
---
# <a name="add-features-to-an-instance-of-sql-server-2014-setup"></a>Aggiungere funzionalità a un'istanza di SQL Server 2014 (programma di installazione)
  In questo argomento vengono fornite istruzioni dettagliate per aggiungere funzionalità a un'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Alcuni componenti o servizi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono specifici di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Essi sono anche noti come specifici dell'istanza. Condividono la stessa versione dell'istanza che li ospita e vengono utilizzati esclusivamente per quell'istanza. È possibile aggiungere i componenti specifici dell'istanza a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], insieme ai componenti condivisi, se non sono già installati. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 Per aggiungere funzionalità a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dal prompt dei comandi, vedere [Install SQL Server 2014 dal](install-sql-server-from-the-command-prompt.md)prompt dei comandi.  
  
## <a name="prerequisites"></a>Prerequisites  
 Prima di continuare, rivedere gli argomenti in [Pianificazione di un'installazione di SQL Server](../../sql-server/install/planning-a-sql-server-installation.md).  
  
> [!NOTE]  
>  Per le installazioni locali è necessario eseguire il programma di installazione come amministratore. Se si installa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da una condivisione remota, è necessario utilizzare un account di dominio con autorizzazioni di lettura per tale condivisione.  
  
> [!NOTE]  
>  Quando si aggiungono funzionalità a un'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], le impostazioni delle segnalazioni relative all'utilizzo delle funzionalità esistenti vengono applicate alle funzionalità aggiunte. Per modificare queste impostazioni, usare lo strumento **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , disponibile nel menu** Strumenti di configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**di** .  
  
## <a name="procedures"></a>Procedure  
  
#### <a name="to-add-features-to-an-instance-of-sscurrent"></a>Per aggiungere funzionalità a un'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
1.  Inserire il supporto di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Nella cartella radice fare doppio clic sul file setup.exe. Per eseguire l'installazione da una condivisione di rete, accedere alla cartella radice nella condivisione, quindi fare doppio clic sul file setup.exe. Se viene visualizzata la finestra di dialogo del programma di installazione di [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , [!INCLUDE[clickOK](../../includes/clickok-md.md)] per installare i prerequisiti, quindi su **Annulla** per uscire dall'installazione di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
2.  L'Installazione guidata consentirà di avviare il Centro installazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per aggiungere una nuova funzionalità a un'istanza esistente di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], fare clic su **Installazione** sulla sinistra dell'area di navigazione, quindi fare clic su **Nuova installazione autonoma di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o aggiunta di funzionalità a un'installazione esistente**.  
  
3.  Controllo configurazione sistema consentirà di eseguire un'operazione di individuazione nel computer. Per visualizzare i dettagli da verificare fare clic su **Visualizza dettagli**. Per continuare, [!INCLUDE[clickOK](../../includes/clickok-md.md)].  
  
4.  Nella pagina Aggiornamenti prodotto vengono visualizzati gli aggiornamenti più recenti sul prodotto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se non si vogliono includere gli aggiornamenti, deselezionare la casella di controllo **Includi aggiornamenti prodotto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** . Se non viene individuato alcun aggiornamento del prodotto, durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] questa pagina non viene visualizzata e viene aperta automaticamente la pagina **Installazione dei file di installazione** .  
  
5.  Nella pagina Installa i file di installazione viene mostrato lo stato di avanzamento del download, dell'estrazione e dell'installazione dei file di installazione. Se viene individuato un aggiornamento per il programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e ne viene specificata l'inclusione, verrà installato anche questo aggiornamento. Fare clic su **Installa** per installare i file di supporto per l'installazione.  
  
6.  Controllo configurazione sistema consentirà di verificare lo stato del sistema del computer prima che l'installazione continui.  
  
7.  Nella pagina Tipo di installazione selezionare l'opzione **Aggiungi funzionalità a un'istanza esistente di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]** e quindi selezionare l'istanza da aggiornare.  
  
8.  Nella pagina Selezione funzionalità selezionare i componenti per l'installazione. Una volta selezionato il nome della funzionalità desiderata, nel riquadro a destra verrà visualizzata una descrizione per ogni gruppo di componenti. È possibile selezionare qualsiasi combinazione di caselle di controllo. Per ulteriori informazioni, vedere [edizioni e componenti di SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md). Ogni componente può essere installato una sola volta in un'istanza specificata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per installare più componenti, è necessario installare un'istanza aggiuntiva di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     I prerequisiti per le funzionalità selezionate vengono visualizzati nel riquadro di destra. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verranno installati i prerequisiti che non sono stati ancora installati durante la procedura di installazione descritta più avanti in questo argomento.  
  
     Controllo configurazione sistema consentirà di verificare lo stato del sistema del computer prima che l'installazione continui. Fare clic su **Avanti** per continuare.  
  
9. Nella pagina Requisiti di spazio su disco viene calcolato lo spazio su disco necessario per le funzionalità specificate e vengono confrontati i requisiti con lo spazio su disco disponibile nel computer in cui è in esecuzione il programma di installazione.  
  
10. Il flusso di lavoro relativo alla parte rimanente di questo argomento dipende dalle funzionalità specificate per l'installazione. Le pagine visualizzate dipendono dalle selezioni effettuate.  
  
11. Nella pagina Configurazione server - Account di servizio specificare gli account di accesso per i servizi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. I servizi effettivamente configurati in questa pagina dipendono dalle caratteristiche selezionate per l'installazione.  
  
     È possibile assegnare lo stesso account di accesso a tutti i servizi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oppure configurare singolarmente l'account di ogni servizio. È inoltre possibile specificare se i servizi verranno avviati automaticamente, manualmente o se sono disabilitati. [!INCLUDE[msCoName](../../includes/msconame-md.md)] consiglia di configurare gli account del servizio singolarmente per fornire privilegi minimi per ogni servizio, in modo che i servizi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abbiano le autorizzazioni minime necessarie per completare le attività. Per altre informazioni, vedere [Configurazione Server - Account di servizio](../../sql-server/install/server-configuration-service-accounts.md) e [Configurare account di servizio e autorizzazioni di Windows](../configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
     Per specificare lo stesso account di accesso per tutti gli account del servizio nell'istanza corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], immettere le credenziali nei campi visualizzati nella parte inferiore della pagina.  
  
     **Nota sulla sicurezza** : [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
     Dopo aver specificato le informazioni di accesso per i servizi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , fare clic su **Avanti**.  
  
12. Usare la scheda **Configurazione server - Regole di confronto** per specificare regole di confronto non predefinite per il [!INCLUDE[ssDE](../../includes/ssde-md.md)] e [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Per altre informazioni, vedere [Configurazione del server - Regole di confronto](../../sql-server/install/server-configuration-collation.md).  
  
13. Utilizzare la pagina Configurazione [!INCLUDE[ssDE](../../includes/ssde-md.md)] - Provisioning account per specificare gli elementi seguenti:  
  
    -   Modalità di sicurezza: selezionare l'autenticazione di Windows o l'autenticazione mista per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se si seleziona l'autenticazione Modalità mista, è necessario specificare una password complessa per l'account amministratore di sistema [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] predefinito.  
  
         Quando viene stabilita la connessione tra un dispositivo e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il meccanismo di sicurezza è lo stesso sia in modalità mista che di autenticazione di Windows. Per ulteriori informazioni, vedere [motore di database configurazione-provisioning dell'account](../../sql-server/install/database-engine-configuration-account-provisioning.md).  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Amministratori: è necessario specificare almeno un amministratore di sistema per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per aggiungere l'account usato per eseguire il programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , fare clic su **Aggiungi utente corrente**. Per aggiungere o rimuovere account dall'elenco degli amministratori di sistema, fare clic su **Aggiungi** o **Rimuovi**, quindi modificare l'elenco di utenti, gruppi o computer con privilegi di amministratore per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per ulteriori informazioni, vedere [motore di database configurazione-provisioning dell'account](../../sql-server/install/database-engine-configuration-account-provisioning.md).  
  
     Dopo aver modificato l'elenco, fare clic su **OK**. Verificare l'elenco di amministratori nella finestra di dialogo di configurazione. Quando l'elenco è completo, fare clic su **Avanti**.  
  
14. Utilizzare la pagina Configurazione [!INCLUDE[ssDE](../../includes/ssde-md.md)] - Directory dati per specificare directory di installazione non predefinite. Per eseguire l'installazione in directory predefinite, fare clic su **Avanti**.  
  
    > [!IMPORTANT]  
    >  Se si specificano directory di installazione non predefinite, verificare che le cartelle di installazione siano univoche per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Nessuna delle directory presenti in questa finestra di dialogo deve essere condivisa con le directory di altre istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Per altre informazioni, vedere [Configurazione del motore di database - Directory dati](../../sql-server/install/database-engine-configuration-data-directories.md).  
  
15. Utilizzare la pagina Configurazione [!INCLUDE[ssDE](../../includes/ssde-md.md)] - FILESTREAM per abilitare la funzione FILESTREAM per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni su FILESTREAM, vedere [Configurazione del motore di database - Filestream](../../sql-server/install/database-engine-configuration-filestream.md). Scegliere Avanti per continuare.  
  
16. Usare la pagina Configurazione [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] - Provisioning account per specificare la modalità server e gli utenti o gli account che disporranno delle autorizzazioni di amministratore per [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. La modalità server determina quali sottosistemi di memoria e archiviazione vengono utilizzati nel server. Tipi di soluzione diversi eseguiti nelle modalità server diverse. Se si intende eseguire database di cubi multidimensionali nel server, scegliere l'opzione predefinita, vale a dire quella relativa alla modalità server multidimensionale e di data mining. Relativamente alle autorizzazioni di amministratore, è necessario specificare almeno un amministratore di sistema per [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Per aggiungere l'account usato per eseguire il programma di installazione di SQL Server, fare clic su **Aggiungi utente corrente**. Per aggiungere o rimuovere account dall'elenco degli amministratori di sistema, fare clic su **Aggiungi** o **Rimuovi**, quindi modificare l'elenco di utenti, gruppi o computer che disporranno di privilegi di amministratore per [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Per altre informazioni sulle autorizzazioni della modalità server e amministratore, vedere [Configurazione di Analysis Services - Provisioning account](../../sql-server/install/analysis-services-configuration-account-provisioning.md).  
  
     Dopo aver modificato l'elenco, fare clic su **OK**. Verificare l'elenco di amministratori nella finestra di dialogo di configurazione. Quando l'elenco è completo, fare clic su **Avanti**.  
  
17. Utilizzare la pagina Configurazione [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] - Directory dati per specificare directory di installazione non predefinite. Per eseguire l'installazione in directory predefinite, fare clic su **Avanti**.  
  
    > [!IMPORTANT]  
    >  Se si specificano directory di installazione non predefinite, verificare che le cartelle di installazione siano univoche per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Nessuna delle directory presenti in questa finestra di dialogo deve essere condivisa con le directory di altre istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Per altre informazioni, vedere [Configurazione di Analysis Services - Directory dati](../../sql-server/install/analysis-services-configuration-data-directories.md).  
  
18. Utilizzare la pagina di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per specificare il tipo di installazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] da creare. Per altre informazioni sulle modalità di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vedere [Opzioni di configurazione di Reporting Services &#40;SSRS&#41;](../../sql-server/install/reporting-services-configuration-options-ssrs.md).  
  
19. Utilizzare la pagina di configurazione del controller di Riesecuzione distribuita per specificare gli utenti a cui si desidera concedere autorizzazioni amministrative per il servizio controller di Riesecuzione distribuita. Gli utenti che dispongono di autorizzazioni amministrative disporranno di accesso illimitato al servizio controller di Riesecuzione distribuita.  
  
     Fare clic su **Aggiungi utente corrente** per aggiungere gli utenti a cui concedere le autorizzazioni di accesso per il servizio controller di Riesecuzione distribuita. Fare clic sul pulsante **Aggiungi** per aggiungere autorizzazioni di accesso per il servizio controller di Riesecuzione distribuita. Fare clic sul pulsante **Rimuovi** per rimuovere le autorizzazioni di accesso dal servizio controller di Riesecuzione distribuita.  
  
     Scegliere **Avanti**per continuare.  
  
20. Utilizzare la pagina di configurazione del client Riesecuzione distribuita per specificare gli utenti a cui si desidera concedere autorizzazioni amministrative per il servizio client Riesecuzione distribuita. Gli utenti che dispongono di autorizzazioni amministrative disporranno di accesso illimitato al servizio client Riesecuzione distribuita.  
  
     Il **nome del controller** è un parametro facoltativo e il valore predefinito è \<*blank*> . Immettere il nome del controller che il computer client comunicherà con per il servizio client Riesecuzione distribuita. Tenere presente quanto segue:  
  
    -   Se è già stato configurato un controller, immettere il nome del controller durante la configurazione di ciascuno client.  
  
    -   In caso contrario, è possibile lasciare vuoto il nome del controller. Tuttavia, è necessario immettere manualmente il nome del controller nel file **configurazione client** .  
  
     Specificare la **Directory di lavoro** per il servizio client Riesecuzione distribuita. La directory di lavoro predefinita è \<*drive letter*> : \Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \DReplayClient\WorkingDir \\ .  
  
     Specificare la **Directory dei risultati** per il servizio client Riesecuzione distribuita. La directory dei risultati predefinita è \<*drive letter*> : \Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \DReplayClient\ResultDir \\ .  
  
     Scegliere **Avanti**per continuare.  
  
21. Nella pagina Segnalazione errori specificare le informazioni che si desidera inviare a [!INCLUDE[msCoName](../../includes/msconame-md.md)] per contribuire a migliorare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per impostazione predefinita, l'opzione per la segnalazione di errori è abilitata.  
  
22. Controllo configurazione sistema eseguirà uno o più set di regole per convalidare la configurazione del computer con le caratteristiche di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specificate.  
  
23. Nella pagina Inizio installazione è presente una visualizzazione albero delle opzioni specificate durante l'installazione. In questa pagina, tramite il programma di installazione vengono indicati l'eventuale abilitazione o disabilitazione della funzionalità di aggiornamento del prodotto e la versione dell'aggiornamento finale. Dopo aver selezionato l'installazione, tramite il programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verranno installati prima i prerequisiti obbligatori per le funzionalità selezionate e successivamente la funzionalità.  
  
24. Durante l'installazione, nella pagina Stato dell'installazione è possibile monitorare lo stato di avanzamento del processo.  
  
25. Al termine dell'installazione nella pagina Operazione completata viene visualizzato un collegamento al file di log di riepilogo del processo di installazione e ad altre note importanti. Per completare il processo di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , fare clic su **Chiudi**.  
  
26. Se viene richiesto, riavviare il computer. È importante leggere il messaggio visualizzato nell'Installazione guidata al termine dell'installazione. Per altre informazioni sui file di log del programma di installazione, vedere [Visualizzare e leggere i file di log del programma di installazione di SQL Server](view-and-read-sql-server-setup-log-files.md).  
  
## <a name="next-steps"></a>Passaggi successivi  
 Configurare l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Per ridurre la superficie di attacco di un sistema, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono installati e attivati in modo selettivo i servizi e le funzionalità principali. Per ulteriori informazioni, vedere [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare e leggere i file di log del programma di installazione di SQL Server](view-and-read-sql-server-setup-log-files.md)   
 [Convalidare un'installazione di SQL Server](validate-a-sql-server-installation.md)   
 [Eliminare un'installazione di SQL Server 2014](repair-a-failed-sql-server-installation.md)   
 [Eseguire l'aggiornamento a SQL Server 2014 usando l'installazione guidata &#40;&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md)   
 [Installazione di SQL Server 2014 dal prompt dei comandi](install-sql-server-from-the-command-prompt.md)  
  
  
