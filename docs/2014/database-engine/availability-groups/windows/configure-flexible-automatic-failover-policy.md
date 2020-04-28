---
title: Configurare i criteri di failover flessibili per controllare le condizioni per il failover automatico (gruppi di disponibilità Always On) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], flexible failover policy
- Availability Groups [SQL Server], failover
- failover [SQL Server], AlwaysOn Availability Groups
ms.assetid: 1ed564b4-9835-4245-ae35-9ba67419a4ce
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 452d3ac4dae2164fa0fa172528ae398ea91fed31
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "72797747"
---
# <a name="configure-the-flexible-failover-policy-to-control-conditions-for-automatic-failover-always-on-availability-groups"></a>Configurare i criteri di failover flessibili per controllare le condizioni per il failover automatico (Gruppi di disponibilità AlwaysOn)
  In questo argomento verrà descritto come configurare i criteri di failover flessibili per un gruppo di disponibilità AlwaysOn tramite [!INCLUDE[tsql](../../../includes/tsql-md.md)] o PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Con i criteri di failover flessibili viene garantito un controllo granulare delle condizioni che causano un failover automatico per un gruppo di disponibilità. Modificando le condizioni di errore che attivano un failover automatico e la frequenza di controlli di integrità, è possibile aumentare o diminuire la probabilità di un failover automatico per supportare il Contratto di servizio per la disponibilità elevata.  
  
  
  
    > [!NOTE]  
    >  The flexible failover policy of an availability group cannot be configured by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="limitations-on-automatic-failovers"></a><a name="Limitations"></a>Limitazioni sui failover automatici  
  
-   Affinché si verifichi un failover automatico, la replica primaria corrente e una replica secondaria devono essere configurate per la modalità di disponibilità con commit sincrono e failover automatico e la replica secondaria deve essere sincronizzata con quella primaria.  
  
-   Se un gruppo di disponibilità supera la relativa soglia di errore WSFC, non verrà effettuato il tentativo di failover automatico per il gruppo di disponibilità da parte del cluster WSFC. Inoltre, il gruppo di risorse WSFC del gruppo di disponibilità rimarrà in uno stato di errore finché l'amministratore del cluster non porterà manualmente online il gruppo di risorse con errori o l'amministratore del database non eseguirà un failover manuale del gruppo di disponibilità. La *soglia di errore WSFC* è definita come il numero massimo di errori supportati per il gruppo di disponibilità durante un determinato periodo di tempo. Il periodo di tempo predefinito è sei ore e il valore predefinito per il numero massimo di errori durante questo periodo è *n*-1, dove *n* è il numero di nodi WSFC. Per modificare i valori soglia dell'errore per un determinato gruppo di disponibilità, utilizzare la console di Gestione cluster di failover WSFC.  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Prerequisiti  
  
-   È necessario essere connessi all'istanza del server che ospita la replica primaria.  
  
###  <a name="security"></a><a name="Security"></a> Sicurezza  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorizzazioni  
  
|Attività|Autorizzazioni|  
|----------|-----------------|  
|Per configurare i criteri di failover flessibili per un nuovo gruppo di disponibilità|Sono necessarie l'appartenenza al ruolo predefinito del server **sysadmin** e l'autorizzazione server CREATE AVAILABILITY GROUP oppure l'autorizzazione ALTER ANY AVAILABILITY GROUP o CONTROL SERVER.|  
|Per modificare i criteri di un gruppo di disponibilità esistente|È necessaria l'autorizzazione ALTER AVAILABILITY GROUP nel gruppo di disponibilità, l'autorizzazione CONTROL AVAILABILITY GROUP, l'autorizzazione ALTER ANY AVAILABILITY GROUP o l'autorizzazione CONTROL SERVER.|  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Uso di Transact-SQL  
 **Per configurare i criteri di failover flessibili**  
  
1.  Connettersi all'istanza del server che ospita la replica primaria.  
  
