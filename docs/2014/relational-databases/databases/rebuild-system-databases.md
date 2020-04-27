---
title: Ricompilare database di sistema | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- master database [SQL Server], rebuilding
- REBUILDDATABASE parameter
- rebuilding databases, master
- system databases [SQL Server], rebuilding
ms.assetid: af457ecd-523e-4809-9652-bdf2e81bd876
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b58378e8ba2193a186fb58e3e784bf9bc3cb4d4c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62871278"
---
# <a name="rebuild-system-databases"></a>Ricompilare database di sistema
  Il processo di ricompilazione deve essere eseguito per correggere problemi di danneggiamento nei database di sistema [master](master-database.md), [model](model-database.md), [msdb](msdb-database.md)e [resource](resource-database.md) oppure per modificare le regole di confronto predefinite a livello di server. In questo argomento sono incluse istruzioni dettagliate per la ricompilazione di database di sistema in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 **Contenuto dell'articolo**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Prerequisiti](#Prerequisites)  
  
-   **Procedure:**  
  
     [Ricompilare database di sistema](#RebuildProcedure)  
  
     [Ricompilare il database resource](#Resource)  
  
     [Creare un nuovo database msdb](#CreateMSDB)  
  
-   **Completamento:**  
  
     [Risolvere gli errori di ricompilazione](#Troubleshoot)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitazioni e restrizioni  
 Quando vengono ricompilati, i database di sistema master, model, msdb e tempdb vengono eliminati e ricreati nel percorso originale. Se nell'istruzione di ricompilazione vengono specificate nuove regole di confronto, i database di sistema vengono creati utilizzando tale impostazione delle regole di confronto. Le eventuali modifiche apportate dall'utente ai database vanno perdute. Ad esempio, è possibile che siano presenti oggetti definiti dall'utente nel database master, processi pianificati nel database msdb o modifiche alle impostazioni predefinite nel database modello.  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Prerequisiti  
 Prima di ricompilare i database di sistema, effettuare le attività seguenti per assicurarsi che sia possibile ripristinare le impostazioni correnti dei database.  
  
1.  Registrare tutti i valori di configurazione a livello di server.  
  
    ```  
    SELECT * FROM sys.configurations;  
    ```  
  
2.  Registrare tutti i Service Pack e gli hotfix applicati all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e le regole di confronto correnti. È necessario riapplicare questi aggiornamenti dopo la ricompilazione dei database di sistema.  
  
    ```  
    SELECT  
    SERVERPROPERTY('ProductVersion ') AS ProductVersion,  
    SERVERPROPERTY('ProductLevel') AS ProductLevel,  
    SERVERPROPERTY('ResourceVersion') AS ResourceVersion,  
    SERVERPROPERTY('ResourceLastUpdateDateTime') AS ResourceLastUpdateDateTime,  
    SERVERPROPERTY('Collation') AS Collation;  
    ```  
  
3.  Registrare il percorso corrente di tutti i file di dati e di log relativi ai database di sistema. Dopo la ricompilazione, tutti i database di sistema vengono installati nel percorso originale. Se i file di dati o di log dei database di sistema sono stati spostati in un percorso diverso, è necessario spostarli di nuovo.  
  
    ```  
    SELECT name, physical_name AS current_file_location  
    FROM sys.master_files  
    WHERE database_id IN (DB_ID('master'), DB_ID('model'), DB_ID('msdb'), DB_ID('tempdb'));  
    ```  
  
4.  Individuare il backup corrente dei database master, modello e msdb.  
  
5.  Se l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è configurata come server di distribuzione repliche, individuare il backup corrente del database di distribuzione.  
  
6.  Assicurarsi di disporre delle autorizzazioni appropriate per ricompilare i database di sistema. Per eseguire questa operazione, è necessario essere membro del ruolo predefinito del server `sysadmin`. Per altre informazioni, vedere [Ruoli a livello di server](../security/authentication-access/server-level-roles.md).  
  
7.  Verificare che le copie dei file modello di log e dati dei database master, modello e msdb esistano nel server locale. Il percorso predefinito per i file modello è C:\Programmi\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn\Templates. Questi file vengono utilizzati durante il processo di ricompilazione e devono essere presenti affinché l'installazione venga completata correttamente. Se non sono disponibili, eseguire la caratteristica Ripristina del programma di installazione oppure copiarli manualmente dal supporto di installazione. Per individuare i file nel supporto di installazione, passare alla directory della piattaforma appropriata (x86 o x64), quindi a setup\sql_engine_core_inst_msi\Pfiles\SqlServr\MSSQL.X\MSSQL\Binn\Templates.  
  
##  <a name="rebuild-system-databases"></a><a name="RebuildProcedure"></a> Ricompilare database di sistema  
 La procedura seguente consente di ricompilare i database di sistema master, modello, msdb e tempdb. Non è possibile specificare i database di sistema da ricompilare. Per le istanze cluster, questa procedura deve essere eseguita nel nodo attivo e la risorsa di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel gruppo di applicazioni cluster corrispondente deve essere portata offline prima di eseguire la procedura.  
  
 Con questa procedura non viene ricompilato il database delle risorse (resource). Vedere la sezione "Procedura per la ricompilazione del database resource" più avanti in questo argomento.  
  
#### <a name="to-rebuild-system-databases-for-an-instance-of-sql-server"></a>Per ricompilare i database di sistema per un'istanza di SQL Server:  
  
1.  Inserire il supporto di installazione di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] nell'unità disco oppure dal prompt dei comandi passare alla directory in cui si trova il file setup.exe nel server locale. Il percorso predefinito sul server è C:\Programmi\Microsoft SQL Server\120\Setup Bootstrap\Release.  
  
2.  Da una finestra del prompt dei comandi immettere il comando seguente. Le parentesi quadre indicano i parametri facoltativi e non devono essere digitate. Se si utilizza un sistema operativo Windows con Controllo account utente abilitato, per eseguire il programma di installazione è necessario disporre di privilegi elevati. Il prompt dei comandi deve essere eseguito come Amministratore.  
  
     `Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName /SQLSYSADMINACCOUNTS=accounts [ /SAPWD= StrongPassword ] [ /SQLCOLLATION=CollationName]`  
  
    |Nome parametro|Descrizione|  
    |--------------------|-----------------|  
    |/QUIET o /Q|Specifica che il programma di installazione verrà eseguito senza alcuna interfaccia utente.|  
    |/ACTION=REBUILDDATABASE|Specifica che il programma di installazione dovrà ricreare i database di sistema.|  
    |/INSTANCENAME =*NomeIstanza*|Nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per l'istanza predefinita, immettere MSSQLSERVER.|  
    |/SQLSYSADMINACCOUNTS=*accounts*|Specifica i gruppi o i singoli account di Windows da aggiungere al ruolo predefinito del server `sysadmin`. Se si specificano più account, separarli con uno spazio. Ad esempio, immettere **BUILTIN\Administrators MyDomain\MyUser**. Quando si specifica un account che contiene uno spazio vuoto all'interno del nome dell'account, racchiudere l'account tra doppie virgolette. Immettere ad esempio `NT AUTHORITY\SYSTEM`.|  
    |[ /SAPWD=*StrongPassword* ]|Specifica la password per l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `sa` account. Questo parametro è necessario se l'istanza usa la modalità autenticazione mista (autenticazione di[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e di Windows).<br /><br /> ** \* Nota sulla sicurezza \* \* ** L' `sa` account è un account noto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ed è spesso indirizzato da utenti malintenzionati. È estremamente importante utilizzare una password complessa per l'accesso all'account `sa`.<br /><br /> Non specificare questo parametro per la modalità di autenticazione di Windows.|  
    |[ /SQLCOLLATION=*CollationName* ]|Vengono specificate nuove regole di confronto a livello di server. Questo parametro è facoltativo e, Se non viene specificato, verranno utilizzate le regole di confronto correnti del server.<br /><br /> ** \* Importante \* \* ** La modifica delle regole di confronto a livello di server non comporta la modifica delle regole di confronto dei database utente esistenti. Tutti i nuovi database utente creati utilizzeranno le nuove regole di confronto per impostazione predefinita.<br /><br /> Per altre informazioni, vedere [Impostare o modificare le regole di confronto del server](../collations/set-or-change-the-server-collation.md).|  
  
3.  Al termine della ricompilazione dei database di sistema, verrà visualizzato di nuovo il prompt dei comandi senza messaggi. Esaminare il file di log Summary.txt per verificare che il processo sia stato completato correttamente. Il percorso di questo file è C:\Programmi\Microsoft SQL Server\120\Setup Bootstrap\Logs.  
  
## <a name="post-rebuild-tasks"></a>Attività successive alla ricompilazione  
 Al termine della ricompilazione del database, potrebbe essere necessario effettuare le attività aggiuntive seguenti:  
  
-   Ripristinare i backup completi più recenti dei database master, modello e msdb. Per altre informazioni, vedere [Backup e ripristino di Database di sistema &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md).  
  
    > [!IMPORTANT]  
    >  Se sono state modificate le regole di confronto del server, non ripristinare i database di sistema. In caso contrario, le nuove regole di confronto verranno sostituite con quelle precedenti.  
  
     Se non è disponibile alcun backup oppure se il backup ripristinato non è aggiornato, ricreare le eventuali voci mancanti. Ad esempio, ricreare tutte le voci mancanti per i database utente, i dispositivi di backup, gli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , gli endpoint e così via. Il modo più efficace per ricreare le voci consiste nell'eseguire gli script originali con cui sono state create.  
  
> [!IMPORTANT]  
>  È consigliabile proteggere gli script per impedire che il contenuto venga modificato da utenti non autorizzati.  
  
-   Se l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è configurata come server di distribuzione repliche, è necessario ripristinare il database di distribuzione. Per altre informazioni, vedere [Eseguire il backup e ripristino di database replicati](../replication/administration/back-up-and-restore-replicated-databases.md).  
  
-   Spostare i database di sistema nei percorsi registrati in precedenza. Per altre informazioni vedere l'articolo [Spostare i database di sistema](system-databases.md).  
  
-   Verificare che i valori di configurazione a livello di server corrispondano ai valori registrati in precedenza.  
  
##  <a name="rebuild-the-resource-database"></a><a name="Resource"></a>Ricompilare il database Resource  
 Con la procedura seguente viene ricompilato il database di sistema delle risorse. Quando si ricompila il database delle risorse, tutti i Service Pack e gli hotfix vanno persi e devono pertanto essere riapplicati.  
  
#### <a name="to-rebuild-the-resource-system-database"></a>Per ricompilare il database di sistema resource:  
  
1.  Avviare il programma di installazione di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] (setup.exe) dal supporto di distribuzione.  
  
2.  Nell'area di navigazione sinistra fare clic su **Manutenzione**, quindi su **Ripristina**.  
  
3.  Verranno eseguite la regola di supporto dell'installazione e le routine dei file per garantire che nel sistema siano installati i prerequisiti e che il computer soddisfi le regole di convalida dell'installazione. Fare clic su **OK** o **Installa** per continuare.  
  
4.  Nella pagina Seleziona istanza selezionare l'istanza da ripristinare, quindi fare clic su **Avanti**.  
  
5.  Verranno eseguite le regole di ripristino per convalidare l'operazione. Per continuare, fare clic su **Avanti**.  
  
6.  Nella pagina **Ripristino** scegliere **Ripristina**. Nella pagina Operazione completata è indicato che l'operazione è stata completata.  
  
##  <a name="create-a-new-msdb-database"></a><a name="CreateMSDB"></a> Creare un nuovo database msdb  
 Se il `msdb` database è danneggiato e non si dispone di un backup del `msdb` database, è possibile crearne uno nuovo `msdb` tramite lo script **lo instmsdb comporterà** .  
  
> [!WARNING]  
>  La ricompilazione `msdb` del database tramite lo script **lo instmsdb comporterà** eliminerà tutte le informazioni archiviate in `msdb` , ad esempio processi, avvisi, operatori, piani di manutenzione, cronologia di backup, impostazioni della gestione basata su criteri, posta elettronica database, prestazioni data warehouse e così via.  
  
1.  Arrestare tutti i servizi che si connettono al [!INCLUDE[ssDE](../../includes/ssde-md.md)], tra cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, [!INCLUDE[ssRS](../../includes/ssrs.md)], [!INCLUDE[ssIS](../../includes/ssis-md.md)]e tutte le applicazioni in cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene utilizzato come archivio dati.  
  
2.  Avviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dalla riga di comando utilizzando il comando `NET START MSSQLSERVER /T3608`  
  
     Per altre informazioni, vedere [Avviare, arrestare, sospendere, riprendere, riavviare i servizi SQL Server](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).  
  
3.  In un'altra finestra della riga di comando `msdb` scollegare il database eseguendo il comando seguente, sostituendo * \<ServerName>* con l'istanza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]di:`SQLCMD -E -S<servername> -dmaster -Q"EXEC sp_detach_db msdb"`  
  
4.  Utilizzando Esplora risorse, rinominare i file `msdb` di database. Per impostazione predefinita, tali file si trovano nella sottocartella DATA per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
5.  Utilizzando Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , arrestare e riavviare normalmente il servizio [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
6.  In una finestra della riga di comando connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ed eseguire il comando `SQLCMD -E -S<servername> -i"C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Install\instmsdb.sql" -o" C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Install\instmsdb.out"`  
  
     Sostituire * \<ServerName>* con l'istanza di [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Utilizzare il percorso del file system dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
7.  Tramite Blocco note di Windows, aprire il file **instmsdb.out** e verificare la presenza di eventuali errori nell'output.  
  
8.  Applicare di nuovo qualsiasi Service Pack o hotfix installati nell'istanza.  
  
9. Ricreare il contenuto dell'utente archiviato nel `msdb` database, ad esempio processi, avvisi e così via.  
  
10. Eseguire il backup del database di `msdb` .  
  
##  <a name="troubleshoot-rebuild-errors"></a><a name="Troubleshoot"></a> Risolvere gli errori di ricompilazione  
 Gli errori di sintassi e altri errori di runtime vengono visualizzati nella finestra del prompt dei comandi. Esaminare l'istruzione di installazione per rilevare gli errori di sintassi seguenti:  
  
-   Barra (/) mancante prima di ogni nome di parametro.  
  
-   Segno di uguale (=) mancante tra il nome e il valore del parametro.  
  
-   Presenza di spazi tra il nome del parametro e il segno di uguale.  
  
-   Presenza di virgole (,) o di altri caratteri non specificati nella sintassi.  
  
 Al termine dell'operazione di ricompilazione, esaminare i log di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per rilevare eventuali errori. Il percorso predefinito dei log è C:\Programmi\Microsoft SQL Server\120\Setup Bootstrap\Logs. Per individuare il file di log che contiene i risultati del processo di ricompilazione, passare alla cartella Logs dal prompt dei comandi, quindi eseguire `findstr /s RebuildDatabase summary*.*`. Con questa ricerca sarà possibile trovare tutti i file di log che contengono i risultati della ricompilazione dei database di sistema. Aprire i file di log ed esaminare i messaggi di errore pertinenti.  
  
## <a name="see-also"></a>Vedi anche  
 [Database di sistema](system-databases.md)  
  
  
