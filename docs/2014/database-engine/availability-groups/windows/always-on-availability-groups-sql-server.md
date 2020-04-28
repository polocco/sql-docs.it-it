---
title: Gruppi di disponibilità Always On (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], about
- secondary replicas, see Availability Groups [SQL Server]
- availability [SQL Server]
- AlwaysOn [SQL Server], see Availability Groups [SQL Server]
- Availability Groups [SQL Server]
ms.assetid: aa427606-8422-4656-b205-c9e665ddc8c1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2e040fb9c05683be9d737ea134710c03d36317cd
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "75229006"
---
# <a name="always-on-availability-groups-sql-server"></a>Gruppi di disponibilità Always On (SQL Server)
  La funzionalità [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] è una soluzione di disponibilità elevata e recupero di emergenza che offre un'alternativa di livello enterprise al mirroring del database. Introdotta in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] aumenta la disponibilità di un set di database utente per un'azienda. Un *gruppo di disponibilità* supporta un ambiente di failover per un set discreto di database utente, noti come *database di disponibilità*, su cui si verifica il failover. Un gruppo di disponibilità supporta un set di database primari di lettura e scrittura e da uno a otto set di database secondari corrispondenti. Facoltativamente, i database secondari possono essere resi disponibili per l'accesso di sola lettura e/o alcune operazioni di backup.  
  
 Per un gruppo di disponibilità il failover si verifica al livello di una replica di disponibilità. I failover non sono dovuti a database ritenuti sospetti in seguito a una perdita di un file di dati, all'eliminazione di un database o al danneggiamento di un log delle transazioni.  
  
  
##  <a name="benefits"></a><a name="Benefits"></a>Vantaggi  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] è incluso un ampio set di opzioni con cui è possibile migliorare la disponibilità del database e che consentono un uso ottimale delle risorse. I componenti chiave sono i seguenti:  
  
