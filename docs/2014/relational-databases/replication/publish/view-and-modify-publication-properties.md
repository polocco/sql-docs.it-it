---
title: Visualizzare e modificare le proprietà della pubblicazione | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- viewing replication properties
- modifying replication properties, articles
- articles [SQL Server replication], modifying
- publications [SQL Server replication], properties
- articles [SQL Server replication], properties
- modifying replication properties, publications
- publications [SQL Server replication], modifying
ms.assetid: 27d72ea4-bcb6-48f2-b4aa-eb1410da7efc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5053cc16734cc18c75e163fec4c06b1768e590cc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "68941060"
---
# <a name="view-and-modify-publication-properties"></a>Visualizzazione e modifica delle proprietà della pubblicazione
  In questo argomento viene descritto come modificare le proprietà delle pubblicazioni in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]o RMO (Replication Management Objects).  
  
 **Contenuto dell'articolo**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Indicazioni](#Recommendations)  
  
-   **Per visualizzare e modificare le proprietà delle pubblicazioni tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Oggetti RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Alcune proprietà non possono essere modificate dopo la creazione di una pubblicazione, mentre altre proprietà non possono essere modificate se sono presenti sottoscrizioni alla pubblicazione. Le proprietà che non possono essere modificate vengono visualizzate come di sola lettura.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Raccomandazioni  
  
-   Dopo la creazione di una pubblicazione, per alcune modifiche delle proprietà è necessario un nuovo snapshot. Se la pubblicazione dispone di sottoscrizioni, per alcune modifiche è inoltre necessario reinizializzare tutte le sottoscrizioni. Per altre informazioni, vedere [Modificare le proprietà di pubblicazioni e articoli](change-publication-and-article-properties.md) e [Aggiungere ed eliminare articoli in pubblicazioni esistenti](add-articles-to-and-drop-articles-from-existing-publications.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Con SQL Server Management Studio  
 Le proprietà delle pubblicazioni possono essere visualizzate e modificate nella finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>** disponibile in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] e Monitoraggio replica. Per informazioni sull'avvio di Monitoraggio replica, vedere [Avviare Monitoraggio replica](../monitor/start-the-replication-monitor.md).  
  
 La finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>** include le pagine seguenti:  
  
-   Nella pagina **Generale** sono presenti il nome e la descrizione della pubblicazione, il nome del database, il tipo di pubblicazione e le impostazioni di scadenza della sottoscrizione.  
  
-   La pagina **Articoli** corrisponde alla pagina **Articoli** presente nella Creazione guidata nuova pubblicazione. Utilizzare questa pagina per aggiungere ed eliminare articoli e per modificare le proprietà e l'applicazione di filtri a colonne per gli articoli.  
  
-   La pagina **Filtra righe** corrisponde alla pagina **Filtro righe tabella** presente nella Creazione guidata nuova pubblicazione. Utilizzare questa pagina per aggiungere, modificare ed eliminare filtri di righe statici per tutti i tipi di pubblicazioni e aggiungere, modificare ed eliminare filtri di righe con parametri e filtri join per le pubblicazioni di tipo merge.  
  
-   La pagina **Snapshot** consente di specificare il formato e la posizione dello snapshot, se comprimere lo snapshot e gli script da eseguire prima e dopo l'applicazione dello snapshot.  
  
-   La pagina **Snapshot FTP** , per le pubblicazioni snapshot e transazionali e per le pubblicazioni di tipo merge nei server di pubblicazione che eseguono versioni precedenti a SQL Server 2005, consente di specificare se i Sottoscrittori possono scaricare file di snapshot tramite FTP (File Transfer Protocol).  
  
-   La pagina **Snapshot FTP e Internet** , per le pubblicazioni di tipo merge da server di pubblicazione che eseguono SQL Server 2005 o versione successiva, consente di specificare se i Sottoscrittori possono scaricare file di snapshot tramite FTP e sincronizzare le sottoscrizioni tramite HTTPS.  
  
-   Nella pagina **Opzioni della sottoscrizione** è possibile impostare alcune opzioni che si applicano a tutte le sottoscrizioni. Le opzioni variano in relazione al tipo di pubblicazione.  
  
-   La pagina **Elenco accesso pubblicazione** consente di specificare quali account di accesso e gruppi possono accedere a una pubblicazione.  
  
-   La pagina **Sicurezza agente** consente di accedere alle impostazioni degli account utilizzati per l'esecuzione degli agenti seguenti e per la creazione di connessioni ai computer in una topologia di replica: l'agente snapshot per tutte le pubblicazioni, l'agente di lettura log per tutte le pubblicazioni transazionali e l'agente di lettura coda per le pubblicazioni transazionali che consentono sottoscrizioni ad aggiornamento in coda.  
  
-   La pagina **Partizioni dati** , per le pubblicazioni di tipo merge da server di pubblicazione che eseguono SQL Server 2005 o versione successiva, consente di specificare se i Sottoscrittori delle pubblicazioni con filtri con parametri possono richiedere uno snapshot qualora non ne fosse disponibile uno. In questa pagina è inoltre possibile generare snapshot per una o più partizioni, una sola volta o in base a una pianificazione periodica.  
  
