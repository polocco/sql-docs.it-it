---
title: Configura topologia (replica peer-to-peer) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.p2pwizard.peers.f1
ms.assetid: 5377c59f-2e25-4852-a306-c87ae3dca9fd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e06e271f8f75fea1cf98c9d8f9697cbfe49c412e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773986"
---
# <a name="configure-topology-peer-to-peer-replication"></a>Configura topologia (replica peer-to-peer)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  La pagina **Configura topologia** consente di eseguire attività di configurazione comuni, ad esempio l'aggiunta di nuovi nodi, l'eliminazione di nodi e l'aggiunta di nuove connessioni tra nodi esistenti. Il nodo selezionato nella pagina **Pubblicazione** di questa procedura guidata viene visualizzato nell'area di progettazione. Per specificare le opzioni di configurazione, fare clic con il pulsante destro del mouse su un nodo, su una connessione o sull'area di progettazione.  
  
> [!NOTE]  
>  La Configurazione guidata topologia peer-to-peer richiede informazioni sulla topologia quando viene chiusa. Se la procedura guidata viene chiusa e riaperta prima che tutti i nodi rispondano alla richiesta di informazioni, è possibile che venga visualizzata una rete parziale.  
  
## <a name="options"></a>Opzioni  
 La pagina **Configura topologia** contiene elementi e opzioni dell'interfaccia che sono disponibili quando si fa clic con il pulsante destro del mouse su un elemento. Nella tabella riportata di seguito viene descritto ogni elemento dell'interfaccia.  
  
|Elemento dell'interfaccia|Descrizione|  
|-----------------------|-----------------|  
|Area di progettazione|Consente di visualizzare gli altri elementi dell'interfaccia. Per aggiungere elementi, fare clic con il pulsante destro del mouse sull'area di progettazione.|  
|![Primo nodo di una topologia](../../relational-databases/replication/media/p2pwizard-firstnode.gif "Primo nodo di una topologia")|Nodo originale nella topologia. I nuovi nodi vengono inizializzati utilizzando una copia del database di pubblicazione dal nodo originale.|  
|![Nodo per cui si dispone di informazioni complete](../../relational-databases/replication/media/p2pwizard-complete.gif "Nodo per cui si dispone di informazioni complete")|Nodo che esegue un'istanza di [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] o versione successiva per cui la replica dispone di informazioni complete. Per specificare le opzioni di configurazione, fare clic con il pulsante destro del mouse sul nodo.|  
|![Nodo per cui si dispone di informazioni incomplete](../../relational-databases/replication/media/p2pwizard-incomplete.gif "Nodo per cui si dispone di informazioni incomplete")|Nodo per cui la replica dispone di informazioni incomplete. Per specificare le opzioni di configurazione, fare clic con il pulsante destro del mouse sul nodo.<br /><br /> La replica dispone di informazioni incomplete a causa di una delle ragioni seguenti:<br /><br /> -Il nodo esegue un'istanza di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]che non archivia tutti i metadati richiesti dalla procedura guidata.<br /><br /> -Il nodo esegue una versione più recente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ma la replica non è in grado di recuperare le informazioni sulla sottoscrizione dal nodo. Per risolvere questa situazione:<br /><br /> Verificare che il database nel nodo sia online e che sia possibile connettersi utilizzando le stesse credenziali degli agenti di distribuzione che si connettono al nodo.<br /><br /> Verificare che l'agente di lettura log e tutti gli agenti di distribuzione che si connettono al nodo siano in esecuzione.<br /><br /> Verificare che il timeout di aggiornamento sia impostato su un valore abbastanza elevato per consentire di raccogliere tutte le informazioni sulla topologia. Per impostare il timeout, fare clic con il pulsante destro del mouse sull'area di progettazione, quindi scegliere **Imposta timeout aggiornamento**.|  
|Linea grigia con frecce|Connessione tra due nodi. Per aggiungere una connessione, fare clic con il pulsante destro del mouse su uno dei nodi che si desidera connettere. Per rimuovere una connessione, fare clic con il pulsante destro del mouse sulla connessione.<br /><br /> Se la linea ha una sola freccia, la replica dispone di informazioni incomplete per uno dei nodi.|  
  
