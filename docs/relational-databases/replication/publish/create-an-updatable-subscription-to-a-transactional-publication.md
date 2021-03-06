---
title: Creare una sottoscrizione aggiornabile (transazionale)
description: Informazioni su come creare una sottoscrizione aggiornabile di una pubblicazione transazionale per SQL Server.
ms.custom: seo-lt-2019
ms.date: 11/20/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- updatable transactional subscriptions
- updateable transactional subscriptions, SSMS
ms.assetid: f9ef89ed-36f6-431b-8843-25d445ec137f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0d28fec80479a8eec877452763e78d4fadfa3d2c
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942838"
---
# <a name="create-an-updatable-subscription-to-a-transactional-publication"></a>Creazione di una sottoscrizione aggiornabile di una pubblicazione transazionale
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
> [!NOTE]  
>  Questa funzionalità continuerà a essere supportata nelle versioni di [!INCLUDE[ssNoVersion_md](../../../includes/ssnoversion-md.md)] dalla 2012 alla 2016.  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  

La replica transazionale consente di ripropagare al server di pubblicazione le modifiche apportate a un Sottoscrittore utilizzando sottoscrizioni ad aggiornamento immediato o ad aggiornamento in coda. È possibile creare una sottoscrizione ad aggiornamento a livello di programmazione tramite le stored procedure di replica. 
 
Configurare le sottoscrizioni aggiornabili nella pagina **Sottoscrizioni aggiornabili** della **Creazione guidata nuova sottoscrizione**. Questa pagina è disponibile solo se è stata attivata una pubblicazione transazionale per le sottoscrizioni aggiornabili. Per altre informazioni sull'abilitazione delle sottoscrizione aggiornabili, vedere [Abilitare le sottoscrizioni aggiornabili per le pubblicazioni transazionali](../../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md).   
  
## <a name="configure-an-updatable-subscription-from-the-publisher"></a>Configurare una sottoscrizione aggiornabile dal server di pubblicazione  

