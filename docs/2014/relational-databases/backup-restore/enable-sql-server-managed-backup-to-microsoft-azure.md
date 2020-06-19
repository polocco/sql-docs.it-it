---
title: Configurazione di SQL Server backup gestito in Azure | Microsoft Docs
ms.custom: ''
ms.date: 08/04/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 68ebb53e-d5ad-4622-af68-1e150b94516e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: abd183f1e7857a811194179f14f20b9fa599fa57
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84958371"
---
# <a name="setting-up-sql-server-managed-backup-to-azure"></a>Configurazione del backup gestito di SQL Server in Azure
  In questo argomento vengono illustrate due esercitazioni:  
  
 Configurare il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] a livello di database, abilitare la notifica tramite posta elettronica e monitorare l'attività di backup.  
  
 Configurare il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] a livello di istanza, abilitare la notifica tramite posta elettronica e monitorare l'attività di backup.  
  
 Per un'esercitazione sulla configurazione [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per i gruppi di disponibilità, vedere [configurazione di SQL Server Backup gestito Microsoft Azure per i gruppi di disponibilità](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).  
  
## <a name="setting-up-ss_smartbackup"></a>Configurazione del [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]  
  
### <a name="enable-and-configure-ss_smartbackup-for-a-database"></a>Abilitare e configurare [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per un database  
 In questa esercitazione vengono descritti i passaggi necessari per abilitare e configurare il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per un database (TestDB), nonché i passaggi per abilitare il monitoraggio dello stato di integrità del [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 **Autorizzazioni:**  
  
-   È richiesta l'appartenenza al ruolo **db_backupoperator** database, con autorizzazioni **ALTER ANY CREDENTIAL** e `EXECUTE` autorizzazioni per **sp_delete_backuphistory**stored procedure.  
  
-   Sono richieste le autorizzazioni **Select** per la funzione **smart_admin. fn_get_current_xevent_settings**.  
  
-   `EXECUTE`Sono necessarie le autorizzazioni per il stored procedure **smart_admin. sp_get_backup_diagnostics** . È inoltre richiesta l'autorizzazione `VIEW SERVER STATE` poiché vengono chiamati internamente altri oggetti di sistema che richiedono tale autorizzazione.  
  
-   `EXECUTE`Sono necessarie le autorizzazioni per le `smart_admin.sp_set_instance_backup` `smart_admin.sp_backup_master_switch` stored procedure e.  


1.  **Creare un account di archiviazione Microsoft Azure:** I backup vengono archiviati nel servizio di archiviazione Microsoft Azure. Se non si dispone già di un account, è necessario creare prima un account di archiviazione Microsoft Azure.
    - SQL Server 2014 USA i BLOB di pagine, che sono diversi dai BLOB in blocchi e di Accodamento. Pertanto, è necessario creare un account per utilizzo generico e non un account BLOB. Per altre informazioni, vedere [Informazioni sugli account di archiviazione di Azure](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).
    - Prendere nota del nome dell'account di archiviazione e delle chiavi di accesso. Le informazioni sul nome dell'account di archiviazione e sulla chiave di accesso vengono utilizzate per creare le credenziali SQL. Le credenziali SQL vengono utilizzate per l'autenticazione dell'account di archiviazione.  
 
2.  **Creare credenziali SQL:** Creare credenziali SQL usando il nome dell'account di archiviazione come identità e la chiave di accesso alle archiviazione come password.  
  
3.  **Verificare che SQL Server Agent servizio sia avviato e in esecuzione:**  Avviare SQL Server Agent se non è attualmente in esecuzione.  [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] è necessaria l'esecuzione di SQL Server Agent nell'istanza per poter eseguire le operazioni di backup.  Per assicurarsi che le operazioni in questione vengano eseguite regolarmente, è possibile impostare l'esecuzione automatica di SQL Server Agent.  
  
4.  **Determinare il periodo di conservazione:** determinare il periodo di conservazione per i file di backup. Il periodo di memorizzazione viene specificato in giorni in un intervallo compreso tra 1 e 30.  
  
5.  **Abilitare e configurare [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] :** avviare SQL Server Management Studio e connettersi all'istanza in cui è installato il database. Nella finestra Query eseguire l'istruzione riportata di seguito dopo aver modificato i valori per le opzioni relative al nome del database, alle credenziali SQL, al periodo di memorizzazione e alla crittografia in base alle esigenze:  
  
     Per ulteriori informazioni sulla creazione di un certificato per la crittografia, vedere il passaggio **creare un certificato di backup** in [creare un backup crittografato](create-an-encrypted-backup.md).  
  
    ```  
    Use msdb;  
    GO  
    EXEC smart_admin.sp_set_db_backup   
                    @database_name='TestDB'   
                    ,@retention_days=30   
                    ,@credential_name='MyCredential'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert'  
                    ,@enable_backup=1;  
    GO  
  
    ```  
  
     [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] ora è abilitato nel database specificato. L'inizio delle operazioni di backup nel database può richiedere fino a 15 minuti.  
  
6.  **Esaminare la configurazione predefinita degli eventi estesi:** esaminare le impostazioni degli eventi estesi eseguendo l'istruzione transact-SQL seguente.  
  
    ```  
    SELECT * FROM smart_admin.fn_get_current_xevent_settings()  
    ```  
  
     Verificare che gli eventi dei canali amministrativo, operativo e analitico siano abilitati per impostazione predefinita e che non possano essere disabilitati. Questa verifica dovrebbe essere sufficiente per monitorare gli eventi per i quali è richiesto un intervento manuale.  È possibile abilitare eventi di debug, ma nei canali di debug sono inclusi eventi informativi e di debug utilizzati dal [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per rilevare eventuali problemi e risolverli. Per altre informazioni, vedere [monitorare SQL Server backup gestito Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).  
  
7.  **Abilitare e configurare notifiche per lo stato di integrità:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] contiene una stored procedure che consente di creare un processo dell'agente per inviare notifiche via posta elettronica di errori o avvisi che potrebbero richiedere attenzione. Nei passaggi seguenti viene illustrato il processo per abilitare e configurare le notifiche tramite posta elettronica:  
  
    1.  Configurare Posta elettronica database se non è già abilitato nell'istanza. Per altre informazioni, vedere [Configurare Posta elettronica database](../database-mail/configure-database-mail.md).  
  
    2.  Configurare la notifica di SQL Server Agent per l'uso di Posta elettronica database. Per altre informazioni, vedere [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).  
  
    3.  **Abilitare le notifiche di posta elettronica per ricevere avvisi ed errori di backup:** nella finestra di query eseguire le istruzioni Transact-SQL seguenti:  
  
        ```  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email1;email2>'  
  
        ```  
  
         Per ulteriori informazioni e per uno script di esempio completo, vedere [monitorare SQL Server backup gestito Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).  
  
8.  **Visualizzare i file di backup nell'account di archiviazione Microsoft Azure** : connettersi all'account di archiviazione da SQL Server Management Studio o dal portale di gestione di Azure. Verrà visualizzato un contenitore per l'istanza di SQL Server in cui viene ospitato il database configurato per utilizzare il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. È inoltre possibile visualizzare un database e un backup del log entro 15 minuti dall'abilitazione del [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per il database.  
  
9. **Monitorare lo stato di integrità:**  è possibile eseguire il monitoraggio attraverso notifiche tramite posta elettronica configurate in precedenza o monitorare attivamente gli eventi registrati. Di seguito sono riportate alcune istruzioni Transact-SQL di esempio utilizzate per visualizzare gli eventi:  
  
    ```  
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
  
    ```  
  
    ```  
    -- to enable debug events  
    Use msdb;  
    Go  
             EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
    ```  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
  
    ```  
  
 I passaggi descritti in questa sezione riguardano in modo specifico la configurazione del [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per la prima volta nel database. È possibile modificare le configurazioni esistenti utilizzando lo stesso sistema stored procedure **smart_admin. sp_set_db_backup** e specificare i nuovi valori. Per ulteriori informazioni, vedere [SQL Server backup gestito in impostazioni di archiviazione e conservazione Microsoft Azure](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md).  
  
### <a name="enable-ss_smartbackup-for-the-instance-with-default-settings"></a>Abilitare il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per l'istanza con le impostazioni predefinite  
 In questa esercitazione vengono descritti i passaggi per abilitare e configurare [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per l'istanza, ovvero "istanza", \\ . Sono inclusi i passaggi per abilitare il monitoraggio dello stato di integrità del [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 **Autorizzazioni:**  
  
-   È richiesta l'appartenenza al ruolo **db_backupoperator** database, con autorizzazioni **ALTER ANY CREDENTIAL** e `EXECUTE` autorizzazioni per **sp_delete_backuphistory**stored procedure.  
  
-   Sono richieste le autorizzazioni **Select** per la funzione **smart_admin. fn_get_current_xevent_settings**.  
  
-   `EXECUTE`Sono necessarie le autorizzazioni per il stored procedure **smart_admin. sp_get_backup_diagnostics** . È inoltre richiesta l'autorizzazione `VIEW SERVER STATE` poiché vengono chiamati internamente altri oggetti di sistema che richiedono tale autorizzazione.  


1.  **Creare un account di archiviazione Microsoft Azure:** I backup vengono archiviati nel servizio di archiviazione Microsoft Azure. Se non si dispone già di un account, è necessario creare prima un account di archiviazione Microsoft Azure.
    - SQL Server 2014 USA i BLOB di pagine, che sono diversi dai BLOB in blocchi e di Accodamento. Pertanto, è necessario creare un account per utilizzo generico e non un account BLOB. Per altre informazioni, vedere [Informazioni sugli account di archiviazione di Azure](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/).
    - Prendere nota del nome dell'account di archiviazione e delle chiavi di accesso. Le informazioni sul nome dell'account di archiviazione e sulla chiave di accesso vengono utilizzate per creare le credenziali SQL. Le credenziali SQL vengono utilizzate per l'autenticazione dell'account di archiviazione.  
  
2.  **Creare credenziali SQL:** Creare credenziali SQL usando il nome dell'account di archiviazione come identità e la chiave di accesso alle archiviazione come password.  
  
3.  **Assicurarsi che il servizio SQL Server Agent sia avviato e in esecuzione:** se non è in esecuzione, avviare SQL Server Agent. [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] è necessaria l'esecuzione di SQL Server Agent nell'istanza per poter eseguire le operazioni di backup.  Per assicurarsi che le operazioni in questione vengano eseguite regolarmente, è possibile impostare l'esecuzione automatica di SQL Server Agent.  
  
4.  **Determinare il periodo di conservazione:** determinare il periodo di conservazione per i file di backup. Il periodo di memorizzazione viene specificato in giorni in un intervallo compreso tra 1 e 30. Dopo avere abilitato il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] a livello di istanza con le impostazioni predefinite, tutti i nuovi database creati successivamente erediteranno le impostazioni. Solo i database impostati sui modelli di recupero con registrazione completa o con registrazione minima delle operazioni bulk sono supportati e saranno configurati automaticamente. È possibile disabilitare il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per un database specifico in qualsiasi momento se non si vuole che [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] venga configurato. È inoltre possibile modificare la configurazione per un database specifico configurando il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] a livello di database.  
  
5.  **Abilitare e configurare [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] :** avviare SQL Server Management Studio e connettersi all'istanza di SQL Server. Nella finestra Query eseguire l'istruzione riportata di seguito dopo aver modificato i valori per le opzioni relative al nome del database, alle credenziali SQL, al periodo di memorizzazione e alla crittografia in base alle esigenze:  
  
     Per ulteriori informazioni sulla creazione di un certificato per la crittografia, vedere il passaggio **creare un certificato di backup** in [creare un backup crittografato](create-an-encrypted-backup.md).  
  
    ```  
    Use msdb;  
    Go  
       EXEC smart_admin.sp_set_instance_backup  
                     @enable_backup=1  
                    ,@retention_days=30   
                    ,@credential_name='sqlbackuptoURL'  
                    ,@encryption_algorithm ='AES_128'  
                    ,@encryptor_type= 'Certificate'  
                    ,@encryptor_name='MyBackupCert';  
    GO  
  
    ```  
  
     A questo punto il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] è abilitato nell'istanza.  
  
6.  Verificare le impostazioni di configurazione eseguendo l'istruzione Transact-SQL riportata di seguito:  
  
    ```  
    Use msdb;  
    GO  
    SELECT * FROM smart_admin.fn_backup_instance_config ();  
  
    ```  
  
7.  Creare un nuovo database nell'istanza. Eseguire l'istruzione Transact-SQL riportata di seguito per visualizzare le impostazioni di configurazione del [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per il database:  
  
    ```  
    Use msdb  
    GO  
    SELECT * FROM smart_admin.fn_backup_db_config('NewDB')  
    ```  
  
     La visualizzazione delle impostazioni e l'inizio delle operazioni di backup nel database può richiedere fino a 15 minuti.  
  
8.  **Abilitare e configurare notifiche per lo stato di integrità:** [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] contiene una stored procedure che consente di creare un processo dell'agente per inviare notifiche via posta elettronica di errori o avvisi che potrebbero richiedere attenzione.  Per ricevere notifiche di questo tipo, è necessario eseguire la stored procedure per creare un processo di SQL Server Agent. Nei passaggi seguenti viene illustrato il processo per abilitare e configurare le notifiche tramite posta elettronica:  
  
    1.  Configurare Posta elettronica database se non è già abilitato nell'istanza. Per altre informazioni, vedere [Configurare Posta elettronica database](../database-mail/configure-database-mail.md).  
  
    2.  Configurare la notifica di SQL Server Agent per l'uso di Posta elettronica database. Per altre informazioni, vedere [Configure SQL Server Agent Mail to Use Database Mail](../database-mail/configure-sql-server-agent-mail-to-use-database-mail.md).  
  
    3.  **Abilitare le notifiche di posta elettronica per ricevere avvisi ed errori di backup:** nella finestra di query eseguire le istruzioni Transact-SQL seguenti:  
  
        ```  
        EXEC msdb.smart_admin.sp_set_parameter  
        @parameter_name = 'SSMBackup2WANotificationEmailIds',  
        @parameter_value = '<email address>'  
  
        ```  
  
         Per ulteriori informazioni sul monitoraggio e su uno script di esempio completo, vedere [monitorare SQL Server backup gestito Microsoft Azure](sql-server-managed-backup-to-microsoft-azure.md).  
  
9. **Visualizzare i file di backup nell'account di archiviazione Microsoft Azure** : connettersi all'account di archiviazione da SQL Server Management Studio o dal portale di gestione di Azure. Verrà visualizzato un contenitore per l'istanza di SQL Server in cui viene ospitato il database configurato per utilizzare il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. È inoltre possibile visualizzare un database e un backup del log entro 15 minuti dalla creazione di un nuovo database.  
  
10. **Monitorare lo stato di integrità:**  è possibile eseguire il monitoraggio attraverso notifiche tramite posta elettronica configurate in precedenza o monitorare attivamente gli eventi registrati. Di seguito sono riportate alcune istruzioni Transact-SQL di esempio utilizzate per visualizzare gli eventi:  
  
    ```  
    --  view all admin events  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    DECLARE @eventresult TABLE  
    (event_type nvarchar(512),  
    event nvarchar (512),  
    timestamp datetime  
    )  
  
    INSERT INTO @eventresult  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek  
  
    SELECT * from @eventresult  
    WHERE event_type LIKE '%admin%'  
  
    ```  
  
    ```  
    --  to enable debug events  
    Use msdb;  
    Go  
             EXEC smart_admin.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
    ```  
  
    ```  
    --  View all events in the current week  
    Use msdb;  
    Go  
    DECLARE @startofweek datetime  
    DECLARE @endofweek datetime  
    SET @startofweek = DATEADD(Day, 1-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)   
    SET @endofweek = DATEADD(Day, 7-DATEPART(WEEKDAY, CURRENT_TIMESTAMP), CURRENT_TIMESTAMP)  
  
    EXEC smart_admin.sp_get_backup_diagnostics @begin_time = @startofweek, @end_time = @endofweek;  
  
    ```  
  
 Le impostazioni predefinite del [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] possono essere ignorate per un database specifico configurando le impostazioni in particolare a livello di database. È inoltre possibile sospendere e riprendere temporaneamente il servizio del [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Per altre informazioni, vedere [SQL Server backup gestito in impostazioni di archiviazione e memorizzazione Microsoft Azure](../../database-engine/sql-server-managed-backup-to-windows-azure-retention-and-storage-settings.md)  
  
  