#### <a name="to-view-and-modify-publication-properties-in-management-studio"></a>Per visualizzare e modificare le proprietà delle pubblicazioni in Management Studio  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
3.  Fare clic con il pulsante destro del mouse su una pubblicazione e quindi scegliere **Proprietà**.  
  
4.  Se necessario, modificare le proprietà e quindi fare clic su **OK**.  
  
#### <a name="to-view-and-modify-publication-properties-in-replication-monitor"></a>Per visualizzare e modificare le proprietà delle pubblicazioni in Monitoraggio replica  
  
1.  Espandere un gruppo di server di pubblicazione nel riquadro sinistro di Monitoraggio replica e quindi espandere un server di pubblicazione.  
  
2.  Fare clic con il pulsante destro del mouse su una pubblicazione e quindi scegliere **Proprietà**.  
  
3.  Se necessario, modificare le proprietà e quindi fare clic su **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Con Transact-SQL  
 È possibile modificare le pubblicazioni e restituire a livello di programmazione le relative proprietà tramite le stored procedure di replica. Le stored procedure utilizzate dipenderanno dal tipo di pubblicazione.  
  
#### <a name="to-view-the-properties-of-a-snapshot-or-transactional-publication"></a>Per visualizzare le proprietà di una pubblicazione snapshot o transazionale  
  
1.  Eseguire [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql), specificando il nome della pubblicazione per il parametro **\@publication**. Se questo parametro viene omesso, verranno restituite le informazioni su tutte le pubblicazioni disponibili nel server di pubblicazione.  
  
#### <a name="to-change-the-properties-of-a-snapshot-or-transactional-publication"></a>Per modificare le proprietà di una pubblicazione snapshot o transazionale  
  
1.  Eseguire [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), specificando la proprietà della pubblicazione da modificare nel parametro **\@property** e il nuovo valore di questa proprietà nel parametro **\@value**.  
  
    > [!NOTE]  
    >  Se la modifica richiederà la generazione di un nuovo snapshot, è necessario specificare anche il valore **1** per **\@force_invalidate_snapshot** e se richiederà la reinizializzazione dei Sottoscrittori, è necessario specificare il valore **1** per **\@force_reinit_subscription**. Per altre informazioni sulle proprietà che, in caso di modifica, richiedono un nuovo snapshot o una reinizializzazione, vedere [Modificare le proprietà di pubblicazioni e articoli](change-publication-and-article-properties.md).  
  
#### <a name="to-view-the-properties-of-a-merge-publication"></a>Per visualizzare le proprietà di una pubblicazione di tipo merge  
  
1.  Eseguire [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), specificando il nome della pubblicazione per il parametro **\@publication**. Se questo parametro viene omesso, verranno restituite le informazioni su tutte le pubblicazioni disponibili nel server di pubblicazione.  
  
#### <a name="to-change-the-properties-of-a-merge-publication"></a>Per modificare le proprietà di una pubblicazione di tipo merge  
  
1.  Eseguire [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql), specificando la proprietà della pubblicazione da modificare nel parametro **\@property** e il nuovo valore di questa proprietà nel parametro **\@value**.  
  
    > [!NOTE]  
    >  Se la modifica richiederà la generazione di un nuovo snapshot, è necessario specificare anche il valore **1** per **\@force_invalidate_snapshot** e se richiederà la reinizializzazione dei Sottoscrittori, è necessario specificare il valore **1** per **\@force_reinit_subscription**. Per altre informazioni sulle proprietà che, in caso di modifica, richiedono un nuovo snapshot o una reinizializzazione, vedere [Modificare le proprietà di pubblicazioni e articoli](change-publication-and-article-properties.md).  
  
#### <a name="to-view-the-properties-of-a-snapshot"></a>Per visualizzare le proprietà di uno snapshot  
  
1.  Eseguire [sp_helppublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql), specificando il nome della pubblicazione per il parametro **\@publication**.  
  
#### <a name="to-change-the-properties-of-a-snapshot"></a>Per modificare le proprietà di uno snapshot  
  
