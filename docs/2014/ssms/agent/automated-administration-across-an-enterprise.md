---
title: Amministrazione automatizzata in un'organizzazione | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- enterprise automatic administration [SQL Server]
- multiserver administration [SQL Server]
- SQL Server Agent jobs, multiserver administration
- jobs [SQL Server Agent], multiserver administration
- master servers [SQL Server], about master servers
- target servers [SQL Server], about target servers
- master servers [SQL Server]
- multiple instances of SQL Server
- target servers [SQL Server]
ms.assetid: 44d8365b-42bd-4955-b5b2-74a8a9f4a75f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8df3e34c2c70c81f9710ade0d6855446b930fb50
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85011803"
---
# <a name="automated-administration-across-an-enterprise"></a>Amministrazione automatizzata in un'organizzazione
  L'automazione dell'amministrazione in più istanze di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene definita *amministrazione multiserver*. Utilizzare l'amministrazione multiserver per eseguire le operazioni seguenti:  
  
-   Gestione di due o più server.  
  
-   Pianificazione dei flussi di informazioni tra server aziendali per il data warehousing.  
  
> [!NOTE]  
>  Come parte dell'impegno costante di [!INCLUDE[msCoName](../../includes/msconame-md.md)] nel ridurre il costo totale di proprietà, in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] sono incluse due nuove caratteristiche: un metodo di gestione dei server denominato gestione basata su criteri e query multiserver che utilizzano server di configurazione e gruppi di server. Tali caratteristiche possono essere utilizzate con, o al posto di, alcune delle caratteristiche descritte in questo argomento. Per altre informazioni, vedere [amministrare i server usando la gestione basata su criteri](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md) e [amministrare più server tramite server di gestione centrale](../../relational-databases/administer-multiple-servers-using-central-management-servers.md).  
  
 Una soddisfacente configurazione di amministrazione multiserver è costituita da almeno un server master e almeno un server di destinazione. Il server master distribuisce processi ai server di destinazione e riceve eventi da tali server. Nel server master è inoltre archiviata la copia centrale delle definizioni di processo per i processi eseguiti nei server di destinazione. I server di destinazione stabiliscono connessioni periodiche al server master per aggiornare l'elenco dei processi pianificati. Se nel server master è presente un nuovo processo, questo viene scaricato dal server di destinazione. Dopo il completamento del processo, il server di destinazione stabilisce una nuova connessione al server master e trasmette lo stato del processo.  
  
 Nella figura seguente viene illustrata la relazione tra il server master e quello di destinazione:  
  
 ![Configurazione dell'amministrazione multiserver](../../database-engine/media/multisvr.gif "Configurazione dell'amministrazione multiserver")  
  
 Se si amministrano server di reparto in un'azienda di grandi dimensioni, è possibile definire i seguenti elementi:  
  
-   Un processo di backup composto da diversi passaggi.  
  
-   Gli operatori da notificare in caso di errore durante di backup.  
  
-   Una pianificazione dell'esecuzione per il processo di backup.  
  
 È possibile creare il processo di backup una sola volta nel server master e quindi integrare ogni server di reparto come server di destinazione. Dal momento dell'integrazione, in tutti i server di reparto verrà eseguito lo stesso processo di backup, anche se il processo sarà stato definito una volta sola.  
  
> [!NOTE]  
>  Le caratteristiche di amministrazione multiserver sono riservate ai membri del ruolo sysadmin. Un membro del ruolo sysadmin nel server di destinazione non può tuttavia modificare le operazioni eseguite in tale server dal server master. Questa misura di sicurezza impedisce l'eliminazione accidentale di passaggi del processo ed evita l'interruzione delle operazioni nel server di destinazione.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Creazione di un ambiente multiserver](create-a-multiserver-environment.md)  
 Contiene informazioni sulla creazione e la gestione di server master e di destinazione.  
  
 [Scegliere l'account di servizio SQL Server Agent adatto ad ambienti multiserver](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)  
 Contiene informazioni sull'impatto dell'utilizzo degli account di Windows non amministrativi o dell'account di sistema locale sul servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent negli ambienti multiserver.  
  
 [Impostazione delle opzioni di crittografia nei server di destinazione](set-encryption-options-on-target-servers.md)  
 Sono incluse informazioni sull'impostazione della sottochiave MsxEncryptChannelOptions del Registro di sistema di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent nei server di destinazione.  
  
 [Gestire i processi in un'azienda](manage-jobs-across-an-enterprise.md)  
 Contiene informazioni su verifica dello stato dei processi, modifica dei server di destinazione per i processi, sincronizzazione dei clock dei server e polling dei server master per determinare lo stato attuale dei processi.  
  
 [Risolvere i problemi relativi a processi multiserver che usano proxy](troubleshoot-multiserver-jobs-that-use-proxies.md)  
 Contiene informazioni sulla risoluzione dei problemi relativi a processi multiserver che utilizzano proxy con esito negativo.  
  
 [Polling dei server](poll-servers.md)  
 Contiene informazioni su come fare in modo, implicitamente ed esplicitamente, che i server di destinazione eseguano il polling dei server master per sincronizzare le informazioni sui processi.  
  
 [Gestione di eventi](manage-events.md)  
 Contiene informazioni sull'inoltro di eventi da server di destinazione a server master.  
  
 [Ottimizzazione dell'amministrazione automatizzata in un'organizzazione](tune-automated-administration-across-an-enterprise.md)  
 Sono incluse informazioni sull'utilizzo ottimale delle caratteristiche di ottimizzazione automatica di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]durante l'amministrazione automatizzata in un ambiente multiserver.  
  
## <a name="see-also"></a>Vedere anche  
 [Compatibilità con le versioni precedenti del motore di database di SQL Server](../../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [Registra server](../register-servers/register-servers.md)   
 [sp_add_targetservergroup &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql)   
 [sp_delete_targetserver &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql)   
 [sp_delete_targetservergroup &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql)   
 [sp_help_downloadlist &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-help-downloadlist-transact-sql)   
 [sp_help_jobserver &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-help-jobserver-transact-sql)   
 [sp_help_targetservergroup &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql)   
 [sp_resync_targetserver &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql)   
 [sp_update_targetservergroup &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql)   
 [dbo.sysjobservers &#40;&#41;Transact-SQL](/sql/relational-databases/system-tables/dbo-sysjobservers-transact-sql)   
 [sys.sysaccount di accesso &#40;&#41;Transact-SQL](/sql/relational-databases/system-compatibility-views/sys-syslogins-transact-sql)   
 [dbo.systargetServers &#40;&#41;Transact-SQL](/sql/relational-databases/system-tables/dbo-systargetservers-transact-sql)  
  
  
