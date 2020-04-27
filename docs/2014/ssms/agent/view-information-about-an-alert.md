---
title: Visualizzare informazioni su un avviso | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, alerts
- viewing alerts
- alerts [SQL Server], viewing
- displaying alerts
- status information [SQL Server], alerts
ms.assetid: a0e3a8c4-e3c2-42a5-b2f8-aa06061d3fa6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c5567abc0893bd183c2468f82278a014e2005113
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "68211298"
---
# <a name="view-information-about-an-alert"></a>Visualizzare informazioni su un avviso
  In questo argomento viene descritto come visualizzare le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] informazioni sugli avvisi [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] di Agent [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] in [!INCLUDE[tsql](../../includes/tsql-md.md)]tramite o.  
  
 **Contenuto dell'articolo**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Per visualizzare informazioni su un avviso utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="security"></a><a name="Security"></a> Sicurezza  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorizzazioni  
 Per impostazione predefinita, i membri del ruolo predefinito del server **sysadmin** possono visualizzare le informazioni su un avviso. Gli altri utenti devono appartenere al ruolo predefinito del database **SQLAgentOperatorRole** nel database **msdb** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-view-information-about-an-alert"></a>Per visualizzare informazioni su un avviso  
  
1.  In **Esplora oggetti** fare clic sul segno più per espandere il server in cui si desidera visualizzare le informazioni su un avviso.  
  
2.  Fare clic sul segno più per espandere **SQL Server Agent**.  
  
3.  Fare clic sul segno più per espandere la cartella **Avvisi** .  
  
4.  Fare clic con il pulsante destro del mouse sull'avviso con le informazioni da visualizzare e selezionare **Proprietà**.  
  
     Per altre informazioni sulle opzioni disponibili contenute nella finestra di dialogo dell'interfaccia utente nella finestra di dialogo _Proprietà dell'avviso_**nome_avviso** , vedere:  
  
    -   [Proprietà avviso-nuovo avviso &#40;pagina generale&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
    -   [Proprietà avviso-pagina nuova risposta avviso &#40;&#41;](alert-properties-new-alert-response-page.md)  
  
    -   [Proprietà avviso: nuova pagina Opzioni &#40;avvisi&#41;](alert-properties-new-alert-options-page.md)  
  
    -   [Proprietà avviso &#40;pagina Cronologia&#41;](alert-properties-history-page.md)  
  
5.  Al termine, fare clic su **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-view-information-about-an-alert"></a>Per visualizzare informazioni su un avviso  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    -- reports information about the Demo: Sev. 25 Errors alert  
    -- This example assumes that the 'Demo: Sev. 25 Errors' alert exists.  
    USE msdb ;  
    GO  
  
    EXEC sp_help_alert @alert_name = 'Demo: Sev. 25 Errors'  
    GO  
    ```  
  
 Per ulteriori informazioni, vedere [sp_help_alert &#40;&#41;Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-help-alert-transact-sql).  
  
  
