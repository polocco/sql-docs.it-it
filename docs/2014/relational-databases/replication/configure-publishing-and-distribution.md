---
title: Configurare la pubblicazione e la distribuzione | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], distribution
- distribution configuration [SQL Server replication]
- publishing [SQL Server replication], configuring
ms.assetid: 3cfc8966-833e-42fa-80cb-09175d1feed7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: afd1544b5412c6ce2d83a9a1e9a50ddf662b3056
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85011052"
---
# <a name="configure-publishing-and-distribution"></a>Configurazione della pubblicazione e della distribuzione
  In questo argomento viene descritto come configurare la pubblicazione e la distribuzione in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]o RMO (Replication Management Objects).  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="security"></a><a name="Security"></a> Sicurezza  
 Per ulteriori informazioni, vedere la pagina relativa alla [distribuzione protetta della replica](security/view-and-modify-replication-security-settings.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Con SQL Server Management Studio  
 Configurare la distribuzione mediante la Creazione guidata nuova pubblicazione o la Configurazione guidata distribuzione. Dopo aver configurato il server di distribuzione, visualizzare e modificare le proprietà nella finestra di dialogo Proprietà database di **distribuzione- \<Distributor> ** . Utilizzare la Configurazione guidata distribuzione se si desidera configurare un database di distribuzione in modo che i membri dei ruoli predefiniti del database **db_owner** possano creare pubblicazioni o per configurare un server di distribuzione remoto che non è un server di pubblicazione.  
  
#### <a name="to-configure-distribution"></a>Per configurare la distribuzione  
  
1.  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] connettersi al server che diventerà il server di distribuzione (in molti casi, il server di distribuzione e quello di pubblicazione coincidono) e quindi espandere il nodo del server.  
  
2.  Fare clic con il pulsante destro del mouse sulla cartella **Replica** e quindi fare clic su **Configura distribuzione**.  
  
3.  Eseguire i vari passaggi della Configurazione guidata distribuzione per:  
  
    -   Selezionare un server di distribuzione. Per utilizzare un server di distribuzione locale, selezionare **'' fungerà \<ServerName> da server di distribuzione per se stesso. SQL Server creerà un database di distribuzione e un log**. Per utilizzare un server di distribuzione remoto, selezionare **Usa il server seguente come server di distribuzione**e quindi specificare un server. È necessario che il server sia già configurato come server di distribuzione e che il server di pubblicazione sia abilitato per l'utilizzo del server di distribuzione. Per altre informazioni, vedere [Abilitazione di un server di pubblicazione remoto in un database di distribuzione &#40;SQL Server Management Studio&#41;](enable-a-remote-publisher-at-a-distributor-sql-server-management-studio.md).  
  
         Se si seleziona un server di distribuzione remoto, è necessario immettere la password nella pagina **Password amministrativa** per le connessioni effettuate dal server di pubblicazione a quello di distribuzione. Questa password deve corrispondere a quella specificata quando il server di pubblicazione è stato attivato nel server di distribuzione remoto.  
  
    -   Specificare una cartella snapshot radice per un server di distribuzione locale. La cartella snapshot è semplicemente una directory designata come condivisione. Gli agenti che eseguono letture e scritture in questa cartella devono disporre di autorizzazioni sufficienti per accedervi. Ogni server di pubblicazione che utilizza questo server di distribuzione crea una cartella nella cartella radice e ogni pubblicazione crea cartelle nella cartella del server di pubblicazione per l'archiviazione dei file snapshot. Per altre informazioni sulle impostazioni di sicurezza appropriate per la cartella, vedere [Sicurezza della cartella snapshot](security/secure-the-snapshot-folder.md).  
  
    -   Specificare il database di distribuzione (per un server di distribuzione locale). Nel database di distribuzione vengono memorizzati metadati e dati di cronologia relativi a tutti i tipi di replica e alle transazioni per la replica transazionale.  
  
    -   Facoltativamente, consentire ad altri server di pubblicazione di utilizzare il server di distribuzione. Se viene consentito ad altri server di pubblicazione di utilizzare il server di distribuzione, è necessario immettere la password nella pagina **Password server di distribuzione** per le connessioni effettuate da questi server di pubblicazione al server di distribuzione.  
  
    -   Facoltativamente, creare lo script delle impostazioni di configurazione. Per altre informazioni, vedere [Scripting Replication](scripting-replication.md).  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Con Transact-SQL  
 La pubblicazione e la distribuzione della replica possono essere configurate a livello di programmazione tramite le stored procedure di replica.  
  
#### <a name="to-configure-publishing-using-a-local-distributor"></a>Per configurare la pubblicazione utilizzando un server di distribuzione locale  
  
