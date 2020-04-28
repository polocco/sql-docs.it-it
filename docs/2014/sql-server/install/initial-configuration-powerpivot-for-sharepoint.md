---
title: Configurazione iniziale (PowerPivot per SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3a0ec2eb-017a-40db-b8d4-8aa8f4cdc146
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 24a52b9dd190032a55306c1fe738c3c1e1787dad
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "79112212"
---
# <a name="initial-configuration-powerpivot-for-sharepoint"></a>Configurazione iniziale (PowerPivot per SharePoint)
  Seguire i passaggi descritti in questo argomento per configurare un'installazione iniziale di PowerPivot per SharePoint. Il modo più semplice per eseguire questa operazione consiste nell'utilizzare lo strumento di configurazione PowerPivot. Tale strumento consente di eseguire in modo automatico tutti i passaggi di configurazione descritti di seguito.  
  
 In alternativa, se si desidera più controllo sul modo in cui il server è configurato, è possibile utilizzare Amministrazione centrale e le informazioni descritte in questo argomento per eseguire ogni passaggio singolarmente.  
  
 
  
## <a name="prerequisites"></a>Prerequisiti  
 È necessario che il server SharePoint sia stato installato tramite l'opzione per server farm durante l'installazione di SharePoint. Non è supportato un server SharePoint autonomo che utilizza un database predefinito. Per ulteriori informazioni, vedere [linee guida per l'utilizzo di SQL Server funzionalità di business intelligence in una farm di SharePoint 2010](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md).  
  
> [!IMPORTANT]  
>  Prima di configurare PowerPivot per SharePoint o una farm di SharePoint che utilizza un server di database [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] è necessario che SharePoint 2010 SP1 sia installato. Se non è stato ancora installato un Service Pack, eseguire adesso questa operazione prima di iniziare a configurare il server.  
  
 È necessario che PowerPivot per SharePoint sia installato È necessario che sia distribuita almeno una soluzione farm. Per distribuire la soluzione farm, utilizzare lo strumento di configurazione PowerPivot o uno script di PowerShell. Le istruzioni per questa operazione sono fornite in questo argomento.  
  
 Il computer deve fare parte di un dominio. Gli account specificati per i servizi devono essere account utente di dominio. Sarà necessario almeno un account di dominio per l'applicazione del servizio PowerPivot. In caso di configurazione di servizi aggiuntivi (quali Excel Services), è necessario disporre di account separati per ogni servizio specificato.  
  
 Per aggiungere PowerPivot per SharePoint alla farm, è necessario essere un amministratore di farm. Per aggiungere server e applicazioni alla farm è necessario inoltre conoscere la passphrase.  
  
##  <a name="step-1-deploy-powerpivot-solutions"></a><a name="deploywsp"></a>Passaggio 1: distribuire soluzioni PowerPivot  
 Le soluzioni da installare e distribuire sono due, ovvero una soluzione farm e una soluzione applicazione Web.  
  
### <a name="install-and-deploy-the-farm-solution"></a>Installare e distribuire la soluzione farm
  
 Nella versione precedente la soluzione farm viene installata e distribuita dal programma di installazione di SQL Server, mentre nella versione corrente è necessario utilizzare lo strumento di configurazione PowerPivot o uno script di PowerShell. Non è possibile utilizzare Amministrazione centrale per distribuire la soluzione farm. Questo è l'unico passaggio della configurazione di PowerPivot per SharePoint che non può essere eseguito in Amministrazione centrale. Dopo che la soluzione farm è stata distribuita, è possibile utilizzare Amministrazione centrale e i passaggi descritti in questo argomento per configurare un'installazione di PowerPivot per SharePoint.  
  
 In questo passaggio si esegue PowerShell per installare e distribuire la soluzione farm. Per ulteriori informazioni, vedere [configurazione di PowerPivot mediante Windows PowerShell](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell).  
  
1.  Aprire una shell di gestione di SharePoint 2010 utilizzando l'opzione **Esegui come amministratore** .  
  
2.  Eseguire il primo cmdlet:  
  
    ```powershell
    Add-SPSolution -LiteralPath "C:\Program Files\Microsoft SQL Server\120\Tools\PowerPivotTools\ConfigurationTool\Resources\PowerPivotFarm.wsp"  
    ```  
  
     Il cmdlet restituisce il nome e l'ID della soluzione e Deployed=False. Nel passaggio successivo la soluzione verrà distribuita.  
  
3.  Eseguire il secondo cmdlet per distribuire la soluzione:  
  
    ```powershell
    Install-SPSolution -Identity PowerPivotFarm.wsp -GACDeployment -Force  
    ```  
  
### <a name="deploy-the-web-application-solution"></a>Distribuire la soluzione applicazione Web
  
1.  Fare clic sul pulsante Start, selezionare **tutti i programmi**, selezionare **prodotti Microsoft SharePoint 2010**, quindi selezionare **Amministrazione centrale SharePoint 2010**.  
  
2.  In Impostazioni sistema di Amministrazione centrale SharePoint 2010 fare clic su **Gestisci soluzioni farm**.  
  
     Verranno visualizzati due pacchetti della soluzione separati: powerpivotfarm.wsp e powerpivotwebapp.wsp. È necessario che la prima soluzione (powerpivotfarm.wsp) sia già distribuita. Una volta distribuita, non è necessario distribuirla nuovamente. La seconda soluzione (powerpivotwebapp.wsp) viene distribuita per Amministrazione centrale. È tuttavia necessario distribuirla manualmente per ogni applicazione Web di SharePoint in grado di supportare l'accesso ai dati PowerPivot.  
  
3.  Fare clic su **powerpivotwebapp. wsp**.  
  
4.  Fare clic su **Distribuisci soluzione.**  
  
5.  In **Distribuisci in?** selezionare l'applicazione Web di SharePoint a cui si desidera aggiungere il supporto della funzionalità PowerPivot.  
  
6.  Fare clic su **OK**.  
  
7.  Ripetere l'operazione per le altre applicazioni Web SharePoint che supporteranno l'accesso ai dati PowerPivot.  
  
##  <a name="step-2-start-services-on-the-server"></a><a name="Geneva"></a>Passaggio 2: avviare i servizi nel server  
 Una distribuzione di PowerPivot per SharePoint richiede che nella farm siano inclusi i servizi seguenti: Servizi di calcolo Excel, servizio di archiviazione sicura e Attestazioni per il servizio token Windows.  
  
 Attestazioni per il servizio token Windows è richiesto per Excel Services e PowerPivot per SharePoint. Viene utilizzato per stabilire le connessioni a origini dati esterne tramite l'identità Windows dell'utente corrente di SharePoint. Questo servizio deve essere in esecuzione in ogni server di SharePoint che dispone di Excel Services o PowerPivot per SharePoint abilitato. Se il servizio non è ancora stato avviato, è necessario avviarlo in questo momento per abilitare Excel Services per l'inoltro delle richieste autenticate al servizio di sistema PowerPivot.  
  
1.  In Impostazioni sistema di amministrazione centrale fare clic **su Gestisci servizi nel server**.  
  
2.  Avviare Attestazioni per il servizio token Windows.  
  
3.  Avviare Servizi di calcolo Excel.  
  
4.  Avviare il servizio di archiviazione sicura.  
  
5.  Verificare che sia Analysis Services sia il servizio di sistema PowerPivot di SQL Server siano avviati.  
  
##  <a name="step-3-create-a-powerpivot-service-application"></a><a name="createapp"></a>Passaggio 3: creare un'applicazione di servizio PowerPivot  
 Il passaggio successivo consiste nel creare un'applicazione del servizio PowerPivot.  
  
1.  In Gestione applicazioni di amministrazione centrale fare clic su **Gestisci applicazioni di servizio**.  
  
2.  Nella barra multifunzione **Applicazioni di servizio** fare clic su **Nuovo**.  
  
3.  Selezionare **SQL Server applicazione di servizio PowerPivot**. Se non è presente nell'elenco, PowerPivot per SharePoint non è installato o la soluzione non è distribuita.  
  
4.  Nella pagina **Crea nuova applicazione di servizio PowerPivot** immettere un nome per l'applicazione. Il valore predefinito è\<PowerPivotServiceApplication Number>. Se si creano più applicazioni di servizio PowerPivot, un nome descrittivo sarà utile per capire come viene utilizzata l'applicazione.  
  
5.  In Pool di applicazioni creare un nuovo pool di applicazioni e selezionare un account di sicurezza. L'account utente di dominio è obbligatorio.  
  
6.  In **server database**scegliere un server di database in cui creare il database dell'applicazione di servizio. Il valore predefinito è l'istanza del motore di database di SQL Server che ospita i database di configurazione della farm.  
  
7.  In **nome database**il valore predefinito è PowerPivotServiceApplication1_\<> GUID. Il nome del database predefinito corrisponde al nome predefinito dell'applicazione di servizio. Se è stato immesso un nome univoco per l'applicazione del servizio, seguire una convenzione di denominazione simile per il nome del database in modo da poterli gestire insieme.  
  
8.  In **Autenticazione database**l'impostazione predefinita è Autenticazione di Windows. Se si sceglie **Autenticazione di SQL Server**, fare riferimento alla guida dell'amministratore di SharePoint per le procedure consigliate sull'utilizzo di questo tipo di autenticazione in una distribuzione di SharePoint.  
  
9. Selezionare la casella di controllo **Aggiungi il proxy per questa applicazione di servizio PowerPivot al gruppo di proxy predefinito.** La connessione all'applicazione di servizio verrà aggiunta al gruppo predefinito di connessioni al servizio. È necessario disporre di almeno un'applicazione del servizio PowerPivot nel gruppo di connessioni predefinito.  
  
     Se un'applicazione del servizio PowerPivot è già elencata nel gruppo di connessioni predefinito, non aggiungerne una seconda. L'aggiunta di due applicazioni di servizio dello stesso tipo del gruppo di connessioni predefinito non è una configurazione supportata. Per ulteriori informazioni sull'utilizzo di applicazioni di servizio aggiuntive in un gruppo di connessione, vedere [connettere un'applicazione del servizio PowerPivot a un'applicazione Web di SharePoint in Amministrazione centrale](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/connect-power-pivot-service-app-to-sharepoint-web-app-in-ca).  
  
10. Fare clic su **OK**. Il servizio verrà visualizzato con altri servizi gestiti nell'elenco di applicazioni di servizio della farm.  
  
##  <a name="step-4-enable-excel-services"></a><a name="ExcelServ"></a>Passaggio 4: abilitare Excel Services  
 PowerPivot per SharePoint richiede Excel Services per il supporto dell'accesso ai dati PowerPivot nella farm. È possibile determinare se Excel Services è già abilitato verificando se l'applicazione Excel Services è presente nell'elenco di applicazioni di servizio in Amministrazione centrale. Se Excel Services non è elencato, effettuare le operazioni seguenti per abilitarlo.  
  
1.  In Gestione applicazioni di amministrazione centrale fare clic su **Gestisci applicazioni di servizio**.  
  
2.  In Crea della barra multifunzione applicazioni di servizio fare clic su **nuovo**.  
  
3.  Selezionare **applicazione Excel Services**.  
  
4.  In Crea nuova applicazione Excel Services specificare un nome, ad esempio Applicazione Excel Services.  
  
5.  In Pool di applicazioni selezionare Crea nuovo pool di applicazioni e assegnare a esso un nome descrittivo, ad esempio Pool di applicazioni di Excel Services.  
  
6.  In Configurabili selezionare un account utente di dominio di Windows per l'identità di questo pool di applicazioni.  
  
7.  Mantenere la casella di controllo predefinita per l'aggiunta del proxy dell'applicazione di servizio all'elenco delle connessioni al servizio predefinito.  
  
8.  Fare clic su **OK**.  
  
9. Fare clic sull'applicazione Excel Services creata.  
  
10. Fare clic su **percorsi file attendibili** e in questa pagina selezionare il percorso attendibile. In genere, viene elencato come **http://** nella colonna Address. Per assicurarsi che sia Excel Services sia il servizio PowerPivot abbiano accesso alla cartella di lavoro, è necessario includere SharePoint come percorso attendibile di Excel Services. Il servizio di sistema PowerPivot non può accedere alle cartelle di lavoro archiviate all'esterno di una farm di SharePoint.  
  
11. Nell'area Proprietà cartella di lavoro impostare **dimensioni massime cartella di lavoro** su 50.  
  
12. In dati esterni impostare **Consenti dati esterni** su **raccolte connessioni dati attendibili e incorporati**. Questa impostazione è necessaria per l'accesso ai dati PowerPivot in una cartella di lavoro.  
  
13. Deselezionare la casella di controllo **avvisa in caso di aggiornamento dati** per consentire immagini di anteprima dei singoli fogli di dati nella raccolta PowerPivot. Se si sceglie di conservare l'avviso e le impostazioni della cartella di lavoro specificano l'aggiornamento all'apertura, si potrebbe ottenere una singola immagine di anteprima dell'avviso anziché le pagine della cartella di lavoro.  
  
14. Fare clic su **OK**.  
  
##  <a name="step-5-enable-secure-store-service-and-configure-data-refresh"></a><a name="SSS"></a>Passaggio 5: abilitare servizio di archiviazione sicura e configurare l'aggiornamento dati  
 PowerPivot per SharePoint richiede il servizio di archiviazione sicura per archiviare le credenziali e l'account di esecuzione automatica per l'aggiornamento dati. È possibile determinare se il servizio di archiviazione sicura è già abilitato verificando se viene visualizzato nell'elenco di applicazioni di servizio.  
  
> [!IMPORTANT]  
>  Se il servizio di archiviazione sicura è abilitato, è necessario ancora verificare che sia stata generata una chiave master. Per istruzioni, vedere la Parte 2: Generare la chiave master nella procedura riportata di seguito.  
  
 Se il servizio di archiviazione sicura non è elencato, effettuare le operazioni seguenti per abilitarlo. Abilitando l'archiviazione sicura, gli autori di cartelle di lavoro e i proprietari di documenti possono accedere a una gamma più ampia di opzioni di connessione all'origine dati quando si pianifica l'aggiornamento dei dati per le cartelle di lavoro pubblicate.  
  
##### <a name="part-1-enable-secure-store-service"></a>Parte 1: Abilitare il servizio di archiviazione sicura  
  
1.  In Gestione applicazioni di amministrazione centrale fare clic su **Gestisci applicazioni di servizio**.  
  
2.  In Crea della barra multifunzione applicazioni di servizio fare clic su **nuovo**.  
  
3.  Selezionare **servizio di archiviazione sicura**.  
  
4.  Nella pagina **Crea applicazione di archiviazione sicura** immettere un nome per l'applicazione.  
  
5.  In **database**specificare il SQL Server istanza di che ospiterà il database per questa applicazione di servizio. Il valore predefinito è l'istanza del motore di database di SQL Server che ospita i database di configurazione della farm.  
  
6.  In **nome database**immettere il nome del database dell'applicazione di servizio. Il valore predefinito è Secure_Store_Service_DB_\<> GUID. Il nome predefinito corrisponde al nome predefinito dell'applicazione di servizio. Se è stato immesso un nome univoco per l'applicazione del servizio, seguire una convenzione di denominazione simile per il nome del database in modo da poterli gestire insieme.  
  
7.  In **Autenticazione database**l'impostazione predefinita è Autenticazione di Windows. Se si sceglie Autenticazione di SQL Server, fare riferimento alla guida dell'amministratore di SharePoint per le procedure consigliate sull'utilizzo di questo tipo di autenticazione nella farm in uso.  
  
8.  In pool di applicazioni selezionare **Crea nuovo pool di applicazioni.** Specificare un nome descrittivo che consentirà ad altri amministratori di server di identificare la modalità di utilizzo del pool di applicazioni.  
  
9. Selezionare un account di sicurezza per il pool di applicazioni. Specificare un account gestito per utilizzare un account utente di dominio.  
  
10. Accettare i valori predefiniti rimanenti, quindi fare clic su **OK.** L'applicazione di servizio verrà visualizzata con altri servizi gestiti nell'elenco di applicazioni di servizio della farm.  
  
##### <a name="part-2-generate-the-master-key"></a>Parte 2: Generare la chiave master  
  
1.  Fare clic sull'applicazione del servizio di archiviazione sicura nell'elenco.  
  
2.  Nella barra multifunzione applicazioni di servizio fare clic su **Gestisci**.  
  
3.  In gestione chiavi fare clic su **genera nuova chiave**.  
  
4.  Immettere e confermare una passphrase. La passphrase verrà utilizzata per aggiungere applicazioni di servizio condivise di archiviazione sicura aggiuntive.  
  
5.  Fare clic su **OK**.  
  
##### <a name="part-3-configure-the-unattended-powerpivot-data-refresh-account"></a>Parte 3: Configurare l'account di aggiornamento dati automatico PowerPivot  
 La creazione di un account di aggiornamento dati automatico per l'accesso ai dati PowerPivot è spesso richiesta per l'accesso ai dati esterni durante l'aggiornamento dei dati. Ad esempio, se Kerberos non è abilitato, è necessario creare un account automatico che il servizio PowerPivot può utilizzare per connettersi alle origini dati esterne.  
  
 Per istruzioni su come creare l'account di aggiornamento dati automatico PowerPivot o altre credenziali archiviate utilizzate nell'aggiornamento dati, vedere [configurare l'account di aggiornamento dati automatico powerpivot &#40;PowerPivot per SharePoint&#41;](../../analysis-services/configure-unattended-data-refresh-account-powerpivot-sharepoint.md) e [configurare le credenziali archiviate per l'aggiornamento dati powerpivot &#40;PowerPivot per SharePoint&#41;](../../../2014/analysis-services/configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).  
  
##  <a name="step-6-enable-usage-data-collection"></a><a name="Usage"></a>Passaggio 6: abilitare la raccolta dei dati di utilizzo  
 PowerPivot per SharePoint utilizza l'infrastruttura della raccolta dati di utilizzo di SharePoint per raggruppare informazioni sull'utilizzo di PowerPivot nell'intera farm. Anche se i dati di utilizzo fanno sempre parte di un'installazione di SharePoint, devono essere abilitati prima di poter essere utilizzati. Per istruzioni, vedere [configurare la raccolta dati di utilizzo per &#40;PowerPivot per SharePoint](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-usage-data-collection-for-power-pivot-for-sharepoint).  
  
##  <a name="step-7-increase-maximum-upload-size-for-sharepoint-web-applications-and-excel-services"></a><a name="Upload"></a>Passaggio 7: aumentare le dimensioni massime di caricamento per le applicazioni Web di SharePoint e Excel Services  
 Poiché le cartelle di lavoro di PowerPivot possono essere di grandi dimensioni, è possibile aumentare le dimensioni massime dei file. Possono essere configurate due impostazioni relative alle dimensioni dei file: Dimensioni massime caricamento per l'applicazione Web e Dimensioni massime cartella di lavoro in Excel Services. Le dimensioni massime dei file devono essere impostate sullo stesso valore in entrambe le applicazioni. Per istruzioni, vedere [configurare le dimensioni massime di caricamento dei File &#40;PowerPivot per SharePoint&#41;](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-maximum-file-upload-size-power-pivot-for-sharepoint).  
  
##  <a name="step-8-activate-powerpivot-feature-integration-for-site-collections"></a><a name="activatePP"></a>Passaggio 8: attivare l'integrazione delle funzionalità di PowerPivot per le raccolte siti  
 L'attivazione di funzionalità a livello di raccolta siti rende disponibile pagine e modelli dell'applicazione nei siti in uso, incluse le pagine di configurazione per l'aggiornamento dati pianificato e le pagine dell'applicazione per la raccolta PowerPivot e le librerie di feed di dati.  
  
1.  Da un sito di SharePoint scegliere **Azioni sito**.  
  
     Per impostazione predefinita, l'accesso alle applicazioni Web SharePoint viene effettuato tramite la porta 80. Ciò significa che spesso è possibile accedere a un sito di SharePoint immettendo il nome del computer http://\<> per aprire la raccolta siti radice.  
  
2.  Fare clic su **Impostazioni sito**.  
  
3.  In Amministrazione raccolta siti selezionare **Caratteristiche raccolta siti**.  
  
4.  Scorrere la pagina verso il basso fino a individuare la **funzionalità di raccolta siti di integrazione PowerPivot**.  
  
5.  Fare clic su **Attiva**.  
  
6.  Ripetere per le raccolte siti aggiuntive aprendo ogni sito e facendo clic su **Azioni sito**.  
  
 Per ulteriori informazioni, vedere [attivazione dell'integrazione delle funzionalità di PowerPivot per le raccolte siti in Amministrazione centrale](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/activate-power-pivot-integration-for-site-collections-in-ca).  
  
##  <a name="step-9-install-the-sql-server-2008-r2-version-of-the-ole-db-provider-on-a-sql-server-2012-powerpivot-for-sharepoint-instance"></a><a name="bkmk_redist"></a>Passaggio 9: installare la versione di SQL Server 2008 R2 del provider di OLE DB in un'istanza SQL Server 2012 PowerPivot per SharePoint  
 Se si desidera eseguire versioni obsolete e versioni più recenti di cartelle di lavoro di PowerPivot in modalità side-by-side sullo stesso server, è necessario installare il provider OLE DB di Analysis Services disponibile in SQL Server 2008 R2 in un server [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] PowerPivot per SharePoint.  
  
 L'installazione del provider consentirà di garantire che le cartelle di lavoro per le quali viene fatto riferimento a MSOLAP.4 nella stringa di connessione dati funzionino correttamente su un server [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] PowerPivot. L'installazione del provider OLE DB per SQL Server 2008 R2 rappresenta inoltre un approccio alternativo all'aggiornamento di cartelle di lavoro create in una versione precedente di PowerPivot per Excel.  
  
 È possibile scaricare il provider dalla [pagina SQL Server 2008 R2 Feature Pack](https://www.microsoft.com/download/details.aspx?id=44272). Cercare **microsoft® provider OLE DB Analysis Services per microsoft® SQL Server® 2008 R2**, quindi scaricare il pacchetto per x64 del programma di `SQLServer2008_ASOLEDB10.msi` installazione.  
  
 Per ulteriori informazioni sull'installazione del provider, inclusi i passaggi di verifica, vedere [Install the provider OLE DB Analysis Services on SharePoint Servers](../../../2014/sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).  
  
##  <a name="step-10-verify-installation"></a><a name="verifyinstall"></a>Passaggio 10: verificare l'installazione  
 L'elaborazione di query PowerPivot si verifica nella farm quando un utente o un'applicazione apre una cartella di lavoro di Excel che contiene dati PowerPivot. Come minimo, è possibile controllare le pagine sui siti di SharePoint per verificare che le funzionalità PowerPivot siano disponibili. Tuttavia, per verificare completamente un'installazione, è necessario disporre di una cartella di lavoro di PowerPivot pubblicabile in SharePoint e accessibile da una raccolta. A scopo di test, è possibile pubblicare una cartella di lavoro di esempio contenente già dati PowerPivot e utilizzarla per confermare la corretta configurazione dell'integrazione SharePoint.  
  
 Per verificare l'integrazione di PowerPivot con un sito di SharePoint, effettuare le operazioni seguenti:  
  
1.  In un browser aprire l'applicazione Web creata. Se sono stati usati i valori predefiniti, è possibile\<specificare http://il nome del computer> nell'indirizzo URL.  
  
2.  Verificare che le funzionalità di elaborazione e di accesso ai dati PowerPivot siano disponibili nell'applicazione. È possibile effettuare questa operazione verificando la presenza di modelli di libreria forniti da PowerPivot:  
  
    1.  In azioni sito fare clic su **altre opzioni.**..  
  
    2.  Nelle librerie dovrebbero essere visualizzate la **libreria di feed di dati** e la **raccolta PowerPivot**. Questi modelli di raccolta vengono forniti dalla funzionalità PowerPivot e saranno visibili nell'elenco delle raccolte se la funzionalità è integrata correttamente.  
  
 Per verificare l'accesso ai dati PowerPivot nel server, effettuare le operazioni seguenti:  
  
1.  Caricare una cartella di lavoro di PowerPivot in Raccolta PowerPivot o in qualsiasi raccolta SharePoint.  
  
2.  Fare clic sul documento per aprirlo dalla raccolta.  
  
3.  Fare clic su un filtro dei dati o filtrare i dati per avviare una query PowerPivot. I dati PowerPivot verranno caricati in background e verranno restituiti i risultati. Nel passaggio successivo verrà effettuata la connessione al server per verificare che i dati vengano caricati e memorizzati nella cache.  
  
4.  Avviare SQL Server Management Studio dal gruppo di programmi Microsoft SQL Server 2008 R2 nel menu Start. Se questo strumento non è installato nel server, è possibile ignorare l'ultimo passaggio per confermare la presenza di file memorizzati nella cache.  
  
5.  In Tipo di server selezionare **Analysis Services**.  
  
6.  In nome server immettere ** \<nome-server> \powerpivot**, dove ** \<Server-Name>** è il nome del computer in cui è installato PowerPivot per SharePoint.  
  
7.  Fare clic su **Connetti**.  
  
8.  In Esplora oggetti fare clic su **database** per visualizzare l'elenco dei file di dati PowerPivot caricati.  
  
9. Nel file system del computer, controllare la cartella seguente per determinare se i file vengono memorizzati nella cache su disco. La presenza di file memorizzati nella cache è un'ulteriore verifica che la distribuzione è operativa. Per visualizzare la cache dei file, spostarsi nella cartella \Programmi\Microsoft SQL Server\MSAS10_50.POWERPIVOT\OLAP\Backup.  
  
##  <a name="post-installation-steps"></a><a name="nextsteps"></a>Passaggi successivi all'installazione  
 Dopo aver verificato l'installazione, terminare la configurazione del servizio creando una raccolta PowerPivot oppure ottimizzando le singole impostazioni di configurazione. Per sfruttare al meglio i componenti server appena installati, è possibile scaricare [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] per creare e pubblicare la prima cartella di lavoro di PowerPivot.  
  
### <a name="install-data-providers-used-for-data-refresh"></a>Installare provider di dati utilizzati per l'aggiornamento dati  
 Se è stato abilitato l'aggiornamento dei dati, per il server saranno necessari gli stessi provider di dati per l'accesso ai dati esterni utilizzati dall'applicazione client PowerPivot per importare i dati originali (ad esempio, se i dati sono stati inizialmente importati utilizzando un provider a 32 bit, anche per l'aggiornamento dei dati lato server sarà richiesto un provider a 32 bit quando si accede alla stessa origine dati esterna). Per ulteriori informazioni, vedere [aggiornamento dati PowerPivot con SharePoint 2010](../../../2014/analysis-services/powerpivot-data-refresh-with-sharepoint-2010.md).  
  
### <a name="install-adonet-data-services"></a>Installare ADO.NET Data Services  
 È necessario installare ADO.NET Data Services 3.5 SP1 se si desidera esportare gli elenchi SharePoint come feed di dati. Per istruzioni, vedere [installare ADO.NET Data Services per supportare esportazioni di feed di dati di elenchi SharePoint](../../../2014/sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md).  
  
### <a name="create-a-powerpivot-gallery"></a>Creare una Raccolta PowerPivot  
 Raccolta PowerPivot include opzioni di anteprima e presentazione per la visualizzazione delle cartelle di lavoro di PowerPivot su un sito di SharePoint. L'utilizzo di Raccolta PowerPivot per pubblicare e visualizzare le cartelle di lavoro di PowerPivot è consigliato per la sua funzionalità di anteprima. Inoltre, se Reporting Services è stato distribuito nello stesso server SharePoint, Raccolta PowerPivot semplifica le procedure di creazione di report. È possibile avviare Generatore report dall'interno di Raccolta PowerPivot per basare un nuovo report su una cartella di lavoro di PowerPivot pubblicata. Per ulteriori informazioni sulla creazione e sull'utilizzo della libreria, vedere [creare e personalizzare la raccolta PowerPivot](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/create-and-customize-power-pivot-gallery) e [utilizzare la raccolta PowerPivot](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/use-power-pivot-gallery).  
  
### <a name="create-additional-trusted-sites-in-excel-services"></a>Creare siti attendibili aggiuntivi in Excel Services  
 È possibile aggiungere siti attendibili in Excel Services per variare le autorizzazioni e le impostazioni di configurazione nei siti che forniscono cartelle di lavoro di Excel e dati PowerPivot. Per altre informazioni, vedere [Create a trusted location for PowerPivot sites in Central Administration](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration).  
  
### <a name="tune-configuration-settings"></a>Ottimizzare le impostazioni di configurazione  
 Un'applicazione di servizio PowerPivot viene creata utilizzando valori e proprietà predefiniti. È possibile modificare le impostazioni di configurazione per singole applicazioni di servizio per modificare la metodologia di allocazione delle richieste, impostare timeout del server, modificare le soglie per gli eventi del report di risposta alle query o specificare il periodo di conservazione dei dati di utilizzo. Per ulteriori informazioni sulla configurazione in Amministrazione centrale o sull'utilizzo delle funzionalità PowerPivot nelle applicazioni Web di SharePoint, vedere [amministrazione e configurazione del server PowerPivot in Amministrazione centrale](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration).  
  
### <a name="install-powerpivot-for-excel-and-build-a-powerpivot-workbook"></a>Installare PowerPivot per Excel e compilare una cartella di lavoro di PowerPivot  
 Dopo aver installato i componenti server in una farm, è possibile creare la prima cartella di lavoro di Excel 2010 che utilizza dati PowerPivot incorporati, quindi pubblicarla in una raccolta SharePoint in un'applicazione Web. Prima di poter compilare cartelle di lavoro di Excel contenenti dati PowerPivot, è necessario partire con un'installazione di Excel 2010, seguita dal componente aggiuntivo PowerPivot per Excel che fornisce il supporto per l'importazione dei dati PowerPivot.  
  
### <a name="add-servers-or-applications"></a>Aggiungere server o applicazioni  
 Quando si distribuisce la soluzione PowerPivot, l'integrazione della funzionalità viene attivata a livello di raccolta siti per tutte le raccolte siti dell'applicazione Web. Quando si creano nuove applicazioni Web, è necessario distribuire la soluzione powerpivotwebapp a ognuna. Per istruzioni, vedere [distribuire soluzioni PowerPivot in SharePoint](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint).  
  
 A seconda del modo in cui si configura l'applicazione del servizio PowerPivot, il servizio di sistema PowerPivot sarà aggiunto al gruppo di connessioni predefinito, rendendolo disponibile a tutte le applicazioni Web che utilizzano le connessioni predefinite. Tuttavia, se le applicazioni Web sono state configurate in modo da utilizzare gli elenchi di connessioni ad applicazioni di servizio personalizzate, sarà necessario aggiungere l'applicazione del servizio PowerPivot a ogni applicazione Web di SharePoint per la quale si desidera abilitare l'elaborazione dei dati PowerPivot. Per ulteriori informazioni, vedere [connettere un'applicazione del servizio PowerPivot a un'applicazione Web di SharePoint in Amministrazione centrale](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/connect-power-pivot-service-app-to-sharepoint-web-app-in-ca).  
  
 Nel tempo, se si rendessero necessarie ulteriori funzionalità di elaborazione e archiviazione dati, sarà possibile aggiungere una seconda istanza del server PowerPivot per SharePoint alla farm. Il processo di installazione è praticamente identico ai passaggi eseguiti per aggiungere il primo server, ad eccezione dei requisiti relativi all'immissione di nomi di istanza o delle informazioni sull'account di servizio. Per istruzioni, vedere [elenco di controllo per la distribuzione: scalabilità orizzontale mediante l'aggiunta di server PowerPivot a una farm di SharePoint 2010](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità supportate dalle edizioni di SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Configurare gli account del servizio PowerPivot](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts)   
 [Creazione e configurazione di un'applicazione di servizio PowerPivot in Amministrazione centrale](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca)   
 [Distribuire soluzioni PowerPivot in SharePoint](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint)   
 [Attivare l'integrazione delle funzionalità di PowerPivot per le raccolte siti in Amministrazione centrale](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/activate-power-pivot-integration-for-site-collections-in-ca)   
 [Installazione di PowerPivot per SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
