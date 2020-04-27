---
title: FileTable (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 07/06/2016
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], overview
- FileTables [SQL Server]
- FileTable [SQL Server], see FileTables [SQL Server]
- FileTable [SQL Server]
ms.assetid: a57b629c-e9ed-48fd-9a48-ed3787d80c8f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e2eec829c3c8909bd318a86ecf35eedb9ac0f222
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66010085"
---
# <a name="filetables-sql-server"></a>FileTable (SQL Server)
  La funzionalità FileTable fornisce supporto per lo spazio dei nomi dei file di Windows e la compatibilità con le applicazioni di Windows ai dati dei file archiviati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. FileTable consente l'integrazione dei componenti di archiviazione e gestione dei dati da parte di un'applicazione e fornisce servizi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] integrati, incluse la ricerca full-text e la ricerca semantica, su dati e metadati non strutturati.  
  
 In altre parole, è possibile archiviare file e documenti in speciali tabelle denominate FileTable in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ma accedere a tali file e documenti da applicazioni di Windows come se questi fossero archiviati nel file system, senza apportare alcuna modifica alle applicazioni del client.  
  
 La caratteristica FileTable si basa sulla tecnologia FILESTREAM di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Per altre informazioni su FILESTREAM, vedere [FILESTREAM &#40;SQL Server&#41;](filestream-sql-server.md).  
  
##  <a name="benefits-of-the-filetable-feature"></a><a name="Goals"></a> Vantaggi della caratteristica FileTable  
 Tra gli obiettivi della caratteristica FileTable sono inclusi i seguenti:  
  
-   Compatibilità con le API Windows per dati dei file archiviati all'interno di un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . La compatibilità con le API Windows include gli elementi seguenti:  
  
    -   Accesso tramite flusso non transazionale e aggiornamenti sul posto ai dati FILESTREAM.  
  
    -   Spazio dei nomi gerarchico di directory e file.  
  
    -   Archiviazione di attributi dei file, quali data di creazione e data di modifica.  
  
    -   Supporto per API di gestione di file e directory di Windows.  
  
-   Compatibilità con altre caratteristiche di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , inclusi strumenti di gestione, servizi e funzionalità di query relazionali su dati FILESTREAM e attributi di file.  
  
 Le tabelle FileTable eliminano pertanto un ostacolo significativo all'utilizzo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per l'archiviazione e la gestione di dati non strutturati che si trovano attualmente come file in file server. Le organizzazioni possono spostare tali dati da file server a tabelle FileTable per sfruttare l'amministrazione integrata e altri servizi forniti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Contemporaneamente, le organizzazioni possono gestire la compatibilità delle applicazioni di Windows che riconoscono tali dati come file nel file system.  
    
##  <a name="what-is-a-filetable"></a><a name="Description"></a> Definizione di tabella FileTable  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornisce una speciale **tabella di file**, denominata anche **FileTable**, per applicazioni che richiedono archiviazione di file e directory nel database, con compatibilità con le API Windows e accesso non transazionale. Il termine FileTable indica una tabella utente specifica con uno schema predefinito per l'archiviazione di dati FILESTREAM, nonché informazioni sulla gerarchia di file e directory e attributi di file.  
  
 Una tabella FileTable offre le funzionalità seguenti:  
  
-   Una tabella FileTable rappresenta una gerarchia di directory e file. In tale tabella sono archiviati i dati correlati a tutti i nodi nella gerarchia, sia per le directory sia per i file inclusi in tali nodi. Questa gerarchia inizia da una directory radice specificata durante la creazione della tabella FileTable.  
  
-   Ogni riga in una tabella FileTable rappresenta un file o una directory.  
  
-   Ogni riga contiene i seguenti elementi. Per altre informazioni sullo schema di una tabella FileTable, vedere [Schema delle tabelle FileTable](filetable-schema.md).  
  
    -   Una colonna**file_stream** per dati del flusso e un identificatore **stream_id** (GUID). La colonna **file_stream** è NULL per una directory.  
  
    -   Entrambe le colonne **path_locator** e **parent_path_locator** per la rappresentazione e la gestione della gerarchia di file e directory.  
  
    -   10 attributi di file, quali data di creazione e data di modifica, utili con le API di I/O dei file.  
  
    -   Una colonna Type che supporta la ricerca full-text e la ricerca semantica su file e documenti.  
  
-   Una tabella FileTable applica determinati vincoli e trigger definiti dal sistema per gestire la semantica degli spazi dei nomi dei file.  
  
-   Quando il database è configurato per l'accesso non transazionale, la gerarchia di file e directory rappresentata nella tabella FileTable viene esposta sotto la condivisione di FILESTREAM configurata per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . In questo modo, viene fornito l'accesso al file system per applicazioni Windows.  
  
 Tra le caratteristiche aggiuntive delle tabelle FileTable sono incluse le seguenti:  
  
-   I dati di file e directory archiviati in una tabella FileTable vengono esposti tramite una condivisione di Windows per l'accesso non transazionale ai file per applicazioni basate su API Windows. Per un'applicazione Windows, questa è simile a una condivisione normale con i file e le directory. Le applicazioni possono utilizzare un vasta gamma di API Windows per gestire i file e le directory inclusi in questa condivisione.  
  
-   La gerarchia di directory rappresentata tramite la condivisione è una struttura di directory puramente logica gestita all'interno della tabella FileTable.  
  
-   Le chiamate per creare o modificare un file o una directory tramite la condivisione di Windows vengono intercettate da un componente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e applicate ai dati relazionali corrispondenti nella tabella FileTable.  
  
-   Le operazioni delle API Windows sono di natura non transazionale e non sono associate alle transazioni utente. L'accesso transazionale ai dati FILESTREAM archiviati in una tabella FileTable, tuttavia, è completamente supportato, come nel caso di qualsiasi colonna FILESTREAM in una normale tabella.  
  
-   È inoltre possibile eseguire query su tabelle FileTable e aggiornarle tramite normale accesso [!INCLUDE[tsql](../../includes/tsql-md.md)] . Le tabelle FileTable sono inoltre integrate con gli strumenti di gestione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e con caratteristiche quali il backup.  
  
  
##  <a name="additional-considerations-for-using-filetables"></a><a name="additional"></a>Ulteriori considerazioni sull'utilizzo di tabelle FileTable  
  
###  <a name="administrative-considerations"></a><a name="DBA"></a>Considerazioni amministrative  
 **Informazioni su FILESTREAM e tabelle FileTable**  
  
-   È necessario configurare tabelle FileTable separatamente da FILESTREAM. È pertanto possibile continuare a utilizzare la caratteristica FILESTREAM senza abilitare l'accesso non transazionale o creare tabelle FileTable.  
  
-   Non è disponibile alcun accesso non transazionale a dati FILESTREAM se non tramite tabelle FileTable. Quando si abilita l'accesso non transazionale, pertanto, il comportamento delle applicazioni e delle colonne FILESTREAM esistenti non subisce modifiche.  
  
 **Informazioni sulle tabelle FileTable e l'accesso non transazionale**  
  
-   È possibile abilitare o disabilitare l'accesso non transazionale a livello di database.  
  
-   È possibile configurare o ottimizzare l'accesso non transazionale a livello di database disabilitando o abilitando l'accesso in sola lettura o in lettura/scrittura.  
  
  
###  <a name="filetables-do-not-support-memory-mapped-files"></a><a name="memory"></a>Le tabelle FileTable non supportano i file mappati alla memoria  
 Le tabelle FileTable non supportano file con mapping in memoria. Blocco note e Paint sono due esempi comuni di applicazioni in cui vengono utilizzati file con mapping in memoria. Non è possibile utilizzare queste applicazioni nello stesso computer di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per aprire file archiviati in una tabella FileTable. Tuttavia è possibile utilizzare queste applicazioni da un computer remoto per aprire file archiviati in una tabella FileTable, perché in queste circostanze la caratteristica con mapping in memoria non viene utilizzata.  
  
  
##  <a name="related-tasks"></a><a name="reltasks"></a> Attività correlate  
 [Abilitazione dei prerequisiti per la tabella FileTable](enable-the-prerequisites-for-filetable.md)  
 Viene descritto come abilitare i prerequisiti per la creazione e l'utilizzo di tabelle FileTable.  
  
 [Creare, modificare e rilasciare FileTables](create-alter-and-drop-filetables.md)  
 Viene descritto come creare una nuova tabella FileTable o modificarne o eliminarne una esistente.  
  
 [Caricamento di file in FileTable](load-files-into-filetables.md)  
 Viene descritto come caricare o eseguire la migrazione dei file in tabelle FileTable.  
  
 [Utilizzare directory e percorsi in FileTable](work-with-directories-and-paths-in-filetables.md)  
 Descrive la struttura di directory nella quale vengono archiviati i file in FileTable.  
  
 [Accesso a tabelle FileTable tramite Transact-SQL](access-filetables-with-transact-sql.md)  
 Viene descritto il funzionamento dei comandi Transact-SQL DML (Data Manipulation Language) con una tabella FileTable.  
  
 [Accedere alle tabelle FileTable con API di Input-Output dei file](access-filetables-with-file-input-output-apis.md)  
 Viene descritto il funzionamento dell'I/O del file system in una tabella FileTable.  
  
 [Gestione di tabelle FileTable](manage-filetables.md)  
 Vengono descritte attività amministrative comuni per la gestione di tabelle FileTable.  
  
  
##  <a name="related-content"></a><a name="relcontent"></a> Contenuto correlato  
 [Schema delle tabelle FileTable](filetable-schema.md)  
 Viene descritto lo schema predefinito e fisso di una tabella FileTable.  
  
 [Compatibilità di FileTable con altre funzionalità di SQL Server](filetable-compatibility-with-other-sql-server-features.md)  
 Viene descritto il funzionamento delle tabelle FileTable con altre caratteristiche di SQL Server.  
  
 [DDL FileTable, funzioni, stored Procedure e viste](../views/views.md)  
 Vengono elencate le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] e gli oggetti di database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aggiunti o modificati per supportare la funzione FileTable.  
  
 
  
