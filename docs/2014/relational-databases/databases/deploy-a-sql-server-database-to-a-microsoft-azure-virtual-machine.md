---
title: Distribuire un database di SQL Server a una macchina virtuale di Microsoft Azure | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.deploymentwizard.deploymentsettings.f1
- sql12.swb.deploymentwizard.progress.f1
- sql11.swb.usevmdialog.f1
- sql11.swb.deploymentwizard.f1
- sql12.swb.deploymentwizard.azuresignin.f1
- sql11.swb.deploymentwizard.summary.f1
- sql11.swb.deploymentwizard.azuresignin.f1
- sql12.swb.deploymentwizard.f1
- sql12.swb.sqlvmdialog.f1
- sql11.swb.newvmdialog.f1
- sql12.swb.deploymentwizard.results.f1
- sql11.swb.deploymentwizard.progress.f1
- sql12.swb.newvmdialog.f1
- sql12.swb.deploymentwizard.sourcesettings.f1
- sql12.swb.usevmdialog.f1
- sql11.swb.deploymentwizard.sourcesettings.f1
- sql11.swb.deploymentwizard.results.f1
- sql12.swb.deploymentwizard.summary.f1
- sql11.swb.deploymentwizard.deploymentsettings.f1
helpviewer_keywords:
- Deploy a database
- Deploy to Azure VM
- Migrate to Azure
- Azure virtual machine
- Migrate to Azure VM
- Migrate to the cloud
- SQL Server Management Studio
- SSMS
- Deploy database wizard
- Deploy a SQL Server database to Azure
- Azure VM
ms.assetid: 5e82e66a-262e-4d4f-aa89-39cb62696d06
author: stevestein
ms.author: sstein
ms.openlocfilehash: 085f8ae1699e6a7bc1ceecb31075dff83d2b79ea
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84970045"
---
# <a name="deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine"></a>Distribuire un database di SQL Server a una macchina virtuale di Microsoft Azure
  Usare la procedura guidata **Distribuisci un database di SQL Server in una** macchina virtuale di Azure per distribuire un database da un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in una macchina virtuale (VM) di Azure. La procedura guidata usa un'operazione di backup completo del database, pertanto copia sempre lo schema completo del database e i dati da un database utente SQL Server. La procedura guidata esegue inoltre tutta la configurazione della macchina virtuale di Azure automaticamente, pertanto non sono necessarie operazioni preliminari per la configurazione della VM.  
  
 Non è possibile usare la procedura guidata per i backup differenziali perché non sovrascrive un database esistente avente lo stesso nome di database. Per sostituire un database esistente sulla VM, è innanzitutto necessario eliminare il database esistente o modificare il nome del database. Se si verifica un conflitto di denominazione tra il nome del database per un'operazione di distribuzione in transito e un database esistente sulla VM, la procedura guidata suggerirà un nome di database aggiunto per il database in transito per consentire il completamento dell'operazione.  
  
##  <a name="before-you-begin"></a><a name="before_you_begin"></a> Prima di iniziare  
 Per completare questa procedura guidata, è necessario essere in grado di fornire le informazioni indicate di seguito e avere configurato le seguenti impostazioni:  
  
-   I dettagli di account Microsoft associati alla sottoscrizione di Azure.  
  
-   Profilo di pubblicazione di Azure.  
  
    > [!CAUTION]  
    >  SQL Server supporta attualmente la versione del profilo di pubblicazione 2.0. Per scaricare la versione supportata del profilo di pubblicazione, vedere [Download del profilo di pubblicazione 2.0](https://go.microsoft.com/fwlink/?LinkId=396421).  
  
-   Il certificato di gestione caricato nella sottoscrizione di Azure.  
  
-   Il certificato di gestione salvato nell'archivio certificati personale sul computer in cui viene eseguita la procedura guidata.  
  
-   È necessario disporre di un percorso di archiviazione temporaneo nel computer in cui è ospitato il database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Il percorso di archiviazione temporaneo deve essere disponibile nel computer in cui viene eseguita la procedura guidata.  
  
-   Se si distribuisce il database a un macchina virtuale esistente, l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve essere configurata per rimanere in attesa su una porta TCP/IP.  
  
-   Una macchina virtuale o un'immagine della raccolta di Azure che si intende usare per la creazione della macchina virtuale deve avere la SQL Server adattatore del cloud configurata e in esecuzione.  
  
-   È necessario configurare un endpoint aperto per il SQL Server adattatore del cloud sul gateway di Azure con la porta privata 11435.  
  
 Inoltre, se si prevede di distribuire il database in una macchina virtuale di Azure esistente, è necessario essere in grado di fornire:  
  
-   Nome DNS del servizio cloud che ospita la macchina virtuale.  
  
-   Credenziali dell'amministratore per la macchina virtuale.  
  
-   Credenziali con privilegi dell'operatore di backup nel database che si desidera distribuire, dall'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]di origine.  
  
 Per altre informazioni sull'esecuzione di SQL Server in macchine virtuali di Azure, vedere [preparazione della migrazione a SQL Server in macchine virtuali di Azure](https://msdn.microsoft.com/library/dn133142.aspx).  
  
 Nei computer che eseguono sistemi operativi Windows Server, è necessario usare le seguenti impostazioni di configurazione per eseguire questa procedura guidata:  
  
