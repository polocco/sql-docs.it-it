---
title: Ripristinare un database in una nuova posizione (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring databases [SQL Server], moving
- database restores [SQL Server], creating new databases
- restoring [SQL Server], with move
- restoring databases [SQL Server], creating new databases
- database backups [SQL Server], creating new database from
- backing up databases [SQL Server], creating new database from
- restoring databases [SQL Server], renaming
- database creation [SQL Server], restoring with move
ms.assetid: 4da76d61-5e11-4bee-84f5-b305240d9f42
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 89b42f439b5622074327506b9f2ca2b2358cd12f
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84957252"
---
# <a name="restore-a-database-to-a-new-location-sql-server"></a>Ripristino di un database in una nuova posizione (SQL Server)
  In questo argomento viene descritto come ripristinare un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un nuovo percorso e facoltativamente rinominare il database, in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. È possibile spostare un database in un nuovo percorso di directory o crearne una copia nella stessa istanza server o in una diversa.  
  
 **Contenuto dell'articolo**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Prerequisiti](#Prerequisites)  
  
     [Indicazioni](#Recommendations)  
  
     [Sicurezza](#Security)  
  
-   **Per ripristinare un database in un nuovo percorso e facoltativamente rinominare il database utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   [Attività correlate](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   L'amministratore di sistema che esegue il ripristino di un backup completo del database deve essere l'unico utente collegato al database.  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Prerequisiti  
  
-   Nel modello di recupero con registrazione completa o con registrazione minima delle operazioni bulk, prima di poter ripristinare un database, è necessario eseguire il backup del log delle transazioni attivo. Per altre informazioni, vedere [Backup di un log delle transazioni &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md).  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Indicazioni  
  
-   Per ripristinare un database crittografato, è necessario poter accedere alla chiave asimmetrica o al certificato utilizzato per crittografare il database. Non è possibile effettuare l'operazione di ripristino del database senza almeno uno di questi due elementi. Di conseguenza, il certificato utilizzato per crittografare la chiave di crittografia del database deve essere conservato fino a quando il backup è necessario. Per altre informazioni, vedere [SQL Server Certificates and Asymmetric Keys](../security/sql-server-certificates-and-asymmetric-keys.md).  
  
-   Per ulteriori considerazioni sullo spostamento di un database, vedere [Copiare database tramite backup e ripristino](../databases/copy-databases-with-backup-and-restore.md).  
  
-   Se si ripristina un database di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] o versione successiva in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], il database viene aggiornato automaticamente. In genere, il database diventa subito disponibile. Se tuttavia un database di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] include indici full-text, questi vengono importati, reimpostati o ricompilati dal processo di aggiornamento, a seconda dell'impostazione della proprietà del server  **upgrade_option** . Se l'opzione di aggiornamento è impostata per l'importazione (**upgrade_option** = 2) o la ricompilazione (**upgrade_option** = 0), gli indici full-text non saranno disponibili durante l'aggiornamento. A seconda della quantità di dati indicizzati, l'importazione può richiedere diverse ore, mentre la ricompilazione può risultare dieci volte più lunga. Si noti inoltre che quando l'opzione di aggiornamento è impostata sull'importazione, gli indici full-text associati vengono ricompilati se non è disponibile un catalogo full-text. Per modificare l'impostazione della proprietà del server **upgrade_option** , usare [sp_fulltext_service](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql).  
  
###  <a name="security"></a><a name="Security"></a> Sicurezza  
 Per motivi di sicurezza, è consigliabile non collegare o ripristinare database da origini sconosciute o non attendibili. Tali database possono contenere codice dannoso che potrebbe eseguire codice [!INCLUDE[tsql](../../includes/tsql-md.md)] indesiderato o causare errori modificando lo schema o la struttura fisica di database. Prima di utilizzare un database da un'origine sconosciuta o non attendibile, eseguire [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) sul database in un server non di produzione ed esaminare il codice contenuto nel database, ad esempio le stored procedure o altro codice definito dall'utente.  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorizzazioni  
 Se il database da ripristinare non esiste, per eseguire un'operazione RESTORE l'utente deve disporre delle autorizzazioni CREATE DATABASE. Se il database esiste, le autorizzazioni per l'istruzione RESTORE vengono assegnate per impostazione predefinita ai membri dei ruoli predefiniti del server **sysadmin** e **dbcreator** e al proprietario (**dbo**) del database.  
  
 Le autorizzazioni per l'istruzione RESTORE vengono assegnate ai ruoli in cui le informazioni sull'appartenenza sono sempre disponibili per il server. Poiché è possibile controllare l'appartenenza ai ruoli predefiniti del database solo quando il database è accessibile e non è danneggiato, condizioni che non risultano sempre vere quando si esegue un'operazione RESTORE, i membri del ruolo predefinito del database **db_owner** non dispongono delle autorizzazioni per l'istruzione RESTORE.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-restore-a-database-to-a-new-location-and-optionally-rename-the-database"></a>Per ripristinare un database in un nuovo percorso e facoltativamente rinominare il database  
  
1.  Connettersi all'istanza appropriata di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]e quindi fare clic sul nome del server in Esplora oggetti per espandere l'albero del server.  
  
2.  Fare clic con il pulsante destro del mouse su **Database**, quindi scegliere **Ripristina database**. Verrà visualizzata la finestra di dialogo **Ripristina database** .  
  
3.  Per specificare l'origine e il percorso dei set di backup da ripristinare, nella pagina **Generale** , utilizzare la sezione **Origine** . Selezionare una delle opzioni seguenti:  
  
    -   **Database**  
  
         Selezionare il database da ripristinare dall'elenco a discesa. Nell'elenco sono inclusi solo i database di cui è stato eseguito il backup in base alla cronologia dei backup di **msdb** .  
  
    > [!NOTE]  
    >  Se il backup viene eseguito da un server diverso, il server di destinazione non disporrà delle informazioni della cronologia di backup per il database specificato. In questo caso, selezionare **Dispositivo** per specificare manualmente il file o il dispositivo da ripristinare.  
  
    1.  **Dispositivo**  
  
         Fare clic sul pulsante Sfoglia ( **...** ) per aprire la finestra di dialogo **Seleziona dispositivi di backup** . Nella casella **Tipi di supporti di backup** selezionare uno dei tipi di dispositivi elencati. Per selezionare uno o più dispositivi per la casella **Supporti di backup** , fare clic su **Aggiungi**.  
  
         Dopo avere aggiunto i dispositivi desiderati nella casella di riepilogo **Dispositivi di backup** , fare clic su **OK** per tornare alla pagina **Generale** .  
  
         Nella casella di riepilogo **Origine: Dispositivo: Database** selezionare il nome del database da ripristinare.  
  
         **Nota** Questo elenco è disponibile solo se si seleziona **Dispositivo** . Saranno disponibili solo i database che dispongono di backup sul dispositivo selezionato.  
  
4.  Nella sezione **Destinazione** , la casella **Database** viene popolata automaticamente con il nome del database da ripristinare. Per modificare il nome del database, immettere il nome nuovo nella casella **Database** .  
  
5.  Nella casella **Ripristina fino a** mantenere l'impostazione predefinita **Ultimo backup eseguito** oppure fare clic su **Cronologia** per accedere alla finestra di dialogo **Cronologia di backup** e selezionare manualmente un momento specifico per arrestare l'azione di recupero. Per ulteriori informazioni sulla designazione di un momento specifico, vedere [Backup Timeline](backup-timeline.md) .  
  
6.  Nella griglia **Selezionare i set di backup da ripristinare** selezionare i set di backup che si desidera ripristinare. In questa griglia vengono visualizzati i backup disponibili per il percorso specificato. Per impostazione predefinita, viene suggerito un piano di recupero. Per ignorare il piano di recupero suggerito, è possibile modificare le impostazioni selezionate nella griglia. I backup che dipendono dal ripristino di un backup precedente vengono automaticamente deselezionati quando il backup precedente è deselezionato.  
  
     Per informazioni sulle colonne nella griglia **Selezionare i set di backup da ripristinare** , vedere [Ripristina database &#40;pagina Generale&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).  
  
7.  Per specificare il nuovo percorso dei file di database, selezionare la pagina **File** , quindi fare clic su **Riloca tutti i file nella cartella**. Fornire un nuovo percorso per **Cartella file di dati** e **Cartella file di log**. Per altre informazioni su questa griglia, vedere [Ripristina database&#40;(pagina File)&#41;](restore-database-files-page.md).  
  
8.  Se lo si desidera, regolare le opzioni nella pagina **Opzioni** . Per altre informazioni su queste opzioni, vedere [Ripristina database &#40;(pagina Opzioni)&#41;](restore-database-options-page.md).  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-restore-a-database-to-a-new-location-and-optionally-rename-the-database"></a>Per ripristinare un database in un nuovo percorso e facoltativamente rinominare il database  
  
1.  Facoltativamente, determinare i nomi logici e fisici dei file del set di backup che contiene il backup di database completo da ripristinare. Questa istruzione restituisce un elenco dei file di database e di log contenuti nel set di backup. La sintassi di base è la seguente:  
  
     RESTORE FILELISTONLY FROM *<dispositivo_backup>* WITH FILE = *backup_set_file_number*  
  
     Dove *backup_set_file_number* indica la posizione del backup nel set di supporti. È possibile ottenere la posizione di un set di backup utilizzando l'istruzione [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) . Per altre informazioni, vedere "Specifica di un set di backup" in [Argomenti RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).  
  
     Questa istruzione supporta inoltre alcune opzioni WITH. Per altre informazioni, vedere [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql).  
  
2.  Eseguire l'istruzione [RESTORE DATABASE](/sql/t-sql/statements/restore-statements-transact-sql) per ripristinare il backup di database completo. Per impostazione predefinita, i file di dati e di log vengono ripristinati nei percorsi originali. Per modificare il percorso di un database, utilizzare l'opzione MOVE per spostare ogni file di database e per evitare conflitti con i file esistenti.  
  
     La sintassi [!INCLUDE[tsql](../../includes/tsql-md.md)] di base per il ripristino del database in un nuovo percorso e con un nuovo nome è la seguente:  
  
     RESTORE DATABASE *new_database_name*  
  
     FROM *backup_device* [ ,...*n* ]  
  
     [ WITH  
  
     {  
  
     [ **Recupero** | NORECOVERY  
  
     [ , ] [ FILE ={ *backup_set_file_number* | @*backup_set_file_number* } ]  
  
     [ , ] MOVE '*logical_file_name_in_backup*' TO '*operating_system_file_name*' [ ,...*n* ]  
  
     }  
  
     ;  
  
    > [!NOTE]  
    >  Quando si prepara lo spostamento di un database in un disco diverso, è necessario verificare che lo spazio disponibile sia sufficiente e identificare potenziali conflitti con i file esistenti. A tale scopo, utilizzare un'istruzione [RESTORE VERIFYONLY](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) che specifica gli stessi parametri MOVE che si intende utilizzare nell'istruzione RESTORE DATABASE.  
  
     Nella tabella seguente vengono descritti argomenti di questa istruzione RESTORE ai fini del ripristino di un database in un nuovo percorso. Per altre informazioni su questi argomenti, vedere [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).  
  
     *new_database_name*  
     Nuovo nome del database.  
  
    > [!NOTE]  
    >  Se il database viene ripristinato in una diversa istanza del server, è possibile utilizzare il nome di database originale anziché uno nuovo.  
  
     *backup_device* [ `,` ...*n* ]  
     Specifica un elenco di dispositivi di backup, da 1 a 64, delimitati da virgole da cui deve essere ripristinato il backup del database. È possibile specificare un dispositivo di backup fisico oppure un dispositivo di backup logico corrispondente, se già definito. Per specificare un dispositivo di backup fisico, utilizzare l'opzione DISK o TAPE:  
  
     { DISK | TAPE } `=` *physical_backup_device_name*  
  
     Per altre informazioni, vedere [Dispositivi di backup &#40;SQL Server&#41;](backup-devices-sql-server.md).  
  
     { **RECOVERY** | NORECOVERY }  
     Se per il database si utilizza il modello di recupero con registrazione completa, può essere necessario applicare i backup del log delle transazioni dopo il ripristino del database. In questo caso, specificare l'opzione NORECOVERY.  
  
     In caso contrario, utilizzare l'opzione RECOVERY (impostazione predefinita).  
  
     FILE = { *backup_set_file_number* | @*backup_set_file_number* }  
     Identifica il set di backup da ripristinare. Il valore *1* per **backup_set_file_number** indica il primo set di backup nel supporto di backup, mentre il valore *2* per **backup_set_file_number** indica il secondo set di backup. È possibile ottenere il valore *backup_set_file_number* di un backup usando l'istruzione [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) .  
  
     Se questa opzione non è specificata, per impostazione predefinita viene utilizzato il primo set di backup disponibili sul dispositivo di backup.  
  
     Per altre informazioni, vedere "Specifica di un set di backup" in [Argomenti RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).  
  
     Sposta **' *`logical_file_name_in_backup`* '** in **' *`operating_system_file_name`* '** [ `,` ... *n* ]  
     Specifica che il file di dati o di log specificato da *logical_file_name_in_backup* deve essere ripristinato nel percorso specificato da *operating_system_file_name*. Specificare un'istruzione MOVE per ogni file logico che si desidera ripristinare dal set di backup in un nuovo percorso.  
  
    |Opzione|Descrizione|  
    |------------|-----------------|  
    |*logical_file_name_in_backup*|Specifica il nome logico di un file di dati o di log da includere nel set di backup. Il nome di file logico di un file di dati o di log in un set di backup corrisponde al relativo nome logico nel database al momento della creazione del set di backup.<br /><br /> Nota: per ottenere un elenco dei file logici del set di backup, usare [RESTORE FILELISTONLY](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql).|  
    |*operating_system_file_name*|Specifica un nuovo percorso per il file indicato da *logical_file_name_in_backup*. Il file verrà ripristinato a questo percorso.<br /><br /> Facoltativamente, *operating_system_file_name* specifica un nuovo nome per il file ripristinato. Questo passaggio è necessario se si crea una copia di un database esistente nella stessa istanza del server.|  
    |*n*|Segnaposto tramite cui viene indicata la possibilità di specificare istruzioni MOVE aggiuntive.|  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> Esempio (Transact-SQL)  
 In questo esempio viene creato un nuovo database denominato `MyAdvWorks` ripristinando un backup del database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] in cui sono inclusi due file: [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Data e [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]_Log. In questo database viene utilizzato il modello di recupero con registrazione minima. Il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] è già presente nell'istanza del server, pertanto i file del backup devono essere ripristinati in un nuovo percorso. L'istruzione RESTORE FILELISTONLY viene utilizzata per stabilire il numero e i nomi dei file del database da ripristinare. Il backup del database corrisponde al primo set disponibile sul dispositivo.  
  
> [!NOTE]  
>  Gli esempi di backup e di ripristino del log delle transazioni, inclusi i ripristini temporizzati, utilizzano il database `MyAdvWorks_FullRM` creato da [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] esattamente come nell'esempio seguente basato su `MyAdvWorks` . Per usare il modello di recupero con registrazione completa è tuttavia necessario modificare il database `MyAdvWorks_FullRM` risultante usando l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente: ALTER DATABASE <nome_database> SET RECOVERY FULL.  
  
```sql  
USE master;  
GO  
-- First determine the number and names of the files in the backup.  
-- AdventureWorks2012_Backup is the name of the backup device.  
RESTORE FILELISTONLY  
   FROM AdventureWorks2012_Backup;  
-- Restore the files for MyAdvWorks.  
RESTORE DATABASE MyAdvWorks  
   FROM AdventureWorks2012_Backup  
   WITH RECOVERY,  
   MOVE 'AdventureWorks2012_Data' TO 'D:\MyData\MyAdvWorks_Data.mdf',   
   MOVE 'AdventureWorks2012_Log' TO 'F:\MyLog\MyAdvWorks_Log.ldf';  
GO  
  
```  
  
 Per un esempio relativo alla creazione di un backup completo del database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] , vedere [Creare un backup completo del database &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Attività correlate  
  
-   [Creazione di un backup completo del database &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)  
  
-   [Ripristinare un backup del database &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md)  
  
-   [Eseguire il backup di un log delle transazioni &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)  
  
-   [Ripristinare un backup del log delle transazioni &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Gestire i metadati quando si rende disponibile un database in un'altra istanza del server &#40;SQL Server&#41;](../databases/manage-metadata-when-making-a-database-available-on-another-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [Copiare database tramite backup e ripristino](../databases/copy-databases-with-backup-and-restore.md)  
  
  
