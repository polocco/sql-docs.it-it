---
title: Modificare il contesto del cluster HADR dell'istanza del server (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- Availability replicas [SQL Server], change WSFC cluster context
ms.assetid: ecd99f91-b9a2-4737-994e-507065a12f80
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: de783ffdb5480a9cdebec2380f81e50a9cba11ec
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62815404"
---
# <a name="change-the-hadr-cluster-context-of-server-instance-sql-server"></a>Modificare il contesto del cluster HADR dell'istanza del server (SQL Server)
  In questo argomento viene descritto come cambiare il contesto del cluster HADR di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizzando [!INCLUDE[tsql](../../../includes/tsql-md.md)] in [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] e versioni successive. Il *contesto del cluster HADR* determina il cluster WSFC (Windows Server Failover Clustering) che gestisce i metadati per le repliche di disponibilità ospitate dall'istanza del server.  
  
 Cambiare il contesto del cluster HADR solo durante una migrazione tra cluster di [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] a un'istanza di [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] in un nuovo cluster WSFC. La migrazione tra cluster di [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] supporta l'aggiornamento del sistema operativo a [!INCLUDE[win8](../../../includes/win8-md.md)] o a [!INCLUDE[win8srv](../../../includes/win8srv-md.md)] con tempi di inattività minimi dei gruppi di disponibilità. Per ulteriori informazioni, vedere [Migrazione tra cluster di gruppi di disponibilità AlwaysOn per l'aggiornamento del sistema operativo](https://msdn.microsoft.com/library/jj873730.aspx).  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Prima di iniziare  
  
> [!CAUTION]  
>  Cambiare il contesto del cluster HADR solo durante la migrazione tra cluster di distribuzioni [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] .  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   È possibile cambiare il contesto del cluster HADR solo dal cluster WSFC locale a un cluster remoto e quindi nuovamente dal cluster remoto al cluster locale. Non è possibile cambiare il contesto del cluster HADR da un cluster remoto a un altro cluster remoto.  
  
-   È possibile cambiare il contesto del cluster HADR in un cluster remoto solo se l'istanza di SQL Server non ospita alcuna replica di disponibilità.  
  
-   Il contesto di un cluster HADR remoto può essere nuovamente cambiato nel cluster locale in qualsiasi momento, a meno che l'istanza del server non ospiti una replica di disponibilità.  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Prerequisiti  
  
-   L'istanza del server in cui si cambia il contesto del cluster HADR deve eseguire [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] o versioni successive (Enterprise Edition o versioni successive).  
  
-   L'istanza del server deve essere abilitata per AlwaysOn. Per altre informazioni, vedere [Abilitare e disabilitare la funzionalità Gruppi di disponibilità Always On &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md).  
  
-   Affinché possa essere cambiata dal contesto del cluster locale in un cluster remoto, un'istanza del server non può ospitare repliche di disponibilità. La vista del catalogo [sys.availability_replicas](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql) non deve restituire righe.  
  
     Se nell'istanza del server sono presenti repliche di disponibilità, prima di poter cambiare il contesto del cluster HADR è necessario eseguire una delle operazioni indicate di seguito:  
  
    |Ruolo della replica|Azione|Collegamento|  
    |------------------|------------|----------|  
    |Primaria|Gruppo di disponibilità offline.|[Portare un gruppo di disponibilità offline &#40;SQL Server&#41;](../../take-an-availability-group-offline-sql-server.md)|  
    |Secondari|Rimozione della replica dal gruppo di disponibilità|[Rimuovere una replica secondaria da un gruppo di disponibilità &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)|  
  
-   Prima di poter passare da un cluster remoto al cluster locale, tutte le repliche con commit sincrono devono essere di tipo SYNCHRONIZED.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Indicazioni  
  
-   È consigliabile specificare il nome di dominio completo. Ciò è dovuto al fatto che, per individuare l'indirizzo IP di destinazione di un nome breve, ALTER SERVER CONFIGURATION utilizza la risoluzione DNS. In alcuni casi, a seconda dell'ordine di ricerca DNS, l'utilizzo di un nome breve potrebbe creare confusione. Si consideri, ad esempio, il comando indicato di seguito, eseguito in un nodo nel dominio `abc` (`node1.abc.com`). Il cluster di destinazione desiderato è il cluster `CLUS01` nel dominio `xyz` (`clus01.xyz.com`). Tuttavia, gli host di dominio locali ospitano anche un cluster denominato `CLUS01` (`clus01.abc.com`).  
  
     Se è stato specificato il nome breve del cluster di destinazione, `CLUS01`, la risoluzione dei nomi DNS potrebbe restituire l'indirizzo IP del cluster errato, `clus01.abc.com`. Per evitare di creare confusione, specificare il nome completo del cluster di destinazione, come nel seguente esempio:  
  
    ```  
    ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = 'clus01.xyz.com'  
    ```  
  
###  <a name="security"></a><a name="Security"></a> Sicurezza  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorizzazioni  
  
-   **Accesso SQL Server**  
  
     È richiesta l'autorizzazione CONTROL SERVER.  
  
-   **Account del servizio SQL Server**  
  
     L'account di servizio di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dell'istanza del server deve disporre degli elementi seguenti:  
  
    -   Autorizzazione per aprire il cluster WSFC di destinazione.  
  
    -   Accesso remoto a WSFC in lettura e scrittura.  
  
 
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Uso di Transact-SQL  
 **Per modificare il contesto del cluster WSFC di una replica di disponibilità**  
  
1.  Connettersi all'istanza del server che ospita la replica primaria o una replica secondaria del gruppo di disponibilità.  
  
2.  Usare la clausola SET HADR CLUSTER CONTEXT dell'istruzione [ALTER SERVER CONFIGURATION](/sql/t-sql/statements/alter-server-configuration-transact-sql) , come segue:  
  
     ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT **=** { **'*`windows_cluster`*'** | LOCALE  
  
     dove  
  
     *windows_cluster*  
     Nome dell'oggetto cluster (CON) di un cluster WSFC. È possibile specificare il nome breve o il nome di dominio completo. È consigliabile specificare il nome di dominio completo. Per ulteriori informazioni, vedere [raccomandazioni](#Recommendations), più indietro in questo argomento.  
  
     LOCAL  
     Cluster WSFC locale.  
  
### <a name="examples"></a>Esempi  
 Nell'esempio seguente il contesto del cluster HADR viene cambiato in un cluster diverso. Per identificare il cluster WSFC di destinazione, `clus01`, nell'esempio viene specificato il nome completo dell'oggetto cluster, `clus01.xyz.com`.  
  
```  
ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = 'clus01.xyz.com';  
```  
  
 Nell'esempio seguente il contesto del cluster HADR viene cambiato in un cluster WSFC locale.  
  
```  
ALTER SERVER CONFIGURATION SET HADR CLUSTER CONTEXT = LOCAL;  
```  
  

  
##  <a name="follow-up-after-switching-the-cluster-context-of-an-availability-replica"></a><a name="FollowUp"></a> Completamento: dopo aver cambiato il contesto del cluster di una replica di disponibilità  
 Il nuovo contesto del cluster HADR diviene effettivo immediatamente e non richiede il riavvio dell'istanza del server. L'impostazione del contesto del cluster HADR è di tipo persistente a livello di istanza e rimane invariata in caso di riavvio dell'istanza del server.  
  
 Confermare il nuovo contesto del cluster HADR eseguendo una query sulla vista a gestione dinamica (DMV) [sys.dm_hadr_cluster](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-transact-sql) , come segue:  
  
```  
SELECT cluster_name FROM sys.dm_hadr_cluster  
```  
  
 Questa query deve restituire il nome del cluster in cui impostare il contesto del cluster HADR.  
  
 Se il contesto del cluster HADR viene cambiato in un nuovo cluster:  
  
-   I metadati vengono puliti per qualsiasi replica di disponibilità ospitata dall'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Tutti i database appartenenti a una replica di disponibilità si trovano ora in uno stato RESTORING.  
  
 
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Attività correlate  
  
-   [Rimuovere un listener del gruppo di disponibilità &#40;SQL Server&#41;](remove-an-availability-group-listener-sql-server.md)  
  
-   [Portare un gruppo di disponibilità offline &#40;SQL Server&#41;](../../take-an-availability-group-offline-sql-server.md)  
  
-   [Aggiungere una replica secondaria a un gruppo di disponibilità &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Rimuovere una replica secondaria da un gruppo di disponibilità &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [Creare o configurare un listener del gruppo di disponibilità &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Creare un join di un database secondario a un gruppo di disponibilità &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
 
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Contenuto correlato  
  
-   [Articoli tecnici su SQL Server 2012](https://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)  
  
-   [Blog del team di SQL Server AlwaysOn: Blog del team ufficiale di SQL Server AlwaysOn](https://blogs.msdn.com/b/sqlalwayson/)  
  
  
  
## <a name="see-also"></a>Vedi anche  
 [Gruppi di disponibilità AlwaysOn (SQL Server)](always-on-availability-groups-sql-server.md) [Windows Server Failover Clustering &#40;WSFC&#41; con SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)   
 [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-server-configuration-transact-sql)  
  
  
