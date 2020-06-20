---
title: Applicazioni livello dati | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- designing DACs
- How to [DAC]
- data-tier application [SQL Server], designing
- wizard [DAC]
ms.assetid: a04a2aba-d07a-4423-ab8a-0a31658f6317
author: stevestein
ms.author: sstein
ms.openlocfilehash: f611367f0b078fb02977c27ee1d61d648de87869
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84970301"
---
# <a name="data-tier-applications"></a>Applicazioni livello dati
  Un'applicazione livello dati è un'entità logica di gestione dei database che definisce tutti gli oggetti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad esempio le tabelle, le viste e gli oggetti istanza, inclusi gli account di accesso, associati a un database dell'utente. Un'applicazione livello dati è un'unità indipendente della distribuzione di database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che consente a sviluppatori di livello dati e ad amministratori di database di comprimere gli oggetti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un elemento portabile chiamato pacchetto di applicazione livello dati, noto anche come DACPAC.  
  
 Un BACPAC è un elemento correlato che incapsula lo schema del database e i dati archiviati nel database.  
  
## <a name="benefits-of-data-tier-applications"></a>Vantaggi delle applicazioni livello dati  
 Il ciclo di vita della maggior parte delle applicazioni di database prevede che gli sviluppatori e gli amministratori di database condividano e scambino script e note di integrazione ad hoc per le attività di aggiornamento e manutenzione dell'applicazione. Mentre questo concetto è accettabile per un numero contenuto di database, diventa rapidamente non impiegabile se i database crescono in termini di numero, dimensione e complessità.  
  
 Un'applicazione livello dati è uno strumento di produttività e gestione del ciclo di vita del database che offre allo sviluppo dichiarativo del database una distribuzione e una gestione semplificata. Uno sviluppatore può creare un database in un progetto di database di SQL Server Data Tools, quindi compilare il database in un pacchetto di applicazione livello dati per passarlo a un amministratore di database. Con DBA è possibile distribuire l'applicazione livello dati tramite SQL Server Management Studio in un'istanza di test o di produzione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. In alternativa, l'amministratore di database può utilizzare il pacchetto di applicazione livello dati per aggiornare un database precedentemente distribuito tramite SQL Server Management Studio. Per completare il ciclo di vita, l'amministratore di database può estrarre il database in un pacchetto di applicazione livello dati e può passarlo a uno sviluppatore per riflettere rettifiche di test o produzione oppure per abilitare ulteriori modifiche di progettazione del database in risposta alle modifiche dell'applicazione.  
  
 Il vantaggio di una distribuzione guidata dall'applicazione livello dati rispetto a un esercizio controllato da script consiste nel fatto che lo strumento consente all'amministratore di database di identificare e convalidare i comportamenti da database di origine e destinazione diversi. Durante gli aggiornamenti, lo strumento avverte l'amministratore di database nel caso in cui è possibile che si verifichi la perdita di dati e fornisce anche un piano di aggiornamento. L'amministratore di database può valutare il piano, quindi utilizzare lo strumento per procedere con l'aggiornamento.  
  
 Le applicazioni livello dati inoltre supportano il controllo delle versioni per consentire allo sviluppatore e all'amministratore di database di mantenere e gestire la derivazione del database tramite il ciclo di vita.  
  
## <a name="dac-concepts"></a>Concetti di applicazione livello dati  
 Un'applicazione livello dati semplifica lo sviluppo, la distribuzione e la gestione degli elementi livello dati che supportano un'applicazione:  
  
-   Un'applicazione livello dati è un'entità logica di gestione dei database che definisce tutti gli oggetti di SQL Server, ad esempio le tabelle, le viste e gli oggetti istanza, associati a un database dell'utente. È un'unità indipendente della distribuzione di database SQL Server che consente a sviluppatori di livello dati e ad amministratori di database di comprimere gli oggetti di SQL Server in un elemento portabile chiamato pacchetto di applicazione livello dati o file .dacpac.  
  
-   Affinché venga trattato come un'applicazione livello dati, è necessario che un database SQL Server venga registrato in modo esplicito da un'operazione dell'utente o in modo implicito da una delle operazioni dell'applicazione livello dati. Quando un database viene registrato, la versione dell'applicazione livello dati e le altre proprietà vengono registrate nei metadati del database. Viceversa, è possibile annullare la registrazione di un database e rimuovere le proprietà dell'applicazione livello dati.  
  