-   Disabilitare la configurazione della sicurezza avanzata: usare Server Manager > Server locale per impostare la configurazione della sicurezza avanzata di Internet Explorer (ESC) su **DISATTIVATO**.  
  
-   Abilitare JavaScript: Internet Explorer > Opzioni Internet > Sicurezza > Livello personalizzato > Esecuzione script > Esecuzione script attivo: **Attiva**.  
  
###  <a name="limitations-and-restrictions"></a><a name="limitations"></a> Limitazioni e restrizioni  
 Il limite per le dimensioni del database per questa operazione è di 1 TB.  
  
 Questa funzionalità di distribuzione è disponibile in SQL Server Management Studio per [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
 Questa funzionalità di distribuzione è destinata solo ai database utente. La distribuzione dei database di sistema non è supportata.  
  
 La funzionalità di distribuzione non supporta i servizi ospitati associati a un gruppo di affinità. Ad esempio, gli account di archiviazione associati a un gruppo di affinità non possono essere selezionati per l'uso nella pagina **Impostazioni di distribuzione** di questa procedura guidata.  
  
 La versione di SQL Server nella macchina virtuale deve essere uguale o successiva alla versione di SQL Server di origine. SQL Server versioni del database che possono essere distribuite in una macchina virtuale di Azure tramite questa procedura guidata:  
  
-   SQL Server 2008  
  
-   SQL Server 2008 R2  
  
-   SQL Server 2012  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
 SQL Server le versioni di database in esecuzione in un database di macchine virtuali di Azure possono essere distribuite in:  
  
-   SQL Server 2012  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
 Se si verifica un conflitto di denominazione tra il nome del database per un'operazione di distribuzione in transito e un database esistente sulla VM, la procedura guidata suggerirà un nome di database aggiunto per il database in transito per consentire il completamento dell'operazione.  
  
###  <a name="considerations-for-deploying-a-filestream-enabled-database-to-an-azure-vm"></a><a name="filestream"></a> Considerazioni per la distribuzione di un database abilitato per FILESTREAM in una macchina virtuale di Azure  
 Tenere presenti le linee guida e le limitazioni seguenti per la distribuzione di database con BLOB archiviati in oggetti FILESTREAM:  
  
-   La funzionalità di distribuzione non permette di distribuire un database abilitato per FILESTREAM in una nuova macchina virtuale. Se FILESTREAM non è abilitato nella macchina virtuale prima di eseguire la procedura guidata, l'operazione di ripristino del database avrà esito negativo e l'operazione della procedura guidata non sarà completata correttamente. Per distribuire correttamente un database che usa FILESTREAM, abilitare FILESTREAM nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nella macchina virtuale host prima di avviare la procedura guidata. Per altre informazioni, vedere [FILESTREAM (SQL Server)](https://msdn.microsoft.com/library/gg471497.aspx).  
  
-   Se il database usa OLTP in memoria, è possibile distribuirlo in una macchina virtuale di Azure senza apportare alcuna modifica al database. Per altre informazioni, vedere [OLTP in memoria (ottimizzazione per la memoria)](https://msdn.microsoft.com/library/dn133186\(SQL.120\).aspx).  
  
###  <a name="considerations-for-geographic-distribution-of-assets"></a><a name="geography"></a>Considerazioni sulla distribuzione geografica delle risorse  
 Si noti che le risorse seguenti devono essere collocate nella stessa area geografica:  
  
-   Servizio cloud  
  
-   Ubicazione della macchina virtuale  
  
-   Servizio di archiviazione su disco di dati  
  
 Se le risorse elencate sopra non si trovano nella stessa area geografica, non sarà possibile completare correttamente la procedura guidata.  
  
###  <a name="wizard-configuration-settings"></a><a name="configuration_settings"></a> Impostazioni di configurazione della procedura guidata  
 Usare i dettagli di configurazione seguenti per modificare le impostazioni per una distribuzione del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in una macchina virtuale di Azure.  
  
-   **Percorso predefinito per il file di configurazione** - %LOCALAPPDATA%\SQL Server\Deploy to SQL in WA VM\DeploymentSettings.xml  
  
-   **Struttura dei file di configurazione**  
  
    -   \<DeploymentSettings>  
  
        -   <OtherSettings  
  
            -   TraceLevel = "debug"\<!-- Logging level -->  
  
            -   BackupPath = " \\ \\ [nome server] \\ [volume] \\ "\<!-- The last used path for backup. Used as default in the wizard. -->  
  
            -   CleanupDisabled = false/>\<!-- Wizard will not delete intermediate files and Azure objects (VM, CS, SA). -->  
  
        -   <PublishProfile\<!-- The last used publish profile information. -->  
  
            -   Certificate = "12A34B567890123ABCD4EF567A8"\<!-- The certificate for use in the wizard. -->  
  
            -   Subscription = "1a2b34c5-67d8-90EF-AB12-xxxxxxxxxxxxx"\<!-- The subscription for use in the wizard. -->  
  
            -   Nome = "sottoscrizione personale"\<!-- The name of the subscription. -->  
  
            -   Publisher="" />  
  
    -   \</DeploymentSettings>  
  
 **Valori del file di configurazione**  
  
###  <a name="permissions"></a><a name="permissions"></a> Autorizzazioni  
 Il database distribuito deve essere in uno stato normale e accessibile per l'account utente che esegue la procedura guidata. L'account utente deve disporre delle autorizzazioni per eseguire un'operazione di backup.  
  
##  <a name="using-the-deploy-database-to-azure-vm-wizard"></a><a name="launch_wizard"></a>Uso della procedura guidata Distribuisci database in una macchina virtuale di Azure  
 **Per avviare la procedura guidata, effettuare i passaggi seguenti:**  
  
1.  Usare SQL Server Management Studio per connettere l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] al database che si desidera distribuire.  
  
2.  In **Esplora oggetti**espandere il nome dell'istanza, quindi il nodo **Database** .  
  
3.  Fare clic con il pulsante destro del mouse sul database che si desidera distribuire, selezionare **attività**, quindi scegliere **Distribuisci database in macchina virtuale di Azure.**  
  

  
##  <a name="introduction-page"></a><a name="Introduction"></a> Pagina Introduzione  
 Questa pagina descrive la procedura guidata **Distribuisci un database di SQL Server in una macchina virtuale di Azure** .  
  
 **Opzioni**  
  
-   **Non visualizzare più questa pagina** - Selezionare questa casella di controllo per evitare che la pagina Introduzione venga visualizzata nuovamente in futuro.  
  
-   **Avanti** : passa alla pagina **Impostazioni di origine** .  
  
-   **Annulla** : Annulla l'operazione e chiude la procedura guidata.  
  
-   **Guida** : avvia l'argomento della Guida di MSDN per la procedura guidata.  
  
##  <a name="source-settings"></a><a name="Source_settings"></a>Impostazioni di origine  
 Usare questa pagina per connettersi all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che ospita il database da distribuire nella macchina virtuale di Azure. Verrà inoltre specificato un percorso temporaneo per i file da salvare dal computer locale prima che vengano trasferiti in Azure. Può essere un percorso di rete condiviso.  
  
 **Opzioni**  
  
-   Fare clic su **Connetti** e quindi specificare i dettagli della connessione per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che ospita il database da distribuire.  
  
-   Usare l'elenco a discesa **Selezione database** per specificare il database da distribuire.  
  
-   Nel campo **altre impostazioni** specificare una cartella condivisa che sarà accessibile al servizio VM di Azure.  
  
##  <a name="azure-sign-in"></a><a name="Azure_sign-in"></a>Accesso ad Azure  
 Usare questa pagina per connettersi ad Azure e fornire il certificato di gestione o i dettagli del profilo di pubblicazione.  
  
 **Opzioni**  
  
-   **Certificato di gestione** : usare questa opzione per specificare un certificato dall'archivio certificati locale corrispondente al certificato di gestione di Azure.  
  
-   **Profilo di pubblicazione** : usare questa opzione se si dispone già di un profilo di pubblicazione scaricato nel computer.  
  
-   **Accedi** : usare questa opzione per accedere ad Azure usando un account Microsoft, ad esempio un account Live ID o Hotmail, per generare e scaricare un nuovo certificato di gestione. Si noti che il numero di certificati per ogni sottoscrizione è limitato.  
  
-   **Sottoscrizione** : selezionare, digitare o incollare l'ID sottoscrizione di Azure corrispondente al certificato di gestione dall'archivio certificati locale o da un profilo di pubblicazione.  
  
##  <a name="deployment-settings-page"></a><a name="Deployment_settings"></a>Pagina Impostazioni distribuzione  
 Usare questa pagina per specificare il server di destinazione e fornire i dettagli sul nuovo database.  
  
 **Opzioni**  
  
-   **Macchina virtuale di Azure** : specificare i dettagli della macchina virtuale che ospiterà il database di SQL Server:  
  
-   **Nome servizio cloud** : specificare il nome del servizio che ospita la macchina virtuale. Per creare un nuovo servizio cloud, specificare un nome per il nuovo servizio cloud.  
  
-   **Nome macchina virtuale** : specificare il nome della macchina virtuale che ospiterà il database di SQL Server. Per creare una nuova macchina virtuale di Azure, specificare un nome per la nuova macchina virtuale.  
  
-   **Impostazioni** : usare il pulsante impostazioni per creare una nuova macchina virtuale per ospitare il database di SQL Server. Se si usa una macchina virtuale esistente, le informazioni immesse saranno usate per autenticare le credenziali.  
  
-   **Account di archiviazione** : selezionare l'account di archiviazione dall'elenco a discesa. Per creare un nuovo account di archiviazione, specificare un nome per il nuovo account. Si noti che gli account di archiviazione associati a un gruppo di affinità non saranno disponibili nell'elenco a discesa.  
  
-   **Database di destinazione** : specificare i dettagli per il database di destinazione.  
  
-   **Connessione server** : dettagli della connessione per il server.  
  
-   **Database** : specificare o confermare il nome di un nuovo database. Se il nome del database esiste già nell'istanza di destinazione di SQL Server, specificare un nome di database modificato.  
  
##  <a name="summary-page"></a><a name="Summary"></a> Pagina Riepilogo  
 Usare questa pagina per esaminare le impostazioni specificate per l'operazione. Per completare l'operazione di distribuzione usando le impostazioni specificate, fare clic su **Fine**. Per annullare l'operazione di distribuzione e chiudere la procedura guidata, fare clic su **Annulla**.  
  
 È possibile che siano necessari passaggi manuali per distribuire i dettagli del database nel database di SQL Server nella macchina virtuale di Azure. Tali passaggi saranno descritti in dettaglio automaticamente.  
  
##  <a name="results-page"></a><a name="Results"></a>Pagina dei risultati  
 In questa pagina è riportato l'esito positivo o negativo dell'operazione di distribuzione, indicante i risultati di ogni azione. Per ogni azione per la quale è stato rilevato un errore sarà presente un'indicazione nella colonna **Risultato** . Fare clic sul collegamento per visualizzare un report dell'errore relativo all'azione.  
  
 Fare clic su **Fine** per chiudere la procedura guidata.  
  
## <a name="see-also"></a>Vedere anche  
 [adattatore del cloud per SQL Server](../../database-engine/cloud-adapter-for-sql-server.md)   
 [Gestione del ciclo di vita del database](../database-lifecycle-management.md)   
 [Esportare un'applicazione livello dati](../data-tier-applications/export-a-data-tier-application.md)   
 [Importare un file BACPAC per creare un nuovo database utente](../data-tier-applications/import-a-bacpac-file-to-create-a-new-user-database.md)   
 [Backup e ripristino del database SQL di Azure](https://msdn.microsoft.com/library/azure/jj650016.aspx)   
 [Distribuzione SQL Server in macchine virtuali di Azure](https://msdn.microsoft.com/library/dn133141.aspx)   
 [Preparazione della migrazione a SQL Server in Macchine virtuali di Azure](https://msdn.microsoft.com/library/dn133142.aspx)  
  
  
