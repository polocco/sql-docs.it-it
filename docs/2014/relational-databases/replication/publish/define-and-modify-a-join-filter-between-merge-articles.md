---
title: Definire e modificare un filtro di join tra articoli di merge | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server replication], join
- merge replication join filters [SQL Server replication]
- modifying filters, join
- join filters
ms.assetid: f7f23415-43ff-40f5-b3e0-0be1d148ee5b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bf8b3b4f00ad2e8a3b9236292ee20948c852b6ef
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "68199549"
---
# <a name="define-and-modify-a-join-filter-between-merge-articles"></a>Definizione e modifica di un filtro di join tra articoli di merge
  In questo argomento viene descritto come definire e modificare un filtro di join tra articoli di merge in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)]. La replica di tipo merge supporta i filtri di join, solitamente utilizzati in combinazione con filtri con parametri per estendere il partizionamento della tabella ad altri articoli correlati.  
  
 **Contenuto dell'articolo**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Indicazioni](#Recommendations)  
  
-   **Per definire e modificare di un filtro di join tra articoli di merge, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Per creare un filtro di join, la pubblicazione deve contenere almeno due tabelle correlate. Dal momento che i filtri join rappresentano un'estensione dei filtri di riga, è necessario definire prima un filtro di riga in una tabella da estendere con un join a un'altra tabella. Dopo aver definito un filtro di join, è possibile estenderlo con un altro filtro di join se la pubblicazione contiene ulteriori tabelle correlate.  
  
-   Se si aggiunge, modifica o elimina un filtro di join dopo che sono state inizializzate sottoscrizioni per la pubblicazione, è necessario generare un nuovo snapshot e reinizializzare tutte le sottoscrizioni in seguito alla modifica. Per altre informazioni sui requisiti per la modifica delle proprietà, vedere [Modificare le proprietà di pubblicazioni e articoli](change-publication-and-article-properties.md).  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Indicazioni  
  
