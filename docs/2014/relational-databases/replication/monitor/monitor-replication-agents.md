---
title: Monitorare gli agenti di replica | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], agents
- Log Reader Agent, monitoring
- Replication Monitor, agents
- Merge Agent, monitoring
- Queue Reader Agent, monitoring
- Snapshot Agent, monitoring
- agents [SQL Server replication], monitoring
- Distribution Agent, monitoring
ms.assetid: d06ed24f-82d7-4b9e-9e40-cc9780476a71
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 64d764d874410f835dee0d02360a2bc78bc35e73
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85005923"
---
# <a name="monitor-replication-agents"></a>Monitoraggio degli agenti di replica
  Monitoraggio replica di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] offre una visualizzazione a livello di sistema dell'attività di replica e semplifica l'individuazione di informazioni su un agente specifico. Nell'elenco seguente vengono inclusi tutti gli agenti, le relative schede di Monitoraggio replica e un collegamento all'argomento in cui si spiega come accedere a queste schede:  
  
-   Gli agenti seguenti sono associati alle pubblicazioni in Monitoraggio replica:  
  
    -   agente snapshot  
  
    -   Agente di lettura log  
  
    -   Agente di lettura coda  
  
     Per accedere alle informazioni e alle attività associate a questi agenti utilizzare la scheda **Agenti** , disponibile per ogni server di pubblicazione e pubblicazione, e la scheda **Avvisi** , disponibile per ogni pubblicazione. Per altre informazioni, vedere [Visualizzare le informazioni ed eseguire attività usando Monitoraggio replica](view-information-and-perform-tasks-replication-monitor.md).  
  
-   Gli agenti seguenti sono associati alle sottoscrizioni in Monitoraggio replica:  
  
    -   Agente di distribuzione  
  
    -   Agente di merge  
  
     Per accedere alle informazioni e alle attività associate a questi agenti utilizzare le schede di pubblicazione seguenti: **Elenco verifica sottoscrizioni** (disponibile per tutti i server di pubblicazione) o **Tutte le sottoscrizioni** (disponibile per tutte le pubblicazioni). Per ulteriori informazioni, vedere [visualizzare le informazioni ed eseguire attività tramite Monitoraggio replica](view-information-and-perform-tasks-replication-monitor.md).  
  
## <a name="using-sql-server-management-studio-to-monitor-replication-agents"></a>Utilizzo di SQL Server Management Studio per il monitoraggio degli agenti di replica  
 In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] sono disponibili le finestre di dialogo seguenti per il monitoraggio degli agenti di replica:  
  
-   **Visualizza stato agente snapshot** (per tutte le pubblicazioni)  
  
-   **Visualizza stato agente di lettura log** (per tutte le pubblicazioni transazionali)  
  
-   **Visualizza stato sincronizzazione** (per tutte le sottoscrizioni: questa finestra di dialogo consente l'accesso all'agente di distribuzione e all'agente di merge)  
  
 Monitoraggio replica offre informazioni aggiuntive su ogni agente e consente di monitorare l'agente di lettura coda, se utilizzato. Per ulteriori informazioni, vedere [visualizzare le informazioni ed eseguire attività tramite Monitoraggio replica](view-information-and-perform-tasks-replication-monitor.md).  
  
#### <a name="to-monitor-the-snapshot-agent-and-log-reader-agent"></a>Per monitorare l'agente snapshot e l'agente di lettura log  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
3.  Fare clic con il pulsante destro del mouse su una pubblicazione e quindi scegliere **Visualizza stato agente di lettura log** o **Visualizza stato agente snapshot**.  
  
4.  Nella finestra di dialogo **Visualizza stato agente di lettura log** o **Visualizza stato agente snapshot** :  
  
    -   Visualizzare lo stato dell'agente.  
  
    -   Avviare o arrestare l'agente se necessario.  
  
    -   Fare clic su **Esegui monitoraggio** per avviare **Monitoraggio replica**.  
  
5.  Fare clic su **Close**.  
  
#### <a name="to-monitor-the-distribution-agent-and-merge-agent-from-the-publisher"></a>Per monitorare l'agente di distribuzione e l'agente di merge (dal server di pubblicazione)  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
3.  Espandere la pubblicazione della sottoscrizione da monitorare.  
  
4.  Fare clic con il pulsante destro del mouse sulla sottoscrizione e quindi scegliere **Visualizza stato sincronizzazione**.  
  
5.  Nella finestra di dialogo **Visualizza stato sincronizzazione** :  
  
    -   Visualizzare lo stato dell'agente.  
  
    -   Avviare o arrestare l'agente se necessario.  
  
    -   Per le sottoscrizioni push fare clic su **Esegui monitoraggio** per avviare **Monitoraggio replica**.  
  
    -   Per le sottoscrizioni pull fare clic su **Visualizza cronologia processi** per avviare **Visualizzatore file log**e visualizzare l'output del log dell'agente.  
  
6.  Fare clic su **Close**.  
  
#### <a name="to-monitor-the-distribution-agent-and-merge-agent-from-the-subscriber"></a>Per monitorare l'agente di distribuzione e l'agente di merge (dal Sottoscrittore)  
  
1.  Connettersi al Sottoscrittore in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Sottoscrizioni locali** .  
  
3.  Fare clic con il pulsante destro del mouse sulla sottoscrizione che si desidera monitorare e quindi scegliere **Visualizza stato sincronizzazione**.  
  
4.  Nella finestra di dialogo **Visualizza stato sincronizzazione** :  
  
    -   Visualizzare lo stato dell'agente.  
  
    -   Avviare o arrestare l'agente se necessario.  
  
    -   Fare clic su **Visualizza cronologia processi** per avviare **Visualizzatore file log**e visualizzare l'output del log dell'agente.  
  
5.  Fare clic su **Close**.  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio della replica](../monitoring-replication.md)   
 [Panoramica degli agenti di replica](../agents/replication-agents-overview.md)  
  
  
