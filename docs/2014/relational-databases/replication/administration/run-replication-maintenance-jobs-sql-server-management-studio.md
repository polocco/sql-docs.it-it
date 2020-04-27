---
title: Eseguire processi di manutenzione della replica (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server replication]
ms.assetid: 0dc485a0-5a50-41eb-a29d-f2b2fb920174
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f294ad3868670783d3010498dd0ba89e1e6a48be
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "63127056"
---
# <a name="run-replication-maintenance-jobs-sql-server-management-studio"></a>Esecuzione di processi di manutenzione della replica (SQL Server Management Studio)
  Nella replica vengono utilizzati i seguenti processi di manutenzione:  
  
-   **Reinizializzazione delle sottoscrizioni con errori di convalida dei dati**
-   **Eliminazione del contenuto della cronologia dell'agente: distribuzione**
-   **Aggiornamento del monitoraggio della replica per la distribuzione.**
-   **Controllo degli agenti di replica**
-   **Eliminazione del contenuto della distribuzione: distribuzione**
-   **Pulizia della sottoscrizione scaduta**  
  
 Avviare e arrestare questi processi dalla cartella **Processi** in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] e dalla scheda **Agenti** in Monitoraggio replica. Per informazioni sull'avvio di Monitoraggio replica, vedere [Avviare Monitoraggio replica](../monitor/start-the-replication-monitor.md). Visualizzare e modificare le proprietà per ogni processo nella finestra di dialogo **Proprietà processo - \<Processo>**, disponibile dalla stessa cartella e dalla stessa scheda.  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-management-studio"></a>Per avviare e arrestare un processo di manutenzione della replica in Management Studio  
  
1.  Connettersi al database di distribuzione in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], quindi espandere il nodo del server.  
  
2.  Espandere la cartella **SQL Server Agent** e quindi la cartella **Processi** .  
  
3.  Fare clic con il pulsante destro del mouse su un processo e quindi scegliere **Avvia processo** o **Arresta processo**.  
  
### <a name="to-start-or-stop-a-replication-maintenance-job-in-replication-monitor"></a>Per avviare e arrestare un processo di manutenzione della replica in Monitoraggio replica  
  
1.  Espandere un gruppo di server di pubblicazione in Monitoraggio replica e quindi selezionare un server di pubblicazione.  
  
2.  Fare clic sulla scheda **Agenti** .  
  
3.  Fare clic con il pulsante destro del mouse su un processo e quindi scegliere **Avvia processo** o **Arresta processo**.  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-management-studio"></a>Per visualizzare e modificare le proprietà per un processo di manutenzione della replica in Management Studio  
  
1.  Connettersi al database di distribuzione in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], quindi espandere il nodo del server.  
  
2.  Espandere la cartella **SQL Server Agent** e quindi la cartella **Processi** .  
  
3.  Fare clic con il pulsante destro del mouse su un processo e scegliere **Proprietà**.  
  
4.  Nella finestra di dialogo **Proprietà processo - \<Processo>** modificare le proprietà, se necessario, quindi fare clic su **OK**.  
  
### <a name="to-view-and-modify-properties-for-a-replication-maintenance-job-in-replication-monitor"></a>Per visualizzare e modificare le proprietà per un processo di manutenzione della replica in Monitoraggio replica  
  
1.  Espandere un gruppo di server di pubblicazione in Monitoraggio replica e quindi selezionare un server di pubblicazione.  
  
2.  Fare clic sulla scheda **Agenti** .  
  
3.  Fare clic con il pulsante destro del mouse su un processo nella griglia e quindi scegliere **Proprietà**.  
  
4.  Nella finestra di dialogo **Proprietà processo - \<Processo>** modificare le proprietà, se necessario, quindi fare clic su **OK**.  
  
## <a name="see-also"></a>Vedi anche  
 [Avviare e arrestare un agente di replica &#40;SQL Server Management Studio&#41;](../agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)   
 [Visualizzazione delle informazioni ed esecuzione di attività tramite Monitoraggio replica](../monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [Amministrazione dell'agente di replica](../agents/replication-agent-administration.md)  
  
  