-   È possibile creare manualmente filtri di join per un set di tabelle oppure generare automaticamente i filtri tramite la replica in base alle relazioni tra le chiavi esterne e le chiavi primarie definite nelle tabelle. Per altre informazioni sulla generazione automatica di un set di filtri di join, vedere [Generare automaticamente un set di filtri di join tra gli articoli di merge &#40;SQL Server Management Studio&#41;](automatically-generate-join-filters-between-merge-articles.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Definire, modificare ed eliminare filtri join nella pagina **Filtro righe tabella** della Creazione guidata nuova pubblicazione o nella pagina **Filtro righe** della finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>**. Per altre informazioni sull'uso della creazione guidata e l'accesso alla finestra di dialogo, vedere [Creare una pubblicazione](create-a-publication.md) e [Visualizzare e modificare le proprietà della pubblicazione](view-and-modify-publication-properties.md).  
  
#### <a name="to-define-a-join-filter"></a>Per definire un filtro di join  
  
1.  Nella pagina **Filtro righe tabella** della Creazione guidata nuova pubblicazione o nella pagina **Filtro righe** di **Proprietà pubblicazione - \<Pubblicazione>** selezionare un filtro di riga o un filtro di join esistente nel riquadro **Tabelle filtrate**.  
  
2.  Fare clic su **Aggiungi**e quindi su **Aggiungi join per estendere il filtro selezionato**.  
  
3.  Creare l'istruzione per il join. Selezionare **Per compilare l'istruzione verrà utilizzato il generatore** o **L'istruzione per il join verrà scritta manualmente**.  
  
    -   Se si sceglie di utilizzare il generatore, utilizzare le colonne della griglia, ovvero**Congiunzione**, **Colonna tabella filtrata**, **Operatore**e **Colonna tabella unita in join**, per compilare un'istruzione per il join.  
  
         Ogni colonna della griglia contiene una casella combinata a discesa, che consente di selezionare due colonne e un operatore (**=**, **<>**, **<=**, **\<**, **>=**, **>** e **like**). I risultati vengono visualizzati nell'area di testo **Anteprima** . Se il join è associato a più di due colonne, selezionare una congiunzione (AND oppure OR) dalla colonna **Congiunzione** e quindi immettere altre due colonne e un operatore.  
  
    -   Se si sceglie di scrivere manualmente l'istruzione per il join, digitarla nell'area di testo **Istruzione per il join** . Utilizzare le caselle di riepilogo **Colonne tabella filtrata** e **Colonne tabella unita in join** per trascinare le colonne nell'area di testo **Istruzione per il join** .  
  
    -   L'istruzione per il join completa sarà simile alla seguente:  
  
        ```  
        SELECT <published_columns> FROM [Sales].[SalesOrderHeader] INNER JOIN [Sales].[SalesOrderDetail] ON [SalesOrderHeader].[SalesOrderID] = [SalesOrderDetail].[SalesOrderID]  
        ```  
  
         Per la clausola JOIN è necessario utilizzare nomi composti da due parti, in quanto la denominazione a tre e quattro parti non è supportata.  
  
4.  Specificare le opzioni per il join:  
  
    -   Se la colonna nella quale viene eseguito il join della tabella filtrata, ovvero la tabella padre, è univoca, selezionare **Chiave univoca**.  
  
        > [!CAUTION]  
        >  Selezionando questa opzione si indica che la relazione tra la tabella padre e le tabelle figlio in un filtro join è uno-a-uno o uno-a-molti. Utilizzare questa opzione solo se esiste un vincolo nella colonna di join della tabella figlio che garantisce l'univocità. Se l'opzione è impostata in modo errato può impedire la convergenza dei dati.  
  
    -   Per impostazione predefinita, durante la sincronizzazione la replica di tipo merge elabora le modifiche riga per riga. Per apportare modifiche correlate nelle righe della tabella filtrata e della tabella unita in join elaborata come unità, selezionare **record logico** ([!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] solo e versioni successive). Questa opzione è disponibile solo se sono soddisfatti i requisiti relativi all'utilizzo dei record logici negli articoli e nelle pubblicazioni. Per altre informazioni, vedere la sezione "Considerazioni sull'utilizzo di record logici" in [Raggruppare modifiche alle righe correlate con record logici](../merge/group-changes-to-related-rows-with-logical-records.md).  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  Se è visualizzata la finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>** fare clic su **OK** per salvare e chiudere la finestra di dialogo.  
  
#### <a name="to-modify-a-join-filter"></a>Per modificare un filtro join  
  
1.  Nella pagina **Filtro righe tabella** della Creazione guidata nuova pubblicazione o nella pagina **Filtro righe** di **Proprietà pubblicazione - \<Pubblicazione>** selezionare un filtro nel riquadro **Tabelle filtrate** e quindi fare clic su **Modifica**.  
  
2.  Nella finestra di dialogo **Modifica join** modificare il filtro.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-delete-a-join-filter"></a>Per eliminare un filtro join  
  
1.  Nella pagina **Filtro righe tabella** della Creazione guidata nuova pubblicazione o nella pagina **Filtro righe** di **Proprietà pubblicazione - \<Pubblicazione>** selezionare un filtro nel riquadro **Tabelle filtrate** e quindi fare clic su **Elimina**. Se il filtro di join eliminato è esteso da altri join, anch'essi verranno eliminati.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Uso di Transact-SQL  
 Tali procedure indicano un filtro con parametri su un articolo padre con filtri di join tra questo articolo e gli articoli figlio correlati. I filtri join possono essere definiti e modificati a livello di programmazione tramite le stored procedure di replica.  
  
#### <a name="to-define-a-join-filter-to-extend-an-article-filter-to-related-articles-in-a-merge-publication"></a>Per definire un filtro join per estendere un filtro di articolo agli articoli correlati in una pubblicazione di tipo merge  
  
1.  Definire il filtro per l'articolo da unire in join, ovvero l'articolo padre.  
  
    -   Per un articolo a cui viene applicato un filtro di riga con parametri, vedere [Definizione e modifica di un filtro di riga con parametri per un articolo di merge](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
    -   Per un articolo a cui viene applicato un filtro di riga statico, vedere [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).  
  
2.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) per definire uno o più articoli correlati, noti anche come articoli figlio, per la pubblicazione. Per altre informazioni, vedere [definire un articolo](define-an-article.md).  
  
3.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_addmergefilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql). Specificare **@publication** **@filtername**un nome univoco per il filtro, il nome dell'articolo figlio creato nel passaggio 2 per **@article**, il nome dell'articolo padre da unire in join **@join_articlename**per e uno dei valori seguenti per: **@join_unique_key**  
  
    -   **0** : indica un join molti-a-uno o molti-a-molti tra gli articoli padre e figlio.  
  
    -   **1** : indica un join uno-a-uno o uno-a-molti tra gli articoli padre e figlio.  
  
     In questo modo viene definito un filtro join tra i due articoli.  
  
    > [!CAUTION]  
    >  Impostare **@join_unique_key** su **1** solo se si dispone di un vincolo nella colonna di join nella tabella sottostante per l'articolo padre che garantisce l'univocità. Se **@join_unique_key** è impostato su **1** in modo errato, è possibile che si verifichi la non convergenza dei dati.  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> Esempi (Transact-SQL)  
 In questo esempio viene definito un articolo per una pubblicazione di tipo merge, in cui all'articolo della tabella `SalesOrderDetail` viene applicato un filtro sulla tabella `SalesOrderHeader` , che presenta essa stessa un filtro di riga statico. Per altre informazioni, vedere [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
 In questo esempio viene definito un gruppo di articoli di una pubblicazione di tipo merge in cui agli articoli è applicata una serie di filtri di join sulla tabella `Employee` , che presenta essa stessa un filtro di riga con parametri sul valore [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql) nella colonna **LoginID** . Per altre informazioni, vedere [Definizione e modifica di un filtro di riga con parametri per un articolo di merge](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md).  
  
 [!code-sql[HowTo#sp_MergeDynamicPub1](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepubdynamic1.sql#sp_mergedynamicpub1)]  
  
## <a name="see-also"></a>Vedi anche  
 [Filtri join](../merge/join-filters.md)   
 [Filtri di riga con parametri](../merge/parameterized-filters-parameterized-row-filters.md)   
 [Modificare le proprietà di pubblicazioni e articoli](change-publication-and-article-properties.md)   
 [Filtrare i dati pubblicati per la replica di tipo merge](../merge/filter-published-data-for-merge-replication.md)   
 [Concetti relativi alle stored procedure del sistema di replica](../concepts/replication-system-stored-procedures-concepts.md)   
 [Definire una relazione tra record logici tra gli articoli di tabelle di merge](define-a-logical-record-relationship-between-merge-table-articles.md)   
 [Definizione e modifica di un filtro di riga con parametri per un articolo di merge](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)  
  
  
