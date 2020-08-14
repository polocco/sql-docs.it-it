---
title: Distribuire un database tramite un'applicazione livello dati | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.dbdeployment.settings.f1
- sql13.swb.dbdeployment.progress.f1
- sql13.swb.dbdeployment.summary.f1
- sql13.swb.dbdeployment.results.f1
- sql13.swb.dbdeployment.welcome.f1
helpviewer_keywords:
- deploy database wizard
- database deploy [SQL Server]
ms.assetid: 08c506e8-4ba0-4a19-a066-6e6a5c420539
author: stevestein
ms.author: sstein
ms.openlocfilehash: e93398b38e2fff73e63013fd0bfc1c4bedc31a43
ms.sourcegitcommit: 822d4b3cfa53269535500a3db5877a82b5076728
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/07/2020
ms.locfileid: "87988761"
---
# <a name="deploy-a-database-by-using-a-dac"></a>Distribuire un database tramite un'applicazione livello dati
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Usare la procedura guidata **Distribuire il database nel database SQL di Microsoft Azure** per distribuire un database tra un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] e un server [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] o tra due server [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)].  
  
##  <a name="before-you-begin"></a><a name="BeforeBegin"></a> Prima di iniziare  
 Nella procedura guidata viene utilizzato un file di archivio BACPAC dell'applicazione livello dati per distribuire sia i dati sia le definizioni degli oggetti di database. Vengono eseguite un'operazione di esportazione dell'applicazione livello dati dal database di origine e un'importazione dell'applicazione livello dati nella destinazione.  
  
###  <a name="database-options-and-settings"></a><a name="DBOptSettings"></a> Opzioni e impostazioni del database  
 Le impostazioni predefinite del database creato durante la distribuzione saranno quelle dell'istruzione CREATE DATABASE. Tuttavia, esiste un'eccezione, cioè le regole di confronto del database e il livello di compatibilità sono impostati sui valori del database di origine.  
  
 Le opzioni del database, ad esempio TRUSTWORTHY, DB_CHAINING e HONOR_BROKER_PRIORITY, non possono essere modificate durante il processo di distribuzione. Le proprietà fisiche, ad esempio il numero di filegroup o i numeri e le dimensioni dei file, non possono essere modificate durante il processo di distribuzione. Al termine della distribuzione, è possibile usare l'istruzione ALTER DATABASE, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell per modificare il database in base alle proprie esigenze.  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Limitazioni e restrizioni  
 La procedura guidata **Distribuisci database** supporta la distribuzione di un database:  
  
-   Da un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] a [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)].  
  
-   Da [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
-   Tra due server [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] .  
  
 La procedura guidata non supporta la distribuzione di database tra due istanze del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 Per poter funzionare con la procedura guidata, in un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] deve essere eseguito [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) o versioni successive. Se in un database presente in un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] sono contenuti oggetti non supportati in [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)], non è possibile utilizzare la procedura guidata per distribuire il database in [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]. Se in un database presente in [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] sono contenuti oggetti non supportati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], non è possibile utilizzare la procedura guidata per distribuire il database nelle istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
###  <a name="security"></a><a name="Security"></a> Sicurezza  
 Per migliorare la sicurezza, gli account di accesso dell'autenticazione di SQL Server vengono archiviati in un file BACPAC dell'applicazione livello dati senza password. Quando il file BACPAC viene importato, l'account di accesso viene creato come account disabilitato con una password generata. Per abilitare gli account di accesso, è necessario accedere usando un account che dispone dell'autorizzazione ALTER ANY LOGIN e usare ALTER LOGIN per abilitare l'account di accesso e assegnare una nuova password che può essere comunicata all'utente. Questa operazione non è necessaria per gli account di accesso dell'autenticazione di Windows, in quanto le relative password non sono gestite da SQL Server.  
  
#### <a name="permissions"></a>Autorizzazioni  
 Per la procedura guidata sono richieste autorizzazioni di esportazione dell'applicazione livello dati sul database di origine. Per l'account di accesso sono richieste almeno le autorizzazioni ALTER ANY LOGIN e VIEW DEFINITION nell'ambito del database, nonché le autorizzazioni SELECT su **sys.sql_expression_dependencies**. L'esportazione di un'applicazione livello dati può essere effettuata da membri del ruolo predefinito del server securityadmin che sono anche membri del ruolo predefinito del database database_owner nel database dal cui viene esportata l'applicazione livello dati. Possono esportare un'applicazione livello dati anche i membri del ruolo predefinito del server sysadmin o dell'account amministratore di sistema SQL Server predefinito denominato **sa** .  
  
 Per la procedura guidata sono richieste autorizzazioni di importazione dell'applicazione livello dati sull'istanza o sul server di destinazione. L'account di accesso deve essere un membro del ruolo predefinito del server **sysadmin** , **serveradmin** o **dbcreator** con autorizzazioni ALTER ANY LOGIN. È anche possibile importare un'applicazione livello dati con l'account dell'amministratore di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] predefinito denominato **sa** . L'importazione di un'applicazione livello dati con gli account di accesso in [!INCLUDE[ssSDS](../../includes/sssds-md.md)] richiede l'appartenenza al ruolo loginmanager o serveradmin. L'importazione di un'applicazione livello dati senza account di accesso in [!INCLUDE[ssSDS](../../includes/sssds-md.md)] richiede l'appartenenza al ruolo dbmanager o serveradmin.  
  
