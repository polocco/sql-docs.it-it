---
title: Eseguire simultaneamente istruzioni su più server
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- multiserver queries
- executing queries against multiple servers
- queries [SQL Server], multiserver
ms.assetid: 197760f3-0a06-43de-8162-69c27d3fbe56
author: markingmyname
ms.author: maghan
manager: jroth
ms.openlocfilehash: 55b77ddf4284dc4f06e8036d0ae1b0c86b3544f7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "75244636"
---
# <a name="execute-statements-against-multiple-servers-simultaneously-sql-server-management-studio"></a>Esecuzione simultanea di istruzioni su più server (SQL Server Management Studio)
  In questo argomento viene descritto come eseguire una query su più server contemporaneamente in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]creando un gruppo di server locali, o un server di gestione centrale e uno o più gruppi di server, e uno o più server registrati all'interno dei gruppi, quindi eseguendo la query sul gruppo completo. I risultati restituiti dalla query possono essere combinati in un singolo riquadro dei risultati oppure possono essere inclusi in riquadri dei risultati distinti. Il set di risultati può includere colonne aggiuntive per il nome del server e l'account di accesso utilizzati dalla query in ciascun server. I server di gestione centrale e i server subordinati possono essere registrati solo tramite l'autenticazione di Windows. I server inclusi nei gruppi di server locali possono essere registrati tramite l'autenticazione di Windows o l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  Prima di utilizzare le procedure seguenti, creare un server di gestione centrale e uno o più gruppi di server. Per altre informazioni, vedere [Creazione di un server di gestione centrale e di un gruppo di server &#40;SQL Server Management Studio&#41;](create-a-central-management-server-and-server-group.md).  
  
 **Contenuto dell'articolo**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Per eseguire istruzioni su più server tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="security"></a><a name="Security"></a> Sicurezza  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorizzazioni  
 Poiché le connessioni gestite da un server di gestione centrale vengono eseguite nel contesto dell'utente, l'utilizzo dell'autenticazione di Windows comporta la possibile variazione delle autorizzazioni effettive per i server registrati. L'utente, ad esempio, potrebbe essere un membro del ruolo predefinito del server sysadmin nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] A, ma disporre di autorizzazioni limitate per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] B.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-execute-statements-against-multiple-configuration-targets-simultaneously"></a>Per eseguire istruzioni su più destinazioni di configurazione simultaneamente  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]scegliere **Server registrati** dal menu **Visualizza**.  
  
2.  Espandere un server di gestione centrale, fare clic con il pulsante destro del mouse su un gruppo di server, scegliere **Connetti**, quindi fare clic su **Nuova query**.  
  
3.  Nell'editor di query digitare ed eseguire un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] , ad esempio la seguente:  
  
    ```  
    USE master  
    GO  
    SELECT * FROM sysdatabases;  
    GO  
    ```  
  
     Per impostazione predefinita, il riquadro dei risultati combinerà i risultati della query restituiti da tutti i server inclusi nel gruppo di server.  
  
#### <a name="to-change-the-multiserver-results-options"></a>Per modificare le opzioni dei risultati multiserver  
  
1.  In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Espandere **Risultati query**, espandere **SQL Server**, quindi fare clic su **Risultati multiserver**.  
  
3.  Nella pagina **Risultati multiserver** specificare le impostazioni desiderate per le opzioni, quindi scegliere **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrare più server tramite server di gestione centrale](../../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