1.  Eseguire [sp_changepublication_snapshot](/sql/relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql), specificando una o più delle nuove proprietà dello snapshot per i parametri appropriati dello snapshot.  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> Esempi (Transact-SQL)  
 In questo esempio di replica transazionale vengono restituite le proprietà della pubblicazione.  
  
 [!code-sql[HowTo#sp_helppublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changetranpub.sql#sp_helppublication)]  
  
 In questo esempio di replica transazionale viene disabilitata la replica dello schema per la pubblicazione.  
  
 [!code-sql[HowTo#sp_changepublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changetranpub.sql#sp_changepublication)]  
  
 In questo esempio di replica di tipo merge vengono restituite le proprietà della pubblicazione.  
  
 [!code-sql[HowTo#sp_helpmergepublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changemergepub.sql#sp_helpmergepublication)]  
  
 In questo esempio di replica di tipo merge viene disabilitata la replica dello schema per la pubblicazione.  
  
 [!code-sql[HowTo#sp_changemergepublication](../../../snippets/tsql/SQL15/replication/howto/tsql/changemergepub.sql#sp_changemergepublication)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
 È possibile modificare le pubblicazioni e accedere alle relative proprietà a livello di programmazione utilizzando oggetti RMO (Replication Management Objects). Le classi RMO utilizzate per visualizzare o modificare le proprietà della pubblicazione dipendono dal tipo di pubblicazione.  
  
#### <a name="to-view-or-modify-properties-of-a-snapshot-or-transactional-publication"></a>Per visualizzare o modificare le proprietà di una pubblicazione snapshot o transazionale  
  
1.  Creare una connessione al server di pubblicazione tramite la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Creare un'istanza della classe <xref:Microsoft.SqlServer.Replication.TransPublication> , impostare le proprietà <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> e <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> per la pubblicazione, quindi impostare la proprietà <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> sulla connessione creata al passaggio 1.  
  
3.  Chiamare il metodo <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> per recuperare le proprietà dell'oggetto. Se questo metodo restituisce `false`, le proprietà della pubblicazione sono state definite in modo non corretto nel passaggio 2 oppure la pubblicazione non esiste.  
  
4.  (Facoltativo) Per modificare le proprietà, specificare un nuovo valore per una o più proprietà che è possibile impostare. Utilizzare l'operatore AND logico (`&` in Microsoft Visual C# e `And` in Microsoft Visual Basic) per determinare se per la proprietà <xref:Microsoft.SqlServer.Replication.PublicationAttributes> è impostato un valore <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> specificato. Utilizzare l'operatore logico OR inclusivo (`|` in Visual C# e `Or` in Visual Basic) e l'operatore logico OR esclusivo (`^` in Visual C# e `Xor` in Visual Basic) per modificare i valori di <xref:Microsoft.SqlServer.Replication.PublicationAttributes> per la proprietà <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A>.  
  
5.  (Facoltativo) Se si specifica un valore `true` per <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, chiamare il metodo <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> per eseguire il commit delle modifiche nel server. Se si specifica un valore `false` per <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (impostazione predefinita), le modifiche vengono inviate immediatamente al server.  
  
#### <a name="to-view-or-modify-properties-of-a-merge-publication"></a>Per visualizzare o modificare le proprietà di una pubblicazione di tipo merge  
  
1.  Creare una connessione al server di pubblicazione tramite la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Creare un'istanza della classe <xref:Microsoft.SqlServer.Replication.MergePublication> , impostare le proprietà <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> e <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> per la pubblicazione, quindi impostare la proprietà <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> sulla connessione creata al passaggio 1.  
  
3.  Chiamare il metodo <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> per recuperare le proprietà dell'oggetto. Se questo metodo restituisce `false`, le proprietà della pubblicazione sono state definite in modo non corretto nel passaggio 2 oppure la pubblicazione non esiste.  
  
4.  (Facoltativo) Per modificare le proprietà, specificare un nuovo valore per una o più proprietà che è possibile impostare. Utilizzare l'operatore AND logico (`&` in Visual C# e `And` in Visual Basic) per determinare se per la proprietà <xref:Microsoft.SqlServer.Replication.PublicationAttributes> è impostato un valore <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> specificato. Utilizzare l'operatore logico OR inclusivo (`|` in Visual C# e `Or` in Visual Basic) e l'operatore logico OR esclusivo (`^` in Visual C# e `Xor` in Visual Basic) per modificare i valori di <xref:Microsoft.SqlServer.Replication.PublicationAttributes> per la proprietà <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A>.  
  
5.  (Facoltativo) Se si specifica un valore `true` per <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, chiamare il metodo <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> per eseguire il commit delle modifiche nel server. Se si specifica un valore `false` per <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (impostazione predefinita), le modifiche vengono inviate immediatamente al server.  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> Esempi (RMO)  
 In questo esempio vengono impostati gli attributi di pubblicazione per una pubblicazione transazionale. Le modifiche vengono memorizzate nella cache finché non vengono inviate al server in modo esplicito.  
  
 [!code-csharp[HowTo#rmo_ChangeTranPub_cached](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changetranpub_cached)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeTranPub_cached](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changetranpub_cached)]  
  
 In questo esempio viene disabilitata la replica DDL per una pubblicazione di tipo merge.  
  
 [!code-csharp[HowTo#rmo_ChangeMergePub_ddl](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changemergepub_ddl)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergePub_ddl](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changemergepub_ddl)]  
  
## <a name="see-also"></a>Vedere anche  
 [Pubblicare dati e oggetti di database](publish-data-and-database-objects.md)   
 [Modificare le proprietà di pubblicazioni e articoli](change-publication-and-article-properties.md)   
 [Apportare modifiche allo schema nei database di pubblicazione](make-schema-changes-on-publication-databases.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)   
 [Aggiungere ed eliminare articoli in una pubblicazione](add-articles-to-and-drop-articles-from-a-publication.md)   
 [Visualizzare le informazioni ed eseguire attività usando Monitoraggio replica](../monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Visualizzare e modificare le proprietà degli articoli](view-and-modify-article-properties.md)  
  
  
