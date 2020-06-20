---
title: Sincronizzare una sottoscrizione mediante Gestione sincronizzazione Microsoft Windows (Gestione sincronizzazione Microsoft Windows) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- synchronization [SQL Server replication], Windows Synchronization Manager
- Windows Synchronization Manager
ms.assetid: 80f15dd6-e84d-4f96-9866-5b34ea531f1e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 49f1b0832fb82425874b656715091f793b79dfd5
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85004494"
---
# <a name="synchronize-a-subscription-using-windows-synchronization-manager-windows-synchronization-manager"></a>Sincronizzazione di una sottoscrizione mediante Gestione sincronizzazione Microsoft Windows (Gestione sincronizzazione Microsoft Windows)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Synchronization Manager può essere utilizzato solo per sincronizzare le sottoscrizioni con le pubblicazioni Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene eseguito nello stesso computer in cui è installato il componente Gestione sincronizzazione, nonché per sincronizzare pagine Web e file offline. Per utilizzare Gestione sincronizzazione:  
  
1.  Abilitare la sincronizzazione delle sottoscrizioni pull con Gestione sincronizzazione Microsoft Windows nella finestra di dialogo **Proprietà sottoscrizione- \<Subscriber> : \<SubscriptionDatabase> ** . Per altre informazioni sull'accesso a questa finestra di dialogo, vedere [Visualizzare e modificare le proprietà delle sottoscrizioni pull](view-and-modify-pull-subscription-properties.md).  
  
2.  Accedere a Gestione sincronizzazione mediante il menu **Start** di Windows.  
  
 Gestione sincronizzazione consente di utilizzare il sistema di risoluzione interattivo per le sottoscrizioni di tipo merge. Generalmente, i conflitti rilevati durante la sincronizzazione vengono risolti automaticamente, ma se la risoluzione interattiva è abilitata, essi possono essere risolti da un utente in fase di sincronizzazione. Se una sincronizzazione viene eseguita all'esterno di Gestione sincronizzazione Microsoft Windows (come sincronizzazione pianificata o sincronizzazione su richiesta in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o Monitoraggio replica), i conflitti vengono risolti automaticamente senza richiedere l'intervento dell'utente, in base al sistema di risoluzione specificato per l'articolo.  
  
> [!NOTE]  
>  A partire da [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] e [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)], le versioni a 64 bit di Gestione sincronizzazione Microsoft Windows non possono rilevare sottoscrizioni a 32 bit.  
  
### <a name="to-enable-the-synchronization-of-pull-subscriptions-with-windows-synchronization-manager"></a>Per abilitare la sincronizzazione delle sottoscrizioni pull con Gestione sincronizzazione Microsoft Windows  
  
1.  Nella pagina **generale** della finestra di dialogo **Proprietà sottoscrizione \<Subscriber> - \<SubscriptionDatabase> :** selezionare il valore **attiva** per l'opzione **Usa Gestione sincronizzazione Microsoft Windows** .  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-synchronize-a-pull-subscription-with-synchronization-manager"></a>Per sincronizzare una sottoscrizione pull con Gestione sincronizzazione  
  
1.  Avviare Gestione sincronizzazione in uno dei modi seguenti:  
  
    -   In Internet Explorer scegliere **Sincronizza**dal menu **Strumenti**.  
  
    -   Fare clic sul menu **Start**, scegliere **Programmi** o **Tutti i i programmi**, quindi **Accessori**e fare clic su **Sincronizza**.  
  
    -   Fare clic sul pulsante **Start**, quindi scegliere **Esegui.** Nella finestra di dialogo **Esegui** Digitare `mobsync.exe` il campo **Apri** e quindi fare clic su **OK**.  
  
2.  Nella finestra di dialogo **Sincronizzazione elementi** selezionare le sottoscrizioni da sincronizzare. Le sottoscrizioni vengono elencate al di sotto delle istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installate nel computer.  
  
3.  Fare clic su **Sincronizza**.  
  
### <a name="to-reinitialize-a-pull-subscription-with-synchronization-manager"></a>Per reinizializzare una sottoscrizione pull con Gestione sincronizzazione  
  
1.  Nella finestra di dialogo **Sincronizzazione elementi** selezionare una sottoscrizione e quindi fare clic su **Proprietà**.  
  
2.  Nella finestra di dialogo **Proprietà sottoscrizione SQL Server** fare clic su **Reinizializza sottoscrizione**.  
  
