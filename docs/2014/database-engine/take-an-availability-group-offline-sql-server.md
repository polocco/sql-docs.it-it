---
title: ALTER AVAILABILITY GROUP offline
description: Procedura per impostare il gruppo di disponibilità Always On offline
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], take offline
ms.assetid: 50f5aad8-0dff-45ef-8350-f9596d3db898
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 87dff347bd0aee1211093d9e3406a24670a80e7f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "75228165"
---
# <a name="take-an-availability-group-offline-sql-server"></a>Portare un gruppo di disponibilità offline (SQL Server)
  In questo argomento viene descritto come portare un gruppo di disponibilità AlwaysOn da uno stato ONLINE a uno stato OFFLINE mediante [!INCLUDE[tsql](../includes/tsql-md.md)] in [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] e versioni successive. Non si verifica alcuna perdita di dati per i database con commit sincrono, poiché se una replica con commit sincrono non è sincronizzata, l'operazione OFFLINE genera un errore e mantiene il gruppo di disponibilità nello stato ONLINE. Mantenendo il gruppo di disponibilità online, verrà evitata una possibile perdita di dati nei database non sincronizzati con commit sincrono. Dopo aver portato un gruppo di disponibilità offline, i relativi database non saranno più disponibili per i client e non sarà possibile riportare nuovamente online il gruppo di disponibilità. Pertanto, portare un gruppo di disponibilità offline esclusivamente per eseguire la migrazione delle risorse del gruppo di disponibilità da un cluster WSFC a un altro.  
  
 Durante la migrazione tra cluster di [!INCLUDE[ssHADR](../includes/sshadr-md.md)], se si connettono applicazioni direttamente alla replica primaria di un gruppo di disponibilità, il gruppo di disponibilità dovrà essere portato offline. La migrazione tra cluster di [!INCLUDE[ssHADR](../includes/sshadr-md.md)] supporta l'aggiornamento del sistema operativo con tempi di inattività minimi dei gruppi di disponibilità. Lo scenario tipico prevede l'utilizzo della migrazione tra cluster di [!INCLUDE[ssHADR](../includes/sshadr-md.md)] per l'aggiornamento del sistema operativo a [!INCLUDE[win8](../includes/win8-md.md)] o [!INCLUDE[win8srv](../includes/win8srv-md.md)]. Per ulteriori informazioni, vedere [Migrazione tra cluster di gruppi di disponibilità AlwaysOn per l'aggiornamento del sistema operativo](https://msdn.microsoft.com/library/jj873730.aspx).  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Prima di iniziare  
  
> [!CAUTION]  
>  Utilizzare l'opzione OFFLINE solo per una migrazione tra cluster di risorse di gruppi di disponibilità.  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Prerequisiti  
  
-   L'istanza del server in cui si immette il comando OFFLINE deve eseguire [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] o versioni successive (Enterprise Edition o versioni successive).  
  
-   Il gruppo di disponibilità deve essere attualmente online.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Indicazioni  
 Prima di portare il gruppo di disponibilità offline, eliminare eventuali listener del gruppo. Per altre informazioni, vedere [Rimuovere un listener del gruppo di disponibilità &#40;SQL Server&#41;](availability-groups/windows/remove-an-availability-group-listener-sql-server.md).  
  
###  <a name="security"></a><a name="Security"></a> Sicurezza  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorizzazioni  
 È necessaria l'autorizzazione ALTER AVAILABILITY GROUP nel gruppo di disponibilità, l'autorizzazione CONTROL AVAILABILITY GROUP, l'autorizzazione ALTER ANY AVAILABILITY GROUP o l'autorizzazione CONTROL SERVER.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Uso di Transact-SQL  
 **Per portare un gruppo di disponibilità offline**  
  
1.  Connettersi a un'istanza del server in cui viene ospitata una replica di disponibilità del gruppo di disponibilità. Può trattarsi della replica primaria o di una replica secondaria.  
  
2.  Utilizzare l'istruzione [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) , come indicato di seguito:  
  
     ALTER AVAILABILITY GROUP *nome_gruppo* OFFLINE  
  
     dove *nome_gruppo* è il nome del gruppo di disponibilità.  
  
### <a name="example"></a>Esempio  
 Nell'esempio seguente il gruppo di disponibilità `AccountsAG` viene portato offline.  
  
```sql
ALTER AVAILABILITY GROUP AccountsAG OFFLINE;  
```  
  
##  <a name="follow-up-after-the-availability-group-goes-offline"></a><a name="FollowUp"></a>Completamento: quando il gruppo di disponibilità passa alla modalità offline  
  
-   **Registrazione dell'operazione ONLINE:**  l'identità del nodo WSFC in cui è stata avviata l'operazione OFFLINE è archiviata nel registro del cluster WSFC e in SQL ERRORLOG.  
  
-   **Se prima di portare il gruppo offline non è stato eliminato il listener del gruppo di disponibilità:**  se si esegue la migrazione del gruppo di disponibilità a un altro cluster WSFC, eliminare il nome di rete virtuale (VNN) e l'IP virtuale (VIP) del listener. È possibile eliminarli tramite la console Gestione cluster di failover, il cmdlet [Remove-ClusterResource](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx) di PowerShell o [cluster.exe](https://technet.microsoft.com/library/ee461015\(WS.10\).aspx). Cluster.exe è deprecato in Windows 8.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Attività correlate  
  
-   [Rimuovere un listener del gruppo di disponibilità &#40;SQL Server&#41;](availability-groups/windows/remove-an-availability-group-listener-sql-server.md)  
  
-   [Modificare il contesto del cluster HADR dell'istanza del server &#40;SQL Server&#41;](availability-groups/windows/change-the-hadr-cluster-context-of-server-instance-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Contenuto correlato  
  
-   [Articoli tecnici su SQL Server 2012](https://msdn.microsoft.com/library/bb418445\(SQL.10\).aspx)  
  
-   [Blog del team di SQL Server AlwaysOn: Blog del team ufficiale di SQL Server AlwaysOn](https://blogs.msdn.com/b/sqlalwayson/)  
  
## <a name="see-also"></a>Vedere anche  
 [Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](availability-groups/windows/always-on-availability-groups-sql-server.md)  