##  <a name="using-the-deploy-database-wizard"></a><a name="UsingDeployDACWizard"></a> Utilizzo della procedura guidata Distribuisci database  
 **Per eseguire la migrazione di un database utilizzando la procedura guidata Distribuisci database**  
  
1.  Connettersi alla posizione del database che si desidera distribuire. È possibile specificare un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] o un server [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] .  
  
2.  In **Esplora oggetti**espandere il nodo dell'istanza in cui è contenuto il database.  
  
3.  Espandere il nodo di **Database** .  
  
4.  Fare clic con il pulsante destro del mouse sul database da distribuire, scegliere **Attività** e quindi **Distribuire il database nel database SQL di Microsoft Azure**  
  
5.  Completare le finestre di dialogo della procedura guidata:  
  
    -   [Pagina Introduzione](#Introduction)  
  
    -   [Impostazioni di distribuzione](#Deployment_settings)  
  
    -   [Pagina Riepilogo](#Summary)  
  
    -   [Progress](#Progress)  
    
    -   [Risultati](#Results)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> Pagina Introduzione  
 In questa pagina vengono illustrati i passaggi necessari per la procedura guidata **Distribuisci database** .  
  
 **Opzioni**  
  
-   **Non visualizzare più questa pagina** Selezionare la casella di controllo per evitare che la pagina Introduzione venga visualizzata nuovamente in futuro.  
  
-   **Avanti** : consente di passare alla pagina **Impostazioni di distribuzione** .  
  
-   **Annulla**: annulla l'operazione e chiude la procedura guidata.  
  
##  <a name="deployment-settings-page"></a><a name="Deployment_settings"></a> Pagina Impostazioni di distribuzione  
 Usare questa pagina per specificare il server di destinazione e fornire i dettagli sul nuovo database.  
  
 **Host locale:**  
  
-   **Connessione server**: specificare i dettagli della connessione al server e quindi fare clic su **Connetti** per verificare la connessione.  
  
-   **Nome nuovo database**: specificare un nome per il nuovo database.  
  
 **[!INCLUDE[ssSDS](../../includes/sssds-md.md)] :**  
  
-   **Edizione di [!INCLUDE[ssSDS](../../includes/sssds-md.md)]** : selezionare l'edizione di [!INCLUDE[ssSDS](../../includes/sssds-md.md)] nel menu a discesa.  
  
-   **Dimensioni massime database**: selezionare le dimensioni massime del database dal menu a discesa.  
  
 **Altre impostazioni:**  
  
-   Specificare una directory locale per il file temporaneo, cioè il file di archivio BACPAC. Si noti che il file verrà creato nel percorso specificato in cui rimarrà una volta completata l'operazione.  
  
##  <a name="summary-page"></a><a name="Summary"></a> Pagina Riepilogo  
 Utilizzare questa pagina per esaminare le impostazioni di origine e destinazione specificate per l'operazione. Per completare l'operazione di distribuzione usando le impostazioni specificate, fare clic su **Fine**. Per annullare l'operazione di distribuzione e chiudere la procedura guidata, fare clic su **Annulla**.  
  
##  <a name="progress-page"></a><a name="Progress"></a> Pagina Stato  
 In questa pagina viene visualizzato un indicatore di stato che indica lo stato dell'operazione. Per visualizzare lo stato dettagliato, fare clic sull'opzione **Visualizza dettagli** .  
  
##  <a name="results-page"></a><a name="Results"></a> Pagina Risultati  
 In questa pagina è riportato l'esito positivo o negativo dell'operazione di distribuzione, indicante i risultati di ogni azione. Ogni azione che ha rilevato un errore avrà un collegamento nella colonna **Risultato** . Fare clic sul collegamento per visualizzare un report dell'errore relativo all'azione.  
  
 Fare clic su **Fine** per chiudere la procedura guidata.  
  
## <a name="using-a-net-framework-application"></a>Utilizzo di un'applicazione .NET Framework  
 **Per distribuire un database usando i metodi DacStoreExport() e Import() in un'applicazione .NET Framework.**  
  
 Per visualizzare un esempio di codice, scaricare l'applicazione di esempio dell'applicazione livello dati da [Codeplex](https://go.microsoft.com/fwlink/?LinkId=219575).  
  
1.  Creare un oggetto server SMO e impostarlo sull'istanza o sul server contenente il database che si desidera distribuire.  
  
2.  Aprire un oggetto **ServerConnection** e connetterlo alla stessa istanza.  
  
3.  Usare il metodo **Export** del tipo **Microsoft.SqlServer.Management.Dac.DacStore** per esportare il database in un file BACPAC. Specificare il nome del database da esportare e il percorso della cartella in cui posizionare il file BACPAC.  
  
4.  Creare un oggetto server SMO e impostarlo sull'istanza o sul server di destinazione.  
  
5.  Aprire un oggetto **ServerConnection** e connetterlo alla stessa istanza.  
  
6.  Usare il metodo **Import** del tipo **Microsoft.SqlServer.Management.Dac.DacStore** per importare il file BACPAC. Specificare il file BACPAC creato dall'esportazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Applicazioni livello dati](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [Esportazione di un'applicazione livello dati](../../relational-databases/data-tier-applications/export-a-data-tier-application.md)   
 [Importare un file BACPAC per creare un nuovo database utente](../../relational-databases/data-tier-applications/import-a-bacpac-file-to-create-a-new-user-database.md)  
  
  