-   Supporta fino a nove repliche di disponibilità. Una *replica di disponibilità* è la creazione di un'istanza di un gruppo di disponibilità ospitata da un'istanza specifica di SQL Server e che mantiene una copia locale di ogni database di disponibilità che appartiene al gruppo di disponibilità. Ogni gruppo di disponibilità supporta una replica primaria e fino a otto repliche secondarie. Per altre informazioni, vedere [Panoramica di Gruppi di disponibilità Always On &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).  
  
    > [!IMPORTANT]  
    >  Ogni replica di disponibilità deve risiedere su un nodo diverso di un singolo cluster WSFC (Windows Server Failover Clustering). Per ulteriori informazioni su prerequisiti, restrizioni e consigli per i gruppi di disponibilità, vedere [prerequisiti, restrizioni e consigli per i gruppi di disponibilità always on; SQL Server;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
-   Supporta modalità di disponibilità alternative, come segue:  
  
    -   *Modalità con commit asincrono*. La modalità di disponibilità è una soluzione di recupero di emergenza che offre risultati ottimali quando le repliche di disponibilità vengono distribuite a distanze considerevoli.  
  
    -   *Modalità con commit sincrono*. La modalità di disponibilità privilegia la disponibilità elevata e la protezione dei dati rispetto alle prestazioni, aumentando tuttavia la latenza delle transazioni. Un determinato gruppo di disponibilità è in grado di supportare fino a tre repliche di disponibilità con commit sincrono, inclusa la replica primaria corrente.  
  
     Per altre informazioni, vedere [modalità di disponibilità. Gruppi di disponibilità Always On;](availability-modes-always-on-availability-groups.md).  
  
-   Supporta molti formati di failover del gruppo di disponibilità: failover automatico, failover manuale pianificato (in genere definito semplicemente "failover manuale") e failover manuale forzato (in genere definito semplicemente "failover forzato"). Per ulteriori informazioni, vedere [failover e modalità di failover. Gruppi di disponibilità Always On;](failover-and-failover-modes-always-on-availability-groups.md).  
  
-   Permette di configurare una determinata replica di disponibilità per supportare una o entrambe le seguenti funzionalità delle repliche secondarie attive:  
  
    -   Accesso alla connessione in sola lettura che permette connessioni in sola lettura alla replica per accedere e leggere i relativi database quando viene eseguita come replica secondaria. Per altre informazioni, vedere [repliche secondarie attive: repliche secondarie leggibili; Gruppi di disponibilità Always On](https://msdn.microsoft.com/library/ff878253.aspx)).  
  
    -   Esecuzione di operazioni di backup sui relativi database quando viene eseguita come replica secondaria. Per altre informazioni, vedere [repliche secondarie attive: backup in repliche secondarie](https://msdn.microsoft.com/library/ff878253.aspx).  
  
     L'uso delle funzionalità secondarie attive migliora l'efficienza IT e riduce i costi tramite un migliore uso delle risorse dell'hardware secondario. Inoltre, la ripartizione delle applicazioni con finalità di lettura e dei processi di backup alle repliche secondarie permette di migliorare le prestazioni sulla replica primaria.  
  
-   Supporta un listener del gruppo di disponibilità per ogni gruppo di disponibilità. Un *listener del gruppo di disponibilità* è un nome del server a cui i client possono connettersi per accedere a un database in una replica primaria o secondaria di un gruppo di disponibilità AlwaysOn. I listener del gruppo di disponibilità indirizzano le connessioni in ingresso alla replica primaria o a una replica secondaria in sola lettura. Il listener permette un failover rapido dell'applicazione dopo il failover del gruppo di disponibilità. Per altre informazioni, vedere [listener del gruppo di disponibilità, connettività client e failover dell'applicazione; SQL Server;](../../listeners-client-connectivity-application-failover.md).  
  
-   Supporta criteri di failover flessibili per un maggiore controllo del failover del gruppo di disponibilità. Per ulteriori informazioni, vedere [failover e modalità di failover. Gruppi di disponibilità Always On;](failover-and-failover-modes-always-on-availability-groups.md).  
  
-   Supporta il ripristino automatico della pagina per la protezione da danneggiamenti di pagina. Per ulteriori informazioni, vedere [la pagina relativa alla correzione automatica della pagina &#40;per i gruppi di disponibilità e il mirroring del database](../../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md).  
  
-   Supporta crittografia e compressione, che forniscono il trasporto sicuro a prestazioni elevate.  
  
-   Fornisce un set integrato di strumenti per semplificare la distribuzione e la gestione dei gruppi di disponibilità, tra cui:  
  
    -   [!INCLUDE[tsql](../../../includes/tsql-md.md)] per la creazione e la gestione di gruppi di disponibilità. Per ulteriori informazioni, vedere [Cenni preliminari sulle istruzioni Transact-SQL per Always on gruppo di disponibilità. SQL Server;](transact-sql-statements-for-always-on-availability-groups.md).  
  
    -   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] , come segue:  
  
        -   La [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] permette di creare e configurare un gruppo di disponibilità. In alcuni ambienti, questa procedura guidata prepara automaticamente i database secondari e avvia la sincronizzazione dei dati per ognuno di essi. Per ulteriori informazioni, vedere [utilizzare la finestra di dialogo nuovo gruppo di disponibilità. SQL Server Management Studio;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md).  
  
        -   La [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] aggiunge uno o più database primari a un gruppo di disponibilità esistente. In alcuni ambienti, questa procedura guidata prepara automaticamente i database secondari e avvia la sincronizzazione dei dati per ognuno di essi. Per altre informazioni, vedere [Usare la procedura guidata Aggiungi database a gruppo di disponibilità (SQL Server)](availability-group-add-database-to-group-wizard.md).  
  
        -   La [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] aggiunge una o più repliche secondarie a un gruppo di disponibilità esistente. In alcuni ambienti, questa procedura guidata prepara automaticamente i database secondari e avvia la sincronizzazione dei dati per ognuno di essi. Per ulteriori informazioni, vedere [utilizzare la procedura guidata Aggiungi replica a gruppo di disponibilità. SQL Server Management Studio;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md).  
  
        -   La [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)] avvia un failover manuale su un gruppo di disponibilità. A seconda della configurazione e dello stato della replica secondaria specificata come destinazione del failover, la procedura guidata può eseguire un failover pianificato o un failover manuale forzato. Per ulteriori informazioni, vedere [utilizzare la procedura guidata failover del gruppo di disponibilità. SQL Server Management Studio;](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md).  
  
    -   [!INCLUDE[ssAoDash](../../../includes/ssaodash-md.md)] esegue il monitoraggio dei gruppi di disponibilità AlwaysOn, delle repliche di disponibilità e dei database di disponibilità e valuta risultati per i criteri AlwaysOn. Per ulteriori informazioni, vedere [utilizzare il dashboard AlwaysOn. SQL Server Management Studio;](use-the-always-on-dashboard-sql-server-management-studio.md).  
  
    -   Nel riquadro Dettagli Esplora oggetti sono visualizzate informazioni di base sui gruppi di disponibilità esistenti. Per ulteriori informazioni, vedere [utilizzare i dettagli Esplora oggetti per monitorare il gruppo di disponibilità. SQL Server Management Studio;](use-object-explorer-details-to-monitor-availability-groups.md).  
  
    -   Cmdlet di PowerShell. Per altre informazioni, vedere [Cenni preliminari sui cmdlet di PowerShell per Always on gruppi di disponibilità. SQL serve;](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md).  
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a>Termini e definizioni  
 gruppo di disponibilità  
 Contenitore per un set di database, i *database di disponibilità*, su cui si verifica il failover.  
  
 database di disponibilità  
 Database che appartiene a un gruppo di disponibilità. Per ogni database di disponibilità, il gruppo di disponibilità gestisce una sola copia di lettura e scrittura (il *database primario*) e da una a otto copie di sola lettura (*database secondari*).  
  
 database primario  
 Copia di lettura e scrittura di un database di disponibilità.  
  
 database secondario  
 Copia di sola lettura di un database di disponibilità.  
  
 replica di disponibilità  
 Istanza di un gruppo di disponibilità ospitata da un'istanza specifica di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che mantiene una copia locale di ogni database di disponibilità che appartiene al gruppo di disponibilità. Sono disponibili due tipi di replica di disponibilità: una *replica primaria* e da una a otto *repliche secondarie*.  
  
 replica primaria  
 Replica di disponibilità che rende disponibili i database primari per le connessioni in lettura e scrittura dai client e invia i record del log delle transazioni per ogni database primario a ogni replica secondaria.  
  
 replica secondaria  
 Replica di disponibilità che mantiene una copia secondaria di ogni database di disponibilità e che rappresenta la destinazione potenziale del failover per il gruppo di disponibilità. Facoltativamente, una replica secondaria può supportare l'accesso in sola lettura ai database secondari creando backup sui database secondari.  
  
 listener del gruppo di disponibilità  
 Nome del server a cui i client possono connettersi per accedere a un database in una replica primaria o secondaria di un gruppo di disponibilità Always On. I listener del gruppo di disponibilità indirizzano le connessioni in ingresso alla replica primaria o a una replica secondaria in sola lettura.  
  
> [!NOTE]  
>  Per ulteriori informazioni, vedere [Panoramica di gruppi di disponibilità AlwaysOn; SQL serve;](overview-of-always-on-availability-groups-sql-server.md).  
  
##  <a name="interoperability-and-coexistence-with-other-database-engine-features"></a><a name="Interoperability"></a> Interoperabilità e coesistenza con altre funzionalità del motore di database  
 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] può essere usato con le funzionalità o i componenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]seguenti:  
  