-   In generale, gli strumenti di applicazione livello dati sono in grado di leggere i file con estensione DACPAC generati dagli strumenti di applicazione livello dati delle versioni precedenti di SQL Server e di distribuire file DACPAC alle versioni precedenti di SQL Server. Tuttavia, gli strumenti di applicazione livello dati delle versioni precedenti non sono in grado di leggere i file con estensione DACPAC generati dagli strumenti di applicazioni livello dati delle versioni successive. In particolare:  
  
    -   Le operazioni dell'applicazione livello dati sono state introdotte con SQL Server 2008 R2. Oltre ai database SQL Server 2008 R2, gli strumenti supportano la generazione di file con estensione DACPAC da database SQL Server 2008, SQL Server 2005 e SQL Server 2000.  
  
    -   Oltre ai database [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], gli strumenti forniti con [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] sono in grado di leggere i file con estensione DACPAC generati dagli strumenti di applicazione livello dati forniti con SQL Server 2008 R2 o SQL Server 2012. Sono inclusi i database di SQL Server 2012, SQL Server 2008 R2, SQL Server 2008 e SQL Server 2005, ma non SQL Server 2000.  
  
    -   Gli strumenti di applicazione livello dati di SQL Server 2008 R2 non sono in grado di leggere i file con estensione DACPAC generati dagli strumenti di [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] o [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
-   Un pacchetto di applicazione livello dati è un file di Windows con l'estensione .dacpac. Il file supporta un formato aperto composto da più sezioni XML che rappresentano i dettagli dell'origine del pacchetto di livello dati, gli oggetti nel database e altre funzionalità. Il file può essere decompresso da un utente avanzato tramite l'utilità DacUnpack.exe che viene fornita con il prodotto per controllare più da vicino ogni sezione.  
  
-   L'utente deve essere membro del ruolo dbmanager o disporre delle autorizzazioni CREATE DATABASE per creare un database, compresa la creazione di un database tramite la distribuzione di un pacchetto di applicazione livello dati. L'utente deve essere membro del ruolo dbmanager o disporre delle autorizzazioni DROP DATABASE per eliminare un database.  
  
## <a name="dac-tools"></a>Strumenti di applicazione livello dati  
 Un pacchetto di applicazione livello dati può essere perfettamente utilizzato in più strumenti forniti con [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Questi strumenti indirizzano i requisiti dei diversi tipi di utente utilizzando un pacchetto di applicazione livello dati come unità di interoperabilità.  
  
-   Sviluppatore di applicazioni  
  
    -   Uno sviluppatore di database può utilizzare un progetto di database SQL Server Data Tools per progettare un database. Una corretta compilazione di questo progetto comporta la generazione di un pacchetto di applicazione livello dati contenuta in un file con estensione .dacpac.  
  
    -   Inoltre, lo sviluppatore può importare un pacchetto di applicazione livello dati in un progetto di database e continuare a progettare il database.  
  
    -   SQL Server Data Tools supporta anche un Local DB per lo sviluppo di applicazioni di database client non connessi. Lo sviluppatore può creare uno snapshot del database locale per creare pacchetto di applicazione livello dati contenuto in un file con estensione .dacpac.  
  
    -   Lo sviluppatore può pubblicare autonomamente un progetto di database direttamente in un database, senza generare un pacchetto di applicazione livello dati. L'operazione di pubblicazione segue un comportamento simile all'operazione di distribuzione di altri strumenti.  
  
-   Amministratore del database  
  
    -   Un amministratore di database può utilizzare SQL Server Management Studio per estrarre un pacchetto di applicazione livello dati da un database esistente ed eseguire altre operazioni dell'applicazione livello dati.  
  
    -   Inoltre, l'amministratore di un database per [!INCLUDE[ssSDS](../../includes/sssds-md.md)] può utilizzare il Portale di gestione per SQL Azure per le operazioni dell'applicazione livello dati.  
  
-   Fornitore di software indipendenti  
  
    -   I servizi di hosting e altri prodotti di gestione di dati per SQL Server sono in grado di utilizzare l'API DACFx per le operazioni dell'applicazione livello dati.  
  
-   Amministratore IT  
  
    -   Gli integratori di sistemi IT e gli amministratori IT possono utilizzare lo strumento riga di comando SqlPackage.exe per le operazioni dell'applicazione livello dati.  
  
## <a name="dac-operations"></a>Operazioni dell'applicazione livello dati  
 Un'applicazione livello dati supporta le seguenti operazioni:  
  
-   **EXTRACT**: l'utente può estrarre un database in un pacchetto di applicazione livello dati.  
  
-   **DEPLOY**: l'utente può distribuire un pacchetto di applicazione livello dati in un server host. Quando la distribuzione viene eseguita tramite uno strumento di gestione come SQL Server Management Studio o il Portale di gestione per SQL Azure, il database risultante nel server host viene registrato in modo implicito come applicazione livello dati.  
  
-   **REGISTER**: l'utente può registrare un database come applicazione livello dati.  
  
-   **UNREGISTER**: è possibile annullare la registrazione di un database registrato in precedenza come applicazione livello dati.  
  
-   **UPGRADE**: è possibile aggiornare un database usando un pacchetto di applicazione livello dati. L'aggiornamento è supportato anche su database non registrati in precedenza come applicazioni livello dati, ma come conseguenza dell'aggiornamento, il database verrà registrato in modo implicito.  
  
## <a name="backup-package-bacpac"></a>Pacchetto di backup (estensione .bacpac)  
 Un BACPAC è un elemento che incapsula lo schema del database e i dati archiviati nel database. Un BACPAC è un file di Windows con l'estensione .bacpac. Analogamente a DACPAC, BACPAC è un formato di file aperto. Il contenuto dello schema del BACPAC è identico a quello del pacchetto di applicazione livello dati. I dati sono archiviati nel formato JSON.  
  
 I pacchetti DACPAC e BACPAC sono simili, ma destinati a scenari diversi. Un pacchetto di applicazione livello dati esegue l'acquisizione e la distribuzione dello schema, compreso l'aggiornamento del database esistente. Il caso d'uso principale di un DACPAC consiste nel distribuire uno schema strettamente definito per gli ambienti di sviluppo, test e produzione e il contrario: l'acquisizione dello schema di produzione e la relativa applicazione a ambienti di test e sviluppo.  
  
 Un BACPAC invece esegue l'acquisizione dello schema e dei dati. Un BACPAC è l'equivalente logico di un backup di database e non può essere utilizzato per aggiornare i database esistenti. L'utilizzo primario di un BACPAC consiste nello spostamento di un database da un server a un altro, o da un server locale al cloud, e l'archiviazione di un database esistente in un formato aperto.  
  
 Un BACPAC supporta due operazioni principali:  
  
-   **EXPORT**: l'utente può esportare lo schema e i dati di un database in un file BACPAC.  
  
-   **IMPORT**: l'utente può importare lo schema e i dati in un nuovo database nel server host.  
  
 Entrambe queste funzionalità sono supportate dagli strumenti di gestione di database Server Management Studio, il Portale di gestione per SQL Azure e l'API DACFx.  
  
## <a name="permissions"></a>Autorizzazioni  
 L'utente deve essere membro del ruolo `dbmanager` o disporre delle autorizzazioni `CREATE DATABASE` per creare un database, compresa la creazione di un database tramite la distribuzione di un pacchetto di applicazione livello dati. L'utente deve essere membro del ruolo `dbmanager` o disporre delle autorizzazioni `DROP DATABASE` per eliminare un database.  
  
## <a name="data-tier-application-tasks"></a>Attività dell'applicazione livello dati  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Viene descritto come utilizzare un file del pacchetto di applicazione livello dati per creare una nuova istanza di applicazione livello dati.|[Distribuire un'applicazione livello dati](deploy-a-data-tier-application.md)|  
|Viene descritto come utilizzare un nuovo file del pacchetto di applicazione livello dati per aggiornare un'istanza alla nuova versione dell'applicazione livello dati.|[Aggiornare un'applicazione livello dati](upgrade-a-data-tier-application.md)|  
|Viene descritto come eliminare un'istanza di applicazione livello dati. È inoltre possibile scollegare o eliminare il database associato o lasciarlo intatto.|[Eliminazione di un'applicazione livello dati](delete-a-data-tier-application.md)|  
|Viene descritto come visualizzare l'integrità dell'applicazione livello dati correntemente distribuita tramite Utilità SQL Server.|[Monitoraggio delle applicazioni livello dati](data-tier-applications.md)|  
|Viene descritto come creare un file .bacpac che contiene un archivio dei dati e dei metadati in un'applicazione livello dati.|[Esportazione di un'applicazione livello dati](export-a-data-tier-application.md)|  
|Viene descritto come utilizzare un file di archivio dell'applicazione livello dati (estensione .bacpac) per eseguire un ripristino logico di un'applicazione livello dati o la migrazione dell'applicazione livello dati a un'altra istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] o [!INCLUDE[ssSDS](../../includes/sssds-md.md)].|[Importare un file BACPAC per creare un nuovo database utente](import-a-bacpac-file-to-create-a-new-user-database.md)|  
|Viene descritto come importare un file BACPAC per creare un nuovo database utente all'interno di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|[Estrarre un'applicazione livello dati da un database](extract-a-dac-from-a-database.md)|  
|Viene descritto come promuovere un database esistente trasformandolo in un'istanza di applicazione livello dati. Una definizione dell'applicazione livello dati viene compilata e archiviata nei database di sistema.|[Registrare un database come applicazione livello dati](register-a-database-as-a-dac.md)|  
|Viene descritto come rivedere il contenuto di un pacchetto di applicazione livello dati e le azioni che un aggiornamento dell'applicazione livello dati eseguirà prima di utilizzare il pacchetto in un sistema di produzione.|[Convalida di un pacchetto di applicazione livello dati](validate-a-dac-package.md)|  
|Viene descritto come posizionare il contenuto di un pacchetto di applicazione livello dati in una cartella dove un amministratore di database può rivedere quello che l'applicazione livello dati fa prima di distribuirlo a un server di produzione.|[Decompressione di un pacchetto di applicazione livello dati](unpack-a-dac-package.md)|  
|Viene descritto come utilizzare una procedura guidata per distribuire un database esistente. Nella procedura guidata vengono utilizzate applicazioni livello dati per effettuare la distribuzione.|[Distribuire un database tramite un'applicazione livello dati](deploy-a-database-by-using-a-dac.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto dell'applicazione livello dati per oggetti e versioni di SQL Server](dac-support-for-sql-server-objects-and-versions.md)  
  
  