3.  Fare clic su **Sì**.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Alla successiva sincronizzazione, per impostazione predefinita verrà applicato un nuovo snapshot al database di sottoscrizione. Per altre informazioni, vedere [Reinizializzare le sottoscrizioni](reinitialize-subscriptions.md).  
  
> [!NOTE]  
>  La replica di tipo merge consente il caricamento nel server di pubblicazione delle eventuali modifiche in attesa prima dell'applicazione dello snapshot. Tale opzione tuttavia non è disponibile da Gestione sincronizzazione. Per caricare le modifiche, sincronizzare la sottoscrizione prima di reinizializzarla.  
  
### <a name="to-set-properties-for-a-pull-subscription-in-synchronization-manager"></a>Per impostare le proprietà di una sottoscrizione pull in Gestione sincronizzazione  
  
1.  Nella finestra di dialogo **Sincronizzazione elementi** selezionare una sottoscrizione e quindi fare clic su **Proprietà**.  
  
2.  Visualizzare e modificare le proprietà nelle schede seguenti:  
  
    -   **Identificazione**  
  
    -   **Accesso al Sottoscrittore**, **Accesso al server di distribuzione**e **Accesso al server di pubblicazione** (solo per la replica di tipo merge)  
  
    -   **Informazioni server Web** (per le sottoscrizioni di tipo merge nei Sottoscrittori in cui è in esecuzione SQL Server 2005 o versione successiva)  
  
    -   **Altri**  
  
     È consigliabile utilizzare l'autenticazione di Windows per tutte le connessioni. Per informazioni sulle autorizzazioni necessarie con l'agente di distribuzione e l'agente di merge, vedere [Replication Agent Security Model](security/replication-agent-security-model.md).  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-remove-a-pull-subscription-from-synchronization-manager"></a>Per rimuovere una sottoscrizione pull da Gestione sincronizzazione  
  
1.  Nella finestra di dialogo **Sincronizzazione elementi** selezionare una sottoscrizione e quindi fare clic su **Proprietà**.  
  
2.  Nella finestra di dialogo **Proprietà sottoscrizione SQL Server** fare clic su **Rimuovi sottoscrizione**.  
  
3.  Selezionare un'opzione nella finestra di dialogo **Rimuovi sottoscrizione** .  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-use-the-interactive-resolver"></a>Per utilizzare il sistema di risoluzione interattivo  
  
1.  Abilitare l'articolo e la sottoscrizione per l'utilizzo della risoluzione interattiva. Per altre informazioni, vedere [Specificare la risoluzione interattiva dei conflitti per articoli di merge](../../relational-databases/replication/publish/specify-merge-replication-properties.md#interactive-conflict-resolution).
  
2.  In seguito all'inizio della sincronizzazione della sottoscrizione in Gestione sincronizzazione, il sistema di risoluzione interattivo viene avviato automaticamente se la risoluzione interattiva dei conflitti è abilitata e si sono verificati conflitti tra uno o più articoli. In tale sistema i conflitti vengono visualizzati uno alla volta, con un suggerimento di risoluzione per ogni conflitto (in base al sistema di risoluzione dei conflitti specificato al momento della creazione della pubblicazione e della sottoscrizione).  
  
3.  Facoltativamente, modificare le colonne visualizzate nel sistema di risoluzione interattivo e quindi fare clic su uno dei pulsanti seguenti per risolvere il conflitto:  
  
    -   **Accetta soluzione proposta**  
  
    -   **Accetta server di pubblicazione**  
  
    -   **Accetta Sottoscrittore**  
  
    -   **Risolvi tutti i conflitti automaticamente** (tutti i conflitti correnti vengono risolti senza ulteriore input)  
  
     La riga selezionata viene quindi applicata al server di pubblicazione e/o al Sottoscrittore e propagata ad altri nodi nella topologia durante le sincronizzazioni successive.  
  
> [!NOTE]  
>  Le modifiche vengono applicate solo se fanno parte della riga scelta per la risoluzione. Se, ad esempio, si apportano modifiche nel **Server di pubblicazione**e quindi si fa clic su **Accetta Sottoscrittore**, le modifiche verranno ignorate.  
  
## <a name="see-also"></a>Vedere anche  
 [Interactive Conflict Resolution](merge/advanced-merge-replication-conflict-interactive-resolution.md)  
  