-   [Informazioni su Change Data Capture; SQL Server;](../../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
-   [Informazioni su Rilevamento modifiche; SQL serve;](../../../relational-databases/track-changes/about-change-tracking-sql-server.md)  
  
-   [Database indipendenti](../../../relational-databases/databases/contained-databases.md)  
  
-   [Crittografia del database](../../../relational-databases/security/encryption/transparent-data-encryption.md)  
  
-   [Snapshot del database](database-snapshots-with-always-on-availability-groups-sql-server.md)  
  
-   [FILESTREAM](../../../relational-databases/blob/filestream-sql-server.md)  
  
-   [FileTable](../../../relational-databases/blob/filetables-sql-server.md)  
  
-   [Log shipping](../../log-shipping/about-log-shipping-sql-server.md)  
  
-   [Archivio BLOB remoto (RBS)](../../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)  
  
-   [Replica](../../install-windows/install-sql-server-replication.md)  
  
-   [Service Broker](../../configure-windows/sql-server-service-broker.md)  
  
-   [SQL Server Agent](../../../ssms/agent/sql-server-agent.md)  
  
-   [Reporting Services](reporting-services-with-always-on-availability-groups-sql-server.md)  
  
> [!WARNING]  
>  Per informazioni sulle restrizioni e le limitazioni per l'uso di [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]altre funzionalità con, vedere [Always on gruppi di disponibilità: interoperabilità. SQL Server;](always-on-availability-groups-interoperability-sql-server.md).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Attività correlate  
  
-   [Introduzione con Always On gruppi di disponibilità; SQL Server;](getting-started-with-always-on-availability-groups-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Contenuto correlato  
  
-   **Blog:**  
  
     [Blog del team di SQL Server Always On: Blog ufficiale del team SQL Server AlwaysOn](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [Pagina relativa ai blog del Servizio Supporto Tecnico Clienti per gli ingegneri di SQL Server](https://blogs.msdn.com/b/psssql/)  
  
-   **Video**  
  
     [Pagina relativa alla prima parte riguardante l'introduzione della soluzione a disponibilità elevata di prossima generazione della serie AlwaysOn di Microsoft SQL Server nome in codice "Denali"](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server nome in codice "Denali" Always On Series, parte 2: compilazione di una soluzione mission-critical a disponibilità elevata con AlwaysOn](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **White paper:**  
  
     [Microsoft SQL Server Always On Solutions Guide for High Availability and Disaster Recovery (Guida alle soluzioni AlwaysOn di Microsoft SQL Server per la disponibilità elevata e il ripristino di emergenza)](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica dei gruppi di disponibilità Always On; SQL Server;](overview-of-always-on-availability-groups-sql-server.md)   
 [Prerequisiti, restrizioni e consigli per Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [Configurazione di un'istanza del server per i gruppi di disponibilità Always On; SQL Server;](always-on-availability-groups-sql-server.md)   
 [Creazione e configurazione dei gruppi di disponibilità; SQL Server;](creation-and-configuration-of-availability-groups-sql-server.md)   
 [Amministrazione di un gruppo di disponibilità; SQL Server;](administration-of-an-availability-group-sql-server.md)   
 [Monitoraggio di Gruppi di disponibilità &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)   
 [Panoramica delle istruzioni Transact-SQL per i gruppi di disponibilità Always On; SQL Server;](transact-sql-statements-for-always-on-availability-groups.md)   
 [Panoramica dei cmdlet di PowerShell per Gruppi di disponibilità AlwaysOn; SQL Server;](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)  
  