1.  Eseguire [sp_get_distributor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-get-distributor-transact-sql) per determinare se il server è già configurato come database di distribuzione.  
  
    -   Se il valore di **installed** nel set di risultati è **0**, eseguire [sp_adddistributor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistributor-transact-sql) nel database master del server di distribuzione.  
  
    -   Se il valore di **distribution db installed** nel set di risultati è **0**, eseguire [sp_adddistributiondb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql) nel database master del server di distribuzione. Specificare il nome del database di distribuzione per il ** \@ database**. Facoltativamente, è possibile specificare il periodo di memorizzazione massimo delle transazioni per ** \@ max_distretention** e il periodo di memorizzazione della cronologia per ** \@ history_retention**. Se viene creato un nuovo database, specificare i parametri desiderati per le relative proprietà.  
  
2.  Nel database di distribuzione, che è anche il server di pubblicazione, eseguire [sp_adddistpublisher &#40;&#41;Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql), specificando la condivisione UNC che verrà utilizzata come cartella snapshot predefinita per ** \@ working_directory**.  
  
3.  Nel server di pubblicazione eseguire [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql). Specificare il database da pubblicare per ** \@ dbname**, il tipo di replica per ** \@ optname**e il valore `true` per ** \@ value**.  
  
#### <a name="to-configure-publishing-using-a-remote-distributor"></a>Per configurare la pubblicazione utilizzando un server di distribuzione remoto  
  
1.  Eseguire [sp_get_distributor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-get-distributor-transact-sql) per determinare se il server è già configurato come database di distribuzione.  
  
    -   Se il valore di **installed** nel set di risultati è **0**, eseguire [sp_adddistributor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistributor-transact-sql) nel database master del server di distribuzione. Specificare una password complessa per la ** \@ password**. Questa password per l'account **distributor_admin** verrà utilizzata per la connessione del server di pubblicazione al server di distribuzione.  
  
    -   Se il valore di **distribution db installed** nel set di risultati è **0**, eseguire [sp_adddistributiondb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql) nel database master del server di distribuzione. Specificare il nome del database di distribuzione per il ** \@ database**. Facoltativamente, è possibile specificare il periodo di memorizzazione massimo delle transazioni per ** \@ max_distretention** e il periodo di memorizzazione della cronologia per ** \@ history_retention**. Se viene creato un nuovo database, specificare i parametri desiderati per le relative proprietà.  
  
2.  Nel server di distribuzione eseguire [sp_adddistpublisher &#40;&#41;Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql), specificando la condivisione UNC che verrà utilizzata come cartella snapshot predefinita per ** \@ working_directory**. Se il server di distribuzione utilizza l'autenticazione di per la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connessione al server di pubblicazione, è necessario specificare anche il valore **0** per ** \@ security_mode** e le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] informazioni di accesso per l' ** \@ account di accesso** e la ** \@ password**.  
  
3.  Nel database master del server di pubblicazione eseguire [sp_adddistributor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistributor-transact-sql). Specificare la password complessa utilizzata nel passaggio 1 per la ** \@ password**. Questa password verrà utilizzata per la connessione del server di pubblicazione al server di distribuzione.  
  
4.  Nel server di pubblicazione eseguire [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql). Specificare il database da pubblicare per ** \@ dbname**, il tipo di replica per ** \@ optname**e il valore true per ** \@ value**.  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> Esempio (Transact-SQL)  
 Nell'esempio seguente viene illustrato come configurare la pubblicazione e la distribuzione a livello di programmazione. Il nome del server da configurare come server di pubblicazione e database di distribuzione locale viene specificato utilizzando variabili di scripting. La pubblicazione e la distribuzione della replica possono essere configurate a livello di programmazione tramite le stored procedure di replica.  
  
 [!code-sql[HowTo#AddDistPub](../../snippets/tsql/SQL15/replication/howto/tsql/adddistpub.sql#adddistpub)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
  
#### <a name="to-configure-publishing-and-distribution-on-a-single-server"></a>Per configurare la pubblicazione e la distribuzione su un singolo server  
  
1.  Creare una connessione al server tramite la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Creare un'istanza della classe <xref:Microsoft.SqlServer.Replication.ReplicationServer>. Passare il valore di <xref:Microsoft.SqlServer.Management.Common.ServerConnection> ottenuto al passaggio 1.  
  
3.  Creare un'istanza della classe <xref:Microsoft.SqlServer.Replication.DistributionDatabase>.  
  
4.  Impostare la proprietà <xref:Microsoft.SqlServer.Replication.DistributionDatabase.Name%2A> sul nome del database e la proprietà <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> sul valore di <xref:Microsoft.SqlServer.Management.Common.ServerConnection> ottenuto al passaggio 1.  
  
5.  Installare il server di distribuzione chiamando il metodo <xref:Microsoft.SqlServer.Replication.ReplicationServer.InstallDistributor%2A> . Passare l'oggetto <xref:Microsoft.SqlServer.Replication.DistributionDatabase> indicato nel passaggio 3.  
  
6.  Creare un'istanza della classe <xref:Microsoft.SqlServer.Replication.DistributionPublisher>.  
  
7.  Impostare le proprietà seguenti di <xref:Microsoft.SqlServer.Replication.DistributionPublisher>:  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> : nome del server di pubblicazione.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> : valore di <xref:Microsoft.SqlServer.Management.Common.ServerConnection> ottenuto al passaggio 1.  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.DistributionDatabase%2A> : nome del database creato al passaggio 5.  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.WorkingDirectory%2A> : condivisione utilizzata per accedere ai file snapshot.  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.PublisherSecurity%2A> : la modalità di sicurezza utilizzata durante la connessione al server di pubblicazione. È consigliato<xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> .  
  
8.  Chiamare il metodo <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Create%2A> .  
  
#### <a name="to-configure-publishing-and-distribution-using-a-remote-distributor"></a>Per configurare la pubblicazione e la distribuzione utilizzando un server di distribuzione remoto  
  
1.  Creare una connessione al server di distribuzione remoto tramite la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Creare un'istanza della classe <xref:Microsoft.SqlServer.Replication.ReplicationServer>. Passare il valore di <xref:Microsoft.SqlServer.Management.Common.ServerConnection> ottenuto al passaggio 1.  
  
3.  Creare un'istanza della classe <xref:Microsoft.SqlServer.Replication.DistributionDatabase>.  
  
4.  Impostare la proprietà <xref:Microsoft.SqlServer.Replication.DistributionDatabase.Name%2A> sul nome del database e la proprietà <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> sul valore di <xref:Microsoft.SqlServer.Management.Common.ServerConnection> ottenuto al passaggio 1.  
  
5.  Installare il server di distribuzione chiamando il metodo <xref:Microsoft.SqlServer.Replication.ReplicationServer.InstallDistributor%2A> . Specificare una password sicura (utilizzata dal server di pubblicazione per la connessione al server di distribuzione remoto) e l'oggetto <xref:Microsoft.SqlServer.Replication.DistributionDatabase> ottenuto al passaggio 3. Per altre informazioni, vedere [Sicurezza del database di distribuzione](security/secure-the-distributor.md).  
  
    > [!IMPORTANT]  
    >  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali, utilizzare i [servizi di crittografia](https://go.microsoft.com/fwlink/?LinkId=34733) forniti da [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows .NET Framework.  
  
6.  Creare un'istanza della classe <xref:Microsoft.SqlServer.Replication.DistributionPublisher>.  
  
7.  Impostare le proprietà seguenti di <xref:Microsoft.SqlServer.Replication.DistributionPublisher>:  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> : nome del server di pubblicazione locale.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> : valore di <xref:Microsoft.SqlServer.Management.Common.ServerConnection> ottenuto al passaggio 1.  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.DistributionDatabase%2A> : nome del database creato al passaggio 5.  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.WorkingDirectory%2A> : condivisione utilizzata per accedere ai file snapshot.  
  
    -   <xref:Microsoft.SqlServer.Replication.DistributionPublisher.PublisherSecurity%2A> : la modalità di sicurezza utilizzata durante la connessione al server di pubblicazione. È consigliato<xref:Microsoft.SqlServer.Replication.ConnectionSecurityContext.WindowsAuthentication%2A> .  
  
8.  Chiamare il metodo <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Create%2A> .  
  
9. Creare una connessione al server di pubblicazione locale tramite la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
10. Creare un'istanza della classe <xref:Microsoft.SqlServer.Replication.ReplicationServer>. Passare l'oggetto <xref:Microsoft.SqlServer.Management.Common.ServerConnection> indicato nel passaggio 9.  
  
11. Chiamare il metodo <xref:Microsoft.SqlServer.Replication.ReplicationServer.InstallDistributor%2A> . Passare il nome e la password del server di distribuzione remoto specificati al passaggio 5.  
  
    > [!IMPORTANT]  
    >  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali, utilizzare i [servizi di crittografia](https://go.microsoft.com/fwlink/?LinkId=34733) offerti da Windows .NET Framework.  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a>Esempio (RMO)  
 È possibile configurare a livello di programmazione la pubblicazione e la distribuzione della replica utilizzando gli oggetti RMO (Replication Management Objects).  
  
 [!code-csharp[HowTo#rmo_AddDistPub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_adddistpub)]  
  
 [!code-vb[HowTo#rmo_vb_AddDistPub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_adddistpub)]  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare e modificare le proprietà del server di distribuzione e dell'editore](view-and-modify-distributor-and-publisher-properties.md)   
 [Concetti relativi alle stored procedure del sistema di replica](concepts/replication-system-stored-procedures-concepts.md)   
 [Configurare la distribuzione](configure-distribution.md)   
 [Concetti di Replication Management Objects](concepts/replication-management-objects-concepts.md)   
 [Configurare la replica per Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) 
  
  
