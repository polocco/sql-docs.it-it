---
title: Eseguire il debug di un gestore della logica di business (programmazione della replica)
description: Informazioni su come usare un gestore della logica di business per chiamare logica di business personalizzata quando viene sincronizzata una sottoscrizione di tipo merge.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- merge replication business logic handlers [SQL Server replication]
- business logic handlers [SQL Server replication]
- BusinessLogicModule class
ms.assetid: edd0d17a-0e9c-4c28-8395-a7d47e8ce3d6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 66e0df2599b8ada5f1c7dc3018e8021e2ee03df7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85654049"
---
# <a name="debug-a-business-logic-handler-replication-programming"></a>Debug di un gestore della logica di business (programmazione della replica)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Utilizzare un gestore della logica di business per richiamare logica di business personalizzata quando viene sincronizzata una sottoscrizione di tipo merge. Per altre informazioni, vedere [Eseguire logiche di business durante la sincronizzazione di tipo merge](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md).  
  
 Il Riconciliatore replica di tipo merge (replrec.dll) chiama l'assembly del codice gestito contenente la logica di business. Nella maggior parte dei casi, replrec.dll e la logica di business personalizzata vengono eseguiti nello stesso computer dell'agente di merge, ovvero nel Sottoscrittore per una sottoscrizione pull o nel server di distribuzione per una sottoscrizione push. Nel caso della sincronizzazione tramite il Web o nel caso di un Sottoscrittore [!INCLUDE[ssEW](../../includes/ssew-md.md)] , il riconciliatore e la logica di business personalizzata vengono eseguiti nel server Web.  
  
### <a name="to-debug-a-business-logic-handler-on-a-local-computer"></a>Per eseguire il debug di un gestore della logica di business in un computer locale  
  
1.  Configurare la pubblicazione e la distribuzione, creare una pubblicazione, quindi creare una sottoscrizione della pubblicazione. Per altre informazioni, vedere [Configurare la pubblicazione e la distribuzione](../../relational-databases/replication/configure-publishing-and-distribution.md) e [Creare una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Creare e registrare un gestore della logica di business. Per altre informazioni, vedere [Implementare un gestore della logica di business per un articolo di merge](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md).  
  
3.  Creare un progetto RMO (Replication Management Objects) in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio che avvia a livello di programmazione l'agente di merge in modo sincrono. Per altre informazioni, vedere [Sincronizzazione di una sottoscrizione pull](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
4.  Impostare un punto di interruzione nel codice del gestore della logica di business, in particolare nel metodo sottoposto a debug o nel costruttore della classe. Per ulteriori informazioni sui metodi che è possibile implementare in un gestore della logica di business, vedere gli argomenti relativi ai metodi degli oggetti <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> .  
  
5.  Compilare il gestore della logica di business in modalità debug e distribuire il file di simboli (pdb) del debug e dell'assembly nel percorso registrato nel passaggio 1.  
  
    > [!NOTE]  
    >  Per semplificare il debug, creare una singola soluzione di Visual Studio .NET che contiene sia il progetto di gestore della logica di business che il progetto per la sincronizzazione della sottoscrizione. In questo caso, impostare il progetto di sincronizzazione come progetto di avvio e configurare l'ambiente di compilazione per la distribuzione dell'assembly della logica di business nel percorso registrato nel passaggio 1 durante il debug.  
  
6.  Eseguire comandi di inserimento, aggiornamento o eliminazione sul database di sottoscrizione o pubblicazione. Il comando e il percorso di esecuzione dipendono dal metodo da sottoporre a debug.  
  
7.  Avviare il progetto dal passaggio 3 in modalità debug per sincronizzare la sottoscrizione.  
  
8.  Presupponendo che non siano stati impostati altri punti di interruzione e che vengano replicati i comandi appropriati, l'esecuzione si arresta quando raggiunge il punto di interruzione nel gestore della logica di business.  
  
### <a name="to-debug-a-business-logic-handler-on-a-web-server-using-web-synchronization-or-for-a-sql-server-compact-subscriber"></a>Per eseguire il debug di un gestore della logica di business in un server Web utilizzando la sincronizzazione tramite il Web oppure per un Sottoscrittore di SQL Server Compact  
  
1.  Configurare la pubblicazione e la distribuzione, creare una pubblicazione, quindi creare una sottoscrizione pull della pubblicazione. La pubblicazione deve supportare la sincronizzazione Web o i Sottoscrittori [!INCLUDE[ssEW](../../includes/ssew-md.md)] .  
  
2.  Creare e registrare un gestore della logica di business. Per altre informazioni, vedere [Implementare un gestore della logica di business per un articolo di merge](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md).  
  
3.  Impostare un punto di interruzione nel codice del gestore della logica di business, in particolare nel metodo sottoposto a debug o nel costruttore della classe. Per ulteriori informazioni sui metodi che è possibile implementare in un gestore della logica di business, vedere gli argomenti relativi ai metodi degli oggetti <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> .  
  
4.  Compilare il gestore della logica di business in modalità debug e distribuire il file di simboli (pdb) del debug e dell'assembly nel server Web nel percorso registrato nel passaggio 1.  
  
    > [!NOTE]  
    >  Se è impossibile compilare il gestore della logica di business perché l'assembly è in uso, digitare il comando `iisreset` al prompt dei comandi del server Web per reimpostare il server Web.  
  
5.  Sincronizzare la sottoscrizione con la sincronizzazione tramite il Web abilitata. Durante la sincronizzazione, il server Web carica l'assembly registrato.  
  
6.  Utilizzando il debugger Visual Studio .NET, collegarsi a uno dei processi seguenti nel server Web:  
  
    -   w3wp.exe - Windows Server 2003.  
  
    -   inetinfo.exe - Windows 2000 e Windows XP.  
  
7.  Nella finestra **Output** controllare l'output di debug per verificare che i simboli per l'assembly registrato siano stati caricati correttamente. Se i simboli non sono stati caricati, assicurarsi che nel passaggio 4 sia stato copiato il file con estensione pbd corretto, quindi ripetere il passaggio 5.  
  
8.  Eseguire comandi di inserimento, aggiornamento o eliminazione sul database di sottoscrizione o pubblicazione. Il comando e il percorso di esecuzione dipendono dal metodo da sottoporre a debug.  
  
9. Utilizzando il debugger di Visual Studio, collegarsi al processo w3wp.exe.  
  
10. Sincronizzare nuovamente la sottoscrizione utilizzando la sincronizzazione tramite il Web.  
  
11. Presupponendo che non siano stati impostati altri punti di interruzione e che vengano replicati i comandi appropriati, l'esecuzione si arresta quando raggiunge il punto di interruzione nel gestore della logica di business.  
  
## <a name="see-also"></a>Vedere anche  
 [Implementare un gestore della logica di business per un articolo di merge](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)  
  
  
