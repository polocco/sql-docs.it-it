---
title: Sicurezza dell'agente di lettura log (SSMS)
description: Descrive la pagina "Sicurezza agente di lettura log" per una pubblicazione transazionale e peer-to-peer in SQL Server Management Studio (SSMS).
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.p2pwizard.LRA.f1
ms.assetid: 6575e2a8-16bb-449c-bdca-4a4202d0972f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ef28a7831ad5d4c63b450da177037d55534b5f63
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85716763"
---
# <a name="log-reader-agent-security-peer-to-peer-replication"></a>Sicurezza agente di lettura log (replica peer-to-peer)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  La pagina **Sicurezza agente di lettura log** consente di specificare gli account con cui viene eseguito l'agente di lettura in ogni peer e vengono stabilite le connessioni. Per informazioni sulle autorizzazioni necessarie per gli agenti e le procedure migliori per la sicurezza della replica, vedere [Modello di sicurezza dell'agente di replica](../../relational-databases/replication/security/replication-agent-security-model.md) e [Procedure consigliate per la sicurezza della replica](../../relational-databases/replication/security/replication-security-best-practices.md).  
  
> [!NOTE]  
>  esiste un agente di lettura log per ogni database pubblicato tramite la replica transazionale. Se l'agente di lettura log per un database è già stato configurato per una pubblicazione nel corso di una precedente esecuzione di questa procedura guidata oppure per un'altra pubblicazione transazionale nello stesso database, in questa procedura guidata non è possibile modificare le credenziali utilizzate dall'agente di lettura log. Se vengono specificate nuove credenziali, queste verranno ignorate. Per modificare le credenziali utilizzare la finestra di dialogo **Proprietà pubblicazione** . Per altre informazioni, vedere [View and Modify Replication Security Settings](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
## <a name="options"></a>Opzioni  
 Fare clic sul pulsante delle proprietà ( **...** ) nella riga di ogni peer per accedere alla finestra di dialogo **Sicurezza agente di lettura log** . Per ulteriori informazioni sulle autorizzazioni necessarie per gli account utilizzati dall'agente, fare clic su **?** nella finestra di dialogo **Sicurezza agente di lettura log** visualizzata.  
  
 Dopo aver immesso le impostazioni nella finestra di dialogo, nella griglia vengono visualizzate le informazioni sulla connessione per il Sottoscrittore.  
  
 **Agenti per il server di pubblicazione**  
 Nome di ogni istanza del server peer.  
  
 **Database peer**  
 Database che funge da database di pubblicazione e da database di sottoscrizione in ogni peer.  
  
 **Connessione al server di distribuzione**  
 Contesto in cui viene creata la connessione al server di distribuzione. La connessione locale al server di distribuzione viene sempre stabilita usando il contesto dell'account di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows con cui viene eseguito l'agente e in questo campo, quindi, verrà sempre visualizzato **Rappresenta '\<Domain>\\<Login\>'** o **Rappresenta '\<Computer>\\<Login\>'** .  
  
 **Connessione server di pubblicazione**  
 Contesto nel quale viene stabilita la connessione al server di pubblicazione. La connessione al server di pubblicazione può essere stabilita usando un account di accesso di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oppure usando il contesto dell'account di Windows con cui viene eseguito l'agente. In questo campo viene visualizzato uno dei valori seguenti: **Usa l'account di accesso '\<Login>'** , **Rappresenta '\<Domain>\\<Login\>'** o **Rappresenta '\<Computer>\\<Login\>'** . [!INCLUDE[msCoName](../../includes/msconame-md.md)] consiglia di stabilire tutte le connessioni utilizzando il contesto dell'account di Windows.  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrare una topologia peer-to-peer &#40;programmazione Transact-SQL della replica&#41;](../../relational-databases/replication/administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)   
 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)  
  
  
