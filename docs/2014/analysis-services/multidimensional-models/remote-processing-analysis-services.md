---
title: Elaborazione remota (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d58bcb3c-0b3f-4ab0-81eb-4fdcc86153af
author: minewiskan
ms.author: owend
ms.openlocfilehash: 699cc312b2f4b0a716d08259daf189276551e5d4
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545770"
---
# <a name="remote-processing-analysis-services"></a>Elaborazione remota (Analysis Services)
  È possibile eseguire l'elaborazione pianificata o automatica in un'istanza remota di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , dove la richiesta di elaborazione proviene da un computer ma viene eseguita in un computer diverso nella stessa rete.  
  
## <a name="prerequisites"></a>Prerequisiti  
  
-   Se si eseguono versioni diverse di SQL Server in ogni computer, le librerie client devono corrispondere alla versione dell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] mediante la quale viene elaborato il modello. Ad esempio, se l'elaborazione viene eseguita in un'istanza di [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)] , la libreria client del computer da cui proviene la richiesta deve corrispondere a [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]. Vedere [Provider di dati utilizzati per le connessioni ad Analysis Services](../instances/data-providers-used-for-analysis-services-connections.md).  
  
-   Nel server remoto, **Consenti connessioni remote al computer** deve essere abilitato e l'account che esegue la richiesta di elaborazione deve essere elencato come utente consentito.  
  
-   Le regole di Windows Firewall devono essere configurate per consentire connessioni in ingresso ad [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Verificare che sia possibile connettersi all'istanza remota di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Vedere [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
-   Risolvere tutti gli errori di elaborazione locale esistenti prima di tentare l'elaborazione remota. Verificare che quando la richiesta di elaborazione è locale, i dati possono essere recuperati correttamente dall'origine dati relazionale esterna. Vedere [Impostare opzioni di rappresentazione &#40;SSAS - multidimensionale&#41;](set-impersonation-options-ssas-multidimensional.md) per istruzioni su come specificare le credenziali usate per recuperare i dati.  
  
## <a name="on-demand-remote-processing"></a>Elaborazione remota su richiesta  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vengono accettate richieste di elaborazione da account utente o applicazione che dispongono di autorizzazioni di amministratore di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Se si è un amministratore, verificare che sia possibile connettersi all'istanza remota ed elaborare il database manualmente tramite la connessione remota.  
  
1.  Nel computer che sarà usato per pianificare l'elaborazione, avviare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e connettersi all'istanza remota di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
2.  Fare clic con il pulsante destro del mouse sul database, selezionare **Processo**, puntare a **Script** , quindi scegliere **Genera script azione in nuova finestra Query**. I comandi usati per richiamare l'elaborazione verranno visualizzati nella finestra Query.  
  
3.  Fare clic su **OK** per iniziare l'elaborazione.  
  
     Il completamento di questa attività fornisce una query XMLA che è possibile includere in un processo pianificato. Conferma inoltre l'assenza di problemi di connessione.  
  
## <a name="schedule-remote-processing-using-sql-server-agent-service"></a>Pianificare l'elaborazione remota tramite il servizio SQL Server Agent  
 Per impostazione predefinita, il servizio SQL Server Agent viene eseguito con un account virtuale, con connessioni di rete effettuate usando l'account del computer. Per evitare di dover concedere diritti amministrativi di un account del computer nell'istanza remota di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , è necessario modificare l'account del servizio SQL Server Agent per un'esecuzione come account utente di dominio con privilegi minimi.  
  
 Assicurarsi di concedere tutte le autorizzazioni necessarie, inclusi i diritti **sysadmin** dell'account per l'istanza del motore di database che fornisce il servizio.  
  
 Usare i collegamenti seguenti per impostare le autorizzazioni:  
  
-   [Configurazione di SQL Server Agent](../../ssms/agent/configure-sql-server-agent.md)  
  
-   Tramite i[SQL Server Agent Components](../../ssms/agent/sql-server-agent.md#Components) vengono suggeriti i ruoli predefiniti del server qualora non sia possibile la concessione di autorizzazioni **sysadmin** .  
  
 Dopo aver configurato le autorizzazioni dell'account, continuare con i passaggi riportati di seguito.  
  
#### <a name="grant-the-sql-server-agent-account-administrator-permission-on-ssas"></a>Concedere l'autorizzazione di amministratore account di SQL Server Agent per SSAS  
  
1.  Tramite [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]connettersi all'istanza remota di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
2.  Fare clic con il pulsante destro del mouse sul nome del server, fare clic su**Proprietà**, quindi scegliere **Sicurezza**.  
  
3.  Fare clic su **Aggiungi** per aggiungere l'account di SQL Server Agent.  
  
#### <a name="create-the-job"></a>Creare il processo  
  
1.  In Management Studio connettersi all'istanza locale del motore di database. SQL Server Agent è l'ultimo elemento in Esplora oggetti. Se necessario, avviare il servizio.  
  
2.  Fare clic con il pulsante destro del mouse su **Processi**, fare clic su **Nuovo processo** , quindi immettere un nome.  
  
3.  In Passaggi fare clic su **Nuovo** , quindi immettere un nome.  
  
4.  In Tipo scegliere **Comando di SQL Server Analysis Services**.  
  
5.  In Server immettere il nome dell'istanza remota di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
6.  In Comando incollare il comando XMLA per elaborare il database. Si tratta dello script XMLA generato nel passaggio di verifica per l'elaborazione remota su richiesta. Fare clic su **OK** per salvare il processo.  
  
#### <a name="start-sql-server-profiler"></a>Avviare SQL Server Profiler  
  
1.  Nel computer remoto avviare SQL Server Profiler. Connettersi all'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , quindi fare clic su **Esegui** per avviare la traccia usando gli eventi predefiniti.  
  
     Usare SQL Server Profiler per il monitoraggio degli eventi di elaborazione mentre si verificano.  
  
2.  Facoltativamente, è possibile impostare le proprietà della traccia per inviare la traccia a un file o a una tabella di un database.  
  
#### <a name="run-the-job"></a>Eseguire il processo  
  
1.  Nel computer usato per eseguire il processo, verificare che tramite il processo sia possibile eseguire il funzionamento di base. In Esplora oggetti in SQL Server Agent espandere **Processi**, fare clic con il pulsante destro del mouse sul processo appena creato, quindi scegliere **Inizia processo al passaggio**. Il processo viene avviato immediatamente. È possibile monitorare lo stato in SQL Server Profiler.  
  
2.  Come passaggio finale, modificare il processo da eseguire in base a una pianificazione definita, aggiungendo le notifiche o gli avvisi necessari per amministrare il processo. Potrebbe inoltre essere necessario ridefinire lo script di elaborazione oppure creare più passaggi del processo per elaborare in modo indipendente gli oggetti.  
  
## <a name="see-also"></a>Vedere anche  
 [Componenti SQL Server Agent](../../ssms/agent/sql-server-agent.md#Components)   
 [Pianificare le attività amministrative di SSAS con SQL Server Agent](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md)   
 [Elaborazione batch &#40;Analysis Services&#41;](batch-processing-analysis-services.md)   
 [Elaborazione di oggetti del modello multidimensionale](processing-a-multidimensional-model-analysis-services.md)   
 [Elaborazione di oggetti &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)  
  
  