### <a name="options-for-the-design-surface"></a>Opzioni per l'area di progettazione  
 **Ridisegna grafico**  
 Consente di ridisegnare gli oggetti sull'area di progettazione senza aggiornare la topologia. Questa operazione potrebbe offrire una vista migliore della topologia.  
  
 **Aggiorna topologia**  
 Consente di eseguire una query su ogni nodo della topologia e visualizzare informazioni aggiornate su ogni nodo. Se vi sono molti nodi, questo processo può richiedere parecchi minuti.  
  
 Se durante la procedura guidata vengono richieste informazioni sulla topologia e si chiude e si riapre la procedura guidata prima che tutti i nodi rispondano alla richiesta, in questa pagina potrebbero non essere visualizzati tutti i nodi della topologia.  
  
 **Aggiungi nuovo nodo peer**  
 Consente di aggiungere un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alla topologia peer-to-peer. L'aggiunta di un'istanza come nodo consente di creare una pubblicazione in tale istanza dopo il completamento della procedura guidata. Dopo avere aggiunto il nodo, fare clic con il pulsante destro del mouse su di esso per aggiungere una connessione tra il nuovo nodo e un nodo esistente.  
  
 Per partecipare a una topologia peer-to-peer, l'istanza deve soddisfare i requisiti seguenti:  
  
-   Deve essere già configurata come server di distribuzione o deve essere associata a un server di distribuzione remoto.  
  
-   Deve contenere una copia del database coinvolto nella replica. Questa copia è in genere un backup ripristinato del database di pubblicazione originale.  
  
 **Seleziona nodo/i da visualizzare**  
 Consente di selezionare i nodi da visualizzare nell'area di progettazione. Questa opzione è utile se la topologia include molti di nodi. Tenere presente che è possibile aggiungere connessioni solo tra nodi visibili nell'area di progettazione.  
  
 **Imposta timeout aggiornamento**  
 Consente di specificare per quanto tempo può essere eseguito il processo di aggiornamento prima del timeout dell'operazione.  
  
### <a name="options-for-each-node"></a>Opzioni per ogni nodo  
 **Aggiungi nuova connessione peer**  
 Consente di aggiungere una connessione tra due nodi. Se, ad esempio, si aggiunge una connessione tra Nodo A e Nodo B, tramite la replica vengono aggiunte due sottoscrizioni: la prima consente a Nodo A di ricevere le modifiche dalla pubblicazione in Nodo B e la seconda consente a Nodo B di ricevere le modifiche dalla pubblicazione in Nodo A.  
  
 **Elimina nodo peer**  
 Consente di rimuovere un nodo dalla topologia. Se, ad esempio, si rimuove Nodo C, la pubblicazione in quel nodo viene rimossa. Vengono rimosse anche le sottoscrizioni tra Nodo A e Nodo C e tra Nodo B e Nodo C. Il database in Nodo C non viene eliminato e la pubblicazione e la distribuzione non vengono disabilitate.  
  
> [!NOTE]  
>  Quando si configura la replica peer-to-peer, viene specificato un ID per ogni nodo. Tale ID, che deve essere univoco in tutti i nodi nella topologia, viene archiviato nella colonna originator_id della tabella di sistema [MSpeer_originatorid_history](../../relational-databases/system-tables/mspeer-originatorid-history-transact-sql.md). Se un nodo viene rimosso dalla topologia, l'ID viene comunque conservato nella tabella della cronologia per impedire falsi conflitti, qualora siano presenti modifiche provenienti dal nodo rimosso che continuano ad essere replicate nella topologia. Se si desidera riutilizzare l'ID per un nuovo nodo, è necessario prima eliminarlo manualmente dalla tabella MSpeer_originatorid_history in tutti i nodi. Prima di eliminare un ID per un nodo, eseguire [sp_requestpeerresponse](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) per verificare che tutte le modifiche provenienti dal nodo siano state replicate.  
  
 **Connessione a TUTTI i nodi visualizzati**  
 Consente di aggiungere connessioni tra il nodo selezionato e tutti gli altri nodi. Se, ad esempio, si seleziona questa opzione per Nodo C in una topologia a tre nodi, tramite la replica vengono aggiunte quattro sottoscrizioni: due che consentono a Nodo A e Nodo B di ricevere le modifiche dalla pubblicazione in Nodo C e due che consentono a Nodo C di ricevere le modifiche dalle pubblicazioni in Nodo A e Nodo B.  
  
 **Seleziona nodo/i da visualizzare**  
 Consente di selezionare i nodi da visualizzare nell'area di progettazione. Questa opzione è utile se la topologia include molti di nodi. Tenere presente che è possibile aggiungere connessioni solo tra nodi visibili nell'area di progettazione.  
  
### <a name="options-for-the-connection-arrows"></a>Opzioni per le frecce di connessione  
 **Rimuovi connessione peer**  
 Consente di rimuovere una connessione tra due nodi. Se, ad esempio, si rimuove una connessione tra Nodo A e Nodo B, tramite la replica vengono eliminate due sottoscrizioni: quella che consente a Nodo A di ricevere le modifiche dalla pubblicazione in Nodo B e quella che consente a Nodo B di ricevere le modifiche dalla pubblicazione in Nodo A.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare la pubblicazione e la distribuzione](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Amministrare una topologia peer-to-peer &#40;programmazione Transact-SQL della replica&#41;](../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  
