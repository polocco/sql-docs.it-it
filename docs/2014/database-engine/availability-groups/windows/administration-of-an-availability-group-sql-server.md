---
title: Amministrazione di un gruppo di disponibilità (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], managing
ms.assetid: 0b7542fa-235e-413d-81bf-3eff9ee07480
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1bc670d47362f2e4170c9ae9a85b0588d07f1e4
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937226"
---
# <a name="administration-of-an-availability-group-sql-server"></a>Amministrazione di un gruppo di disponibilità (SQL Server)
  La gestione di un gruppo di disponibilità AlwaysOn esistente in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] prevede una o più delle attività seguenti:  
  
-   Modifica delle proprietà di una replica di disponibilità esistente, ad esempio per modificare l'accesso della connessione client (per la configurazione di repliche secondarie leggibili), attraverso la modifica della modalità di failover, della modalità di disponibilità o dell'impostazione del timeout di sessione.  
  
-   Aggiunta o rimozione di repliche secondarie.  
  
-   Aggiunta o rimozione di un database.  
  
-   Sospensione o ripresa di un database.  
  
-   Esecuzione di un failover manuale pianificato ( *failover manuale*) o di un failover manuale forzato ( *failover forzato*).  
  
-   Creazione o configurazione di un listener del gruppo di disponibilità.  
  
-   Gestione di [repliche secondarie leggibili](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) per un gruppo di disponibilità. Tale attività implica la configurazione di una o più repliche per l'accesso in sola lettura quando vengono eseguite nel ruolo secondario e la configurazione del routing di sola lettura.  
  
-   Gestione di [backup in repliche secondarie](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) per un gruppo di disponibilità. Tale attività implica la configurazione del percorso di esecuzione dei processi di backup e quindi la creazione di script dei processi di backup per implementare le preferenze di backup. È necessario creare script dei processi di backup per ogni database nel gruppo di disponibilità in ogni istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in cui è ospitata una replica di disponibilità.  
  
-   Eliminazione di un gruppo di disponibilità.  
  
-   Migrazione tra cluster di gruppi di disponibilità AlwaysOn per l'aggiornamento del sistema operativo  
  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Attività correlate  
 **Per configurare un gruppo di disponibilità esistente**  
  
-   [Aggiungere una replica secondaria a un gruppo di disponibilità &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Rimuovere una replica secondaria da un gruppo di disponibilità &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [Aggiungere un database a un gruppo di disponibilità &#40;SQL Server&#41;](availability-group-add-a-database.md)  
  
-   [Rimuovere un database secondario da un gruppo di disponibilità &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [Rimuovere un database primario da un gruppo di disponibilità &#40;SQL Server&#41;](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [Configurare i criteri di failover flessibili per controllare le condizioni per il failover automatico &#40;Gruppi di disponibilità AlwaysOn&#41;](configure-flexible-automatic-failover-policy.md)  
  
 **Per gestire un gruppo di disponibilità**  
  
-   [Configurare il backup su repliche di disponibilità &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [Eseguire un failover manuale pianificato di un gruppo di disponibilità &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [Eseguire un failover manuale forzato di un gruppo di disponibilità &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [Rimuovere un gruppo di disponibilità &#40;SQL Server&#41;](remove-an-availability-group-sql-server.md)  
  
 **Per gestire una replica di disponibilità**  
  
-   [Aggiungere una replica secondaria a un gruppo di disponibilità &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Creare un join di una replica secondaria a un gruppo di disponibilità &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Rimuovere una replica secondaria da un gruppo di disponibilità &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [Modificare la modalità di disponibilità di una replica di disponibilità &#40;SQL Server&#41;](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [Modificare la modalità di failover di una replica di disponibilità &#40;SQL Server&#41;](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [Configurare il backup su repliche di disponibilità &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [Configurare l'accesso in sola lettura in una replica di disponibilità &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [Configurare il routing di sola lettura per un gruppo di disponibilità &#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [Modificare il periodo di timeout della sessione per una replica di disponibilità &#40;SQL Server&#41;](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 **Per gestire un database di disponibilità**  
  
-   [Aggiungere un database a un gruppo di disponibilità &#40;SQL Server&#41;](availability-group-add-a-database.md)  
  
-   [Creare un join di un database secondario a un gruppo di disponibilità &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Rimuovere un database primario da un gruppo di disponibilità &#40;SQL Server&#41;](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [Rimuovere un database secondario da un gruppo di disponibilità &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [Sospendere un database di disponibilità &#40;SQL Server&#41;](suspend-an-availability-database-sql-server.md)  
  
-   [Riprendere un database di disponibilità &#40;SQL Server&#41;](resume-an-availability-database-sql-server.md)  
  
 **Per monitorare un gruppo di disponibilità**  
  
-   [Monitoraggio di Gruppi di disponibilità &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)  
  
 **Per supportare la migrazione di gruppi di disponibilità in un nuovo cluster WSFC (migrazione tra cluster)**  
  
-   [Modificare il contesto del cluster HADR dell'istanza del server &#40;SQL Server&#41;](change-the-hadr-cluster-context-of-server-instance-sql-server.md)  
  
-   [Portare un gruppo di disponibilità offline &#40;SQL Server&#41;](../../take-an-availability-group-offline-sql-server.md)  
  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Contenuto correlato  
  
-   **Blog:**  
  
     [Blog del team di SQL Server AlwaysOn: Blog ufficiale del team di SQL Server AlwaysOn](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [Pagina relativa ai blog del Servizio Supporto Tecnico Clienti per gli ingegneri di SQL Server](https://blogs.msdn.com/b/psssql/)  
  
-   **Video:**  
  
     [Pagina relativa alla prima parte riguardante l'introduzione della soluzione a disponibilità elevata di prossima generazione della serie AlwaysOn di Microsoft SQL Server nome in codice "Denali"](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Pagina relativa alla seconda parte riguardante la compilazione di una soluzione a disponibilità elevata critica tramite AlwasyOn della serie AlwaysOn di Microsoft SQL Server nome in codice "Denali"](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **White paper:**  
  
     [Pagina relativa ai white paper Microsoft per SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Pagina relativa ai white paper del team di consulenza clienti di SQL Server](http://sqlcat.com/)  
  
  
## <a name="see-also"></a>Vedere anche  
 [Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](always-on-availability-groups-sql-server.md)   
 [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Configurazione di un'istanza del server per Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](configuration-of-a-server-instance-for-always-on-availability-groups-sql-server.md)  
 [Creazione e configurazione di gruppi di disponibilità &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md)   
 [Repliche secondarie attive: repliche secondarie leggibili &#40;Gruppi di disponibilità AlwaysOn&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)   
 [Repliche secondarie attive: backup in repliche secondarie &#40;Gruppi di disponibilità AlwaysOn&#41;](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)  
 [Listener del gruppo di disponibilità, connettività client e failover dell'applicazione &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)   
 [Criteri AlwaysOn per problemi operativi con Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md)   
 [Monitoraggio di Gruppi di disponibilità &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)   
 [Gruppi di disponibilità AlwaysOn: interoperabilità &#40;SQL Server&#41;](always-on-availability-groups-interoperability-sql-server.md)   
 [Panoramica delle istruzioni Transact-SQL per Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](transact-sql-statements-for-always-on-availability-groups.md)   
 [Panoramica dei cmdlet di PowerShell per Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)  
  