1. Connettersi al server di pubblicazione in Microsoft SQL Server Management Studio e quindi espandere il nodo del server.
2. Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .
3. Fare clic col pulsante destro del mouse su una pubblicazione transazionale abilitata per l'aggiornamento di sottoscrizioni e quindi scegliere **Nuove sottoscrizioni**.
4. Seguire i passaggi della procedura guidata per specificare le opzioni della sottoscrizione, ad esempio il server nel quale deve essere eseguito l'agente di distribuzione.
5. Nella pagina **Sottoscrizioni aggiornabili** della **Creazione guidata nuova sottoscrizione** verificare che **Replica** sia selezionato.
6. Selezionare un'opzione nell'elenco a discesa **Commit nel server di pubblicazione**:

    * Per usare sottoscrizioni ad aggiornamento immediato, selezionare **Commit delle modifiche simultaneo**. Se si seleziona questa opzione e la pubblicazione consente sottoscrizioni ad aggiornamento in coda (impostazione predefinita per le pubblicazioni create con la Creazione guidata nuova pubblicazione), la proprietà della sottoscrizione **update_mode** è impostata su **failover**. Questa modalità consente di passare all'aggiornamento in coda in un momento successivo se necessario.

    * Per usare sottoscrizioni ad aggiornamento in coda, selezionare **Accoda le modifiche ed esegui il commit appena possibile**. Se si seleziona questa opzione e la pubblicazione consente sottoscrizioni ad aggiornamento immediato (impostazione predefinita per le pubblicazioni create con Creazione guidata nuova pubblicazione) e se il Sottoscrittore esegue SQL Server 2005 o versione successiva, la proprietà della sottoscrizione **update_mode** è impostata su queued failover. Questa modalità consente di passare all'aggiornamento immediato in un momento successivo se necessario.

    Per altre informazioni su come cambiare modalità di aggiornamento, vedere [Passare da una modalità di aggiornamento all'altra per una sottoscrizione transazionale aggiornabile](../../../relational-databases/replication/administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).

7. La pagina **Account di accesso per sottoscrizioni aggiornabili** viene visualizzata per le sottoscrizioni che usano l'aggiornamento immediato o la cui proprietà **update_mode** è impostata su **queued failover**. Nella pagina **Account di accesso per sottoscrizioni aggiornabili** specificare un server collegato tramite il quale vengono eseguite le connessioni al server di pubblicazione per sottoscrizioni ad aggiornamento immediato. Le connessioni vengono utilizzate dai trigger che si attivano presso il Sottoscrittore e propagano le modifiche al server di pubblicazione. Selezionare una delle opzioni seguenti:

    * **Crea un server collegato che stabilisce la connessione utilizzando l'autenticazione di SQL Server.** Selezionare questa opzione se non è stato definito un server remoto o un server collegato tra il Sottoscrittore e il server di pubblicazione. Durante la replica verrà creato automaticamente un server collegato. È necessario che l'account specificato esista già nel server di pubblicazione.

    * **Usa un server collegato o remoto già definito** Selezionare questa opzione se è stato definito un server remoto o un server collegato tra il Sottoscrittore e il server di pubblicazione tramite [sp_addserver (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md), [sp_addlinkedserver (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md), SQL Server Management Studio o un altro metodo.

    Per informazioni sulle autorizzazioni necessarie per l'account di accesso al server collegato, vedere **Sottoscrizioni ad aggiornamento in coda** in [descrizione collegamento](../../../relational-databases/replication/security/secure-the-subscriber.md).

8. Completare la procedura guidata.

## <a name="configure-an-updatable-subscription-from-the-subscriber"></a>Configurare una sottoscrizione aggiornabile dal Sottoscrittore


1. Connettersi al Sottoscrittore in SQL Server Management Studio e quindi espandere il nodo del server.
2. Espandere la cartella **Replica** .
3. Fare clic col pulsante destro del mouse sulla cartella **Sottoscrizioni locali** e quindi scegliere **Nuove sottoscrizioni**.
4. Nella pagina **Pubblicazione** della **Creazione guidata nuova sottoscrizione** selezionare **Trova server di pubblicazione SQL Server** nell'elenco a discesa **Server di pubblicazione**.
5. Connettersi al server di pubblicazione nella finestra di dialogo **Connetti a server** .
6. Nella pagina **Pubblicazione** selezionare una pubblicazione transazionale abilitata per l'aggiornamento di sottoscrizioni.
7. Seguire i passaggi della procedura guidata per specificare le opzioni della sottoscrizione, ad esempio il server nel quale deve essere eseguito l'agente di distribuzione.
8. Nella pagina **Sottoscrizioni aggiornabili** della Creazione guidata nuova sottoscrizione verificare che **Replica** sia selezionato.
9. Selezionare un'opzione nell'elenco a discesa **Commit nel server di pubblicazione**:

    * Per usare sottoscrizioni ad aggiornamento immediato, selezionare **Commit delle modifiche simultaneo**. Se si seleziona questa opzione e la pubblicazione consente sottoscrizioni ad aggiornamento in coda (impostazione predefinita per le pubblicazioni create con la Creazione guidata nuova pubblicazione), la proprietà della sottoscrizione **update_mode** è impostata su **failover**. Questa modalità consente di passare all'aggiornamento in coda in un momento successivo se necessario.

    * Per usare sottoscrizioni ad aggiornamento in coda, selezionare **Accoda le modifiche ed esegui il commit appena possibile**. Se si seleziona questa opzione e la pubblicazione consente sottoscrizioni ad aggiornamento immediato (impostazione predefinita per le pubblicazioni create con Creazione guidata nuova pubblicazione) e se il Sottoscrittore esegue SQL Server 2005 o versione successiva, la proprietà della sottoscrizione **update_mode** è impostata su **queued failover**. Questa modalità consente di passare all'aggiornamento immediato in un momento successivo se necessario.

    Per altre informazioni su come cambiare modalità di aggiornamento, vedere [Passare da una modalità di aggiornamento all'altra per una sottoscrizione transazionale aggiornabile](../../../relational-databases/replication/administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).

10. La pagina **Account di accesso per sottoscrizioni aggiornabili** viene visualizzata per le sottoscrizioni che usano l'aggiornamento immediato o la cui proprietà **update_mode** è impostata su **failover**. Nella pagina **Account di accesso per sottoscrizioni aggiornabili** specificare un server collegato tramite il quale vengono eseguite le connessioni al server di pubblicazione per sottoscrizioni ad aggiornamento immediato. Le connessioni vengono utilizzate dai trigger che si attivano presso il Sottoscrittore e propagano le modifiche al server di pubblicazione. Selezionare una delle opzioni seguenti:

    * **Crea un server collegato che stabilisce la connessione utilizzando l'autenticazione di SQL Server.** Selezionare questa opzione se non è stato definito un server remoto o un server collegato tra il Sottoscrittore e il server di pubblicazione. Durante la replica verrà creato automaticamente un server collegato. È necessario che l'account specificato esista già nel server di pubblicazione.

    * **Usa un server collegato o remoto già definito** Selezionare questa opzione se è stato definito un server remoto o un server collegato tra il Sottoscrittore e il server di pubblicazione tramite [sp_addserver (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md), [sp_addlinkedserver (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md), SQL Server Management Studio o un altro metodo.

    Per informazioni sulle autorizzazioni necessarie per l'account di accesso al server collegato, vedere **Sottoscrizioni ad aggiornamento in coda** in [descrizione collegamento](../../../relational-databases/replication/security/secure-the-subscriber.md).

11. Completare la procedura guidata.

## <a name="create-an-immediate-updating-pull-subscription"></a>Creare una sottoscrizione pull ad aggiornamento immediato ##

1. Nel server di pubblicazione eseguire [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)per verificare che la pubblicazione supporti le sottoscrizioni ad aggiornamento immediato. 

    * Se il valore di `allow_sync_tran` nel set di risultati è `1`, la pubblicazione supporta le sottoscrizioni ad aggiornamento immediato.
    * Se il valore di `allow_sync_tran` nel set di risultati è `0`, sarà necessario creare nuovamente la pubblicazione abilitando le sottoscrizioni ad aggiornamento immediato.

2. Nel server di pubblicazione eseguire [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)per verificare che la pubblicazione supporti le sottoscrizioni pull. 

    * Se il valore di `allow_pull` nel set di risultati è `1`, la pubblicazione supporta le sottoscrizioni pull.
    * Se il valore di `allow_pull` è `0`, eseguire [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), specificando `allow_pull` per `@property` e `true` per `@value`. 

3. Nel Sottoscrittore eseguire [sp_addpullsubscription](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md). Specificare `@publisher` e `@publication`, nonché uno dei seguenti valori per `@update_mode`:

    * `sync tran` - abilita la sottoscrizione per l'aggiornamento immediato.
    * `failover` - abilita la sottoscrizione per l'aggiornamento immediato sostituito dall'aggiornamento in coda in caso di failover.
    > [!NOTE]  
    >  `failover` richiede che la pubblicazione sia abilitata anche per le sottoscrizioni ad aggiornamento in coda. 
 
4. Nel Sottoscrittore eseguire [sp_addpullsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md). Specificare le opzioni seguenti:

    * I parametri `@publisher`, `@publisher_db`e `@publication` . 
    * Le credenziali di Microsoft Windows per l'esecuzione dell'agente di distribuzione nel Sottoscrittore per `@job_login``@job_password`. 

    > [!NOTE]  
    > Per le connessioni attivate con l'autenticazione integrata di Windows vengono sempre usate le credenziali di Windows specificate da `@job_login` e `@job_password`. L'agente di distribuzione attiva sempre la connessione locale al Sottoscrittore utilizzando l'autenticazione integrata di Windows. Per impostazione predefinita, l'agente si connette al server di distribuzione con l'autenticazione integrata di Windows. 
 
    * (Facoltativo) Il valore `0` per `@distributor_security_mode` e le informazioni sull'account di accesso di Microsoft SQL Server per `@distributor_login` e `@distributor_password`, se è necessario usare l'autenticazione di SQL Server per la connessione al server di distribuzione. 
    * Specificare una pianificazione per il processo dell'agente di distribuzione da eseguire per la sottoscrizione. 

5. Nel database di sottoscrizione del Sottoscrittore eseguire [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md). Specificare `@publisher`, `@publication`, il nome del database di pubblicazione per `@publisher_db`e uno dei valori seguenti per `@security_mode`: 

    * `0` - Usare l'autenticazione di SQL Server quando si eseguono aggiornamenti nel server di pubblicazione. Questa opzione richiede di specificare un account di accesso valido nel server di pubblicazione per `@login` e `@password`.
    * `1` - Usare il contesto di sicurezza dell'utente che esegue le modifiche nel Sottoscrittore quando ci si connette al server di pubblicazione. Per informazioni sulle restrizioni correlate a questa modalità di sicurezza, vedere [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md) .
    * `2` - Usare un account di accesso esistente e definito dall'utente per il server collegato, creato con [sp_addlinkedserver](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md).

6. Nel server di pubblicazione eseguire [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) specificando `@publication`, `@subscriber`, `@destination_db`, il valore pull per `@subscription_type`e lo stesso valore specificato al passaggio 3 per `@update_mode`. La sottoscrizione pull verrà registrata nel server di pubblicazione. 


## <a name="create-an-immediate-updating-push-subscription"></a>Creare una sottoscrizione push ad aggiornamento immediato ##

1. Nel server di pubblicazione eseguire [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)per verificare che la pubblicazione supporti le sottoscrizioni ad aggiornamento immediato. 

    * Se il valore di `allow_sync_tran` nel set di risultati è `1`, la pubblicazione supporta le sottoscrizioni ad aggiornamento immediato.
    * Se il valore di `allow_sync_tran` nel set di risultati è `0`, sarà necessario creare nuovamente la pubblicazione abilitando le sottoscrizioni ad aggiornamento immediato.

2. Nel server di pubblicazione eseguire [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)per verificare che la pubblicazione supporti le sottoscrizioni push. 

    * Se il valore di `allow_push` nel set di risultati è `1`, la pubblicazione supporta le sottoscrizioni push.
    * Se il valore di `allow_push` è `0`, eseguire [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), specificando `allow_push` per `@property` e `true` per `@value`. 

3. Nel server di pubblicazione eseguire [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Specificare `@publication`, `@subscriber`, `@destination_db`, nonché uno dei seguenti valori per `@update_mode`:

    * `sync tran` - abilita il supporto per l'aggiornamento immediato.
    * `failover` - abilita il supporto per l'aggiornamento immediato sostituito dall'aggiornamento in coda in caso di failover.

    > [!NOTE]  
    >  `failover` richiede che la pubblicazione sia abilitata anche per le sottoscrizioni ad aggiornamento in coda. 
 
4. Nel server di pubblicazione eseguire [sp_addpushsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md). Specificare i parametri seguenti:

    * `@subscriber`, `@subscriber_db`e `@publication`. 

    * Le credenziali di Windows usate per eseguire l'agente di distribuzione nel server di distribuzione per `@job_login` e `@job_password`. 

    > [!NOTE]  
    >  Per le connessioni attivate con l'autenticazione integrata di Windows vengono sempre usate le credenziali di Windows specificate da `@job_login` e `@job_password`. L'agente di distribuzione esegue sempre la connessione locale al server di distribuzione utilizzando l'autenticazione integrata di Windows. Per impostazione predefinita, l'agente si connette al Sottoscrittore utilizzando l'autenticazione integrata di Windows. 

    * (Facoltativo) Il valore `0` per `@subscriber_security_mode` e le informazioni sull'account di accesso di SQL Server per `@subscriber_login` e `@subscriber_password`, se è necessario usare l'autenticazione di SQL Server per la connessione al Sottoscrittore. 
    * Specificare una pianificazione per il processo dell'agente di distribuzione da eseguire per la sottoscrizione.

5. Nel database di sottoscrizione del Sottoscrittore eseguire [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md). Specificare `@publisher`, `@publication`, il nome del database di pubblicazione per `@publisher_db`e uno dei valori seguenti per `@security_mode`: 

     * `0` - Usare l'autenticazione di SQL Server quando si eseguono aggiornamenti nel server di pubblicazione. Questa opzione richiede di specificare un account di accesso valido nel server di pubblicazione per `@login` e `@password`.
     * `1` - Usare il contesto di sicurezza dell'utente che esegue le modifiche nel Sottoscrittore quando ci si connette al server di pubblicazione. Per informazioni sulle restrizioni correlate a questa modalità di sicurezza, vedere [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md) .
     * `2` - Usare un account di accesso esistente e definito dall'utente per il server collegato, creato con [sp_addlinkedserver](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md).


## <a name="create-a-queued-updating-pull-subscription"></a>Creare una sottoscrizione pull ad aggiornamento in coda

1. Nel server di pubblicazione eseguire [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)per verificare che la pubblicazione supporti le sottoscrizioni ad aggiornamento in coda. 

    * Se il valore di `allow_queued_tran` nel set di risultati è `1`, la pubblicazione supporta le sottoscrizioni ad aggiornamento immediato.
    * Se il valore di `allow_queued_tran` nel set di risultati è `0`, sarà necessario creare nuovamente la pubblicazione abilitando le sottoscrizioni ad aggiornamento in coda.

2. Nel server di pubblicazione eseguire [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)per verificare che la pubblicazione supporti le sottoscrizioni pull. 

    * Se il valore di `allow_pull` nel set di risultati è `1`, la pubblicazione supporta le sottoscrizioni pull.
    * Se il valore di `allow_pull` è `0`, eseguire [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), specificando `allow_pull` per `@property` e `true` per `@value`. 

3. Nel Sottoscrittore eseguire [sp_addpullsubscription](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md). Specificare `@publisher` e `@publication`, nonché uno dei seguenti valori per `@update_mode`:

    * `queued tran` - abilita la sottoscrizione per l'aggiornamento in coda.
    * `queued failover` - abilita il supporto per l'aggiornamento in coda sostituito dall'aggiornamento immediato in caso di failover.

    > [!NOTE]  
    >  `queued failover` richiede che la pubblicazione sia abilitata anche per le sottoscrizioni ad aggiornamento immediato. Per eseguire il failover all'aggiornamento immediato, è necessario usare [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md) per definire le credenziali con cui replicare nel server di pubblicazione le modifiche apportate al Sottoscrittore.
 
4. Nel Sottoscrittore eseguire [sp_addpullsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md). Specificare i parametri seguenti:

    * @publisher, `@publisher_db`e `@publication`. 
    * Le credenziali di Windows per l'esecuzione dell'agente di distribuzione nel Sottoscrittore per `@job_login` e `@job_password`. 

    > [!NOTE]  
    > Per le connessioni attivate con l'autenticazione integrata di Windows vengono sempre usate le credenziali di Windows specificate da `@job_login` e `@job_password`. L'agente di distribuzione attiva sempre la connessione locale al Sottoscrittore utilizzando l'autenticazione integrata di Windows. Per impostazione predefinita, l'agente si connette al server di distribuzione con l'autenticazione integrata di Windows. 
 
    * (Facoltativo) Il valore `0` per `@distributor_security_mode` e le informazioni sull'account di accesso di SQL Server per `@distributor_login` e `@distributor_password`, se è necessario usare l'autenticazione di SQL Server per la connessione al server di distribuzione. 
    * Specificare una pianificazione per il processo dell'agente di distribuzione da eseguire per la sottoscrizione.

5. Nel server di pubblicazione eseguire [sp_addsubscriber](../../../relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql.md) per registrare il Sottoscrittore nel server di pubblicazione specificando `@publication`, `@subscriber`, `@destination_db`, il valore pull per `@subscription_type`e lo stesso valore specificato al passaggio 3 per `@update_mode`. La sottoscrizione pull verrà registrata nel server di pubblicazione. 


## <a name="create-a-queued-updating-push-subscription"></a>Creare una sottoscrizione push ad aggiornamento in coda 

1. Nel server di pubblicazione eseguire [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)per verificare che la pubblicazione supporti le sottoscrizioni ad aggiornamento in coda. 

    * Se il valore di allow_queued_tran nel set di risultati è 1, la pubblicazione supporta le sottoscrizioni ad aggiornamento immediato.
    * Se il valore di allow_queued_tran nel set di risultati è 0, sarà necessario creare nuovamente la pubblicazione abilitando le sottoscrizioni ad aggiornamento in coda. Per altre informazioni, vedere Procedura: Abilitare le sottoscrizioni aggiornabili per le pubblicazioni transazionali (Programmazione Transact-SQL della replica).

2. Nel server di pubblicazione eseguire [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)per verificare che la pubblicazione supporti le sottoscrizioni push. 

    * Se il valore di `allow_push` nel set di risultati è `1`, la pubblicazione supporta le sottoscrizioni push.
    * Se il valore di `allow_push` è `0`, eseguire [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), specificando allow_push per `@property` e `true` per `@value`. 

3. Nel server di pubblicazione eseguire [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Specificare `@publication`, `@subscriber`, `@destination_db`, nonché uno dei seguenti valori per `@update_mode`:

    * `queued tran` - abilita la sottoscrizione per l'aggiornamento in coda.
    * `queued failover` - abilita il supporto per l'aggiornamento in coda sostituito dall'aggiornamento immediato in caso di failover.

    > [!NOTE]  
    > Con l'opzione queued failover è necessario che la pubblicazione sia abilitata anche per le sottoscrizioni ad aggiornamento immediato. Per eseguire il failover all'aggiornamento immediato, è necessario usare [sp_link_publication](../../../relational-databases/system-stored-procedures/sp-link-publication-transact-sql.md) per definire le credenziali con cui replicare nel server di pubblicazione le modifiche apportate al Sottoscrittore.

4. Nel server di pubblicazione eseguire [sp_addpushsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md). Specificare i parametri seguenti:

    * `@subscriber`, `@subscriber_db`e `@publication`. 
    * Le credenziali di Windows usate per eseguire l'agente di distribuzione nel server di distribuzione per `@job_login` e `@job_password`. 

    > [!NOTE]  
    > Per le connessioni attivate con l'autenticazione integrata di Windows vengono sempre usate le credenziali di Windows specificate da `@job_login` e `@job_password`. L'agente di distribuzione esegue sempre la connessione locale al server di distribuzione utilizzando l'autenticazione integrata di Windows. Per impostazione predefinita, l'agente si connette al Sottoscrittore con l'autenticazione integrata di Windows. 
 
    * (Facoltativo) Il valore `0` per `@subscriber_security_mode` e le informazioni sull'account di accesso di SQL Server per `@subscriber_login` e `@subscriber_password`, se è necessario usare l'autenticazione di SQL Server per la connessione al Sottoscrittore. 
    * Specificare una pianificazione per il processo dell'agente di distribuzione da eseguire per la sottoscrizione.

## <a name="set-queued-updating-conflict-resolution-options"></a>Impostare le opzioni di risoluzione dei conflitti per l'aggiornamento in coda 
Per impostare le opzioni di risoluzione dei conflitti per le pubblicazioni che supportano sottoscrizioni ad aggiornamento in coda, usare la pagina **Opzioni sottoscrizione** della finestra di dialogo **Proprietà pubblicazione - \<Publication>** . Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
  
1.  Nella pagina **Opzioni sottoscrizione** della finestra di dialogo **Proprietà pubblicazione - \<Publication>** selezionare uno dei valori seguenti per l'opzione **Criteri di risoluzione dei conflitti**:  
  
    -   **Mantieni la modifica del server di pubblicazione**    
    -   **Mantieni la modifica del Sottoscrittore**    
    -   **Reinizializza la sottoscrizione**  


## <a name="example"></a>Esempio

In questo esempio viene creata una sottoscrizione pull ad aggiornamento immediata di una pubblicazione che supporta le sottoscrizioni ad aggiornamento immediato. I valori per l'account di accesso e la relativa password vengono specificati in fase di esecuzione tramite variabili di scripting sqlcmd.

> [!NOTE]  
>  Questo script usa le variabili di scripting di sqlcmd, nel formato `$(MyVariable)`. Per informazioni su come usare le variabili di scripting nella riga di comando e in SQL Server Management Studio, vedere la sezione **Esecuzione di script di replica** nell'argomento [Concetti di base relativi alle stored procedure del sistema di replica](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md).

```sql
-- Execute this batch at the Subscriber.
DECLARE @publication AS sysname;
DECLARE @publicationDB AS sysname;
DECLARE @publisher AS sysname;
DECLARE @login AS sysname;
DECLARE @password AS nvarchar(512);
SET @publication = N'AdvWorksProductTran';
SET @publicationDB = N'AdventureWorks2008R2';
SET @publisher = $(PubServer);
SET @login = $(Login);
SET @password = $(Password);

-- At the subscription database, create a pull subscription to a transactional 
-- publication using immediate updating with queued updating as a failover.
EXEC sp_addpullsubscription 
    @publisher = @publisher, 
    @publication = @publication, 
    @publisher_db = @publicationDB, 
    @update_mode = N'failover', 
    @subscription_type = N'pull';

-- Add an agent job to synchronize the pull subscription, 
-- which uses Windows Authentication when connecting to the Distributor.
EXEC sp_addpullsubscription_agent 
    @publisher = @publisher, 
    @publisher_db = @publicationDB, 
    @publication = @publication,
    @job_login = @login,
    @job_password = @password; 

-- Add a Windows Authentication-based linked server that enables the 
-- Subscriber-side triggers to make updates at the Publisher. 
EXEC sp_link_publication 
    @publisher = @publisher, 
    @publication = @publication,
    @publisher_db = @publicationDB, 
    @security_mode = 0,
    @login = @login,
    @password = @password;
GO

USE AdventureWorks2008R2;
GO

-- Execute this batch at the Publisher.
DECLARE @publication AS sysname;
DECLARE @subscriptionDB AS sysname;
DECLARE @subscriber AS sysname;
SET @publication = N'AdvWorksProductTran'; 
SET @subscriptionDB = N'AdventureWorks2008R2Replica'; 
SET @subscriber = $(SubServer);

-- At the Publisher, register the subscription, using the defaults.
USE [AdventureWorks2008R2]
EXEC sp_addsubscription 
    @publication = @publication, 
    @subscriber = @subscriber, 
    @destination_db = @subscriptionDB, 
    @subscription_type = N'pull', 
    @update_mode = N'failover';
GO
``` 


## <a name="see-also"></a>Vedere anche

[Updatable Subscriptions for Transactional Replication](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
[Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)   
[Utilizzo di sqlcmd con variabili di scripting](../../../ssms/scripting/sqlcmd-use-with-scripting-variables.md)   