2.  Per un nuovo gruppo di disponibilità, usare l'istruzione [create Availability Group](/sql/t-sql/statements/create-availability-group-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] . Se si modifica un gruppo di disponibilità esistente, utilizzare l'istruzione [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] .  
  
    -   Per impostare il livello di condizione del failover, usare l'opzione FAILURE_CONDITION_LEVEL = *n* dove *n* è un numero intero da 1 a 5.  
  
         Ad esempio, l'istruzione [!INCLUDE[tsql](../../../includes/tsql-md.md)] seguente modifica il livello di condizione di errore di un gruppo di disponibilità esistente, `AG1`, nel livello uno:  
  
        ```sql
        ALTER AVAILABILITY GROUP AG1 SET (FAILURE_CONDITION_LEVEL = 1);  
        ```  
  
         La relazione di questi valori interi con i livelli di condizione di errore è la seguente:  
  
        |[!INCLUDE[tsql](../../../includes/tsql-md.md)] Valore|Level|Il failover automatico viene avviato...|  
        |------------------------------|-----------|-------------------------------------------|  
        |1|Uno|In caso di server inaccessibile. Il servizio SQL Server viene arrestato a causa di un failover o un riavvio.|  
        |2|Due|In caso di mancata risposta del server. Viene soddisfatta qualsiasi condizione di valore inferiore, il servizio SQL Server è connesso al cluster e viene superata la soglia di Timeout controllo integrità o la replica primaria corrente si trova in uno stato di errore.|  
        |3|Tre|In caso di errori critici del server. Viene soddisfatta qualsiasi condizione di valore inferiore o si verifica un errore critico interno del server.<br /><br /> Si tratta del livello predefinito.|  
        |4|Quattro|In caso di errori con gravità moderata del server. Viene soddisfatta qualsiasi condizione di valore inferiore o si verifica un errore non critico del server.|  
        |5|Cinque|In qualsiasi condizione di errore qualificata. Viene soddisfatta qualsiasi condizione di valore inferiore o si verifica una condizione di errore appropriata.|  
  
         Per altre informazioni sui livelli di condizione del failover, vedere [Criteri di failover flessibili per failover automatico di un gruppo di disponibilità &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md).  
  
    -   Per configurare la soglia di Timeout controllo integrità, usare l'opzione HEALTH_CHECK_TIMEOUT = *n* dove *n* è un numero intero compreso tra 15000 millisecondi (15 secondi) e 4294967295 millisecondi. Il valore predefinito è 30000 millisecondi (30 secondi)  
  
         Ad esempio, l'istruzione [!INCLUDE[tsql](../../../includes/tsql-md.md)] seguente modificata la soglia di Timeout controllo integrità di un gruppo di disponibilità esistente, `AG1`, in 60.000 millisecondi (un minuto).  
  
        ```sql
        ALTER AVAILABILITY GROUP AG1 SET (HEALTH_CHECK_TIMEOUT = 60000);  
        ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> Utilizzo di PowerShell  

### <a name="to-configure-the-flexible-failover-policy"></a>Per configurare i criteri di failover flessibili * *  
  
1.  Impostare il valore predefinito (`cd`) sull'istanza del server che ospita la replica primaria.  
  
2.  Quando si aggiunge una replica di disponibilità a un gruppo di disponibilità, utilizzare il cmdlet `New-SqlAvailabilityGroup`. Quando si modifica una replica di disponibilità esistente, utilizzare il cmdlet `Set-SqlAvailabilityGroup`.  
  
    -   Per impostare il livello di condizione del failover, `FailureConditionLevel`usare il parametro *Level* , dove *Level* è uno dei valori seguenti:  
  
        |valore|Level|Il failover automatico viene avviato...|  
        |-----------|-----------|-------------------------------------------|  
        |`OnServerDown`|Uno|In caso di server inaccessibile. Il servizio SQL Server viene arrestato a causa di un failover o un riavvio.|  
        |`OnServerUnresponsive`|Due|In caso di mancata risposta del server. Viene soddisfatta qualsiasi condizione di valore inferiore, il servizio SQL Server è connesso al cluster e viene superata la soglia di Timeout controllo integrità o la replica primaria corrente si trova in uno stato di errore.|  
        |`OnCriticalServerError`|Tre|In caso di errori critici del server. Viene soddisfatta qualsiasi condizione di valore inferiore o si verifica un errore critico interno del server.<br /><br /> Si tratta del livello predefinito.|  
        |`OnModerateServerError`|Quattro|In caso di errori con gravità moderata del server. Viene soddisfatta qualsiasi condizione di valore inferiore o si verifica un errore non critico del server.|  
        |`OnAnyQualifiedFailureConditions`|Cinque|In qualsiasi condizione di errore qualificata. Viene soddisfatta qualsiasi condizione di valore inferiore o si verifica una condizione di errore appropriata.|  
  
         Per altre informazioni sui livelli di condizione del failover, vedere [Criteri di failover flessibili per failover automatico di un gruppo di disponibilità &#40;SQL Server&#41;](flexible-automatic-failover-policy-availability-group.md).  
  
         Ad esempio, il comando seguente modifica il livello di condizione di errore di un gruppo di disponibilità esistente, `AG1`, nel livello uno:  
  
        ```powershell
        Set-SqlAvailabilityGroup `
         -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg `
         -FailureConditionLevel OnServerDown  
        ```  
  
    -   Per impostare la soglia di timeout controllo integrità, usare `HealthCheckTimeout`il parametro *n* , dove *n* è un numero intero compreso tra 15000 millisecondi (15 secondi) e 4294967295 millisecondi. Il valore predefinito è 30000 millisecondi (30 secondi).  
  
         Ad esempio, il comando seguente modifica la soglia di Timeout controllo integrità di un gruppo di disponibilità esistente, `AG1`, in 120.000 millisecondi (due minuti).  
  
        ```powershell
        Set-SqlAvailabilityGroup `
         -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAG `
         -HealthCheckTimeout 120000  
        ```  
  
> [!NOTE]  
>  Per visualizzare la sintassi di un cmdlet, utilizzare il cmdlet `Get-Help` nell'ambiente [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Per altre informazioni, vedere [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).  
  
 **Per impostare e utilizzare il provider PowerShell per SQL Server**  
  
-   [Provider PowerShell per SQL Server](../../../powershell/sql-server-powershell-provider.md)  
  
-   [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Modalità di disponibilità (Gruppi di disponibilità AlwaysOn)](availability-modes-always-on-availability-groups.md)   
 [Failover e modalità di failover &#40;Gruppi di disponibilità AlwaysOn&#41;](failover-and-failover-modes-always-on-availability-groups.md)   
 [Windows Server failover clustering &#40;&#41; WSFC con SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)   
 [Criteri di failover per le istanze del cluster di failover](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md)   
 [sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql)  
