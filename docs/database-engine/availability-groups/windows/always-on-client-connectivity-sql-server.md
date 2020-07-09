---
title: Supporto della connettività di driver e client per i gruppi di disponibilità
description: 'Questo argomento illustra alcune considerazioni relative alla connettività client a gruppi di disponibilità Always On, tra cui i prerequisiti e le restrizioni e alcune indicazioni per la configurazione e la definizione delle impostazioni client. '
ms.custom: seodec18
ms.date: 04/26/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
- Availability Groups [SQL Server], prerequisites and restrictions
- Availability Groups [SQL Server], client connectivity
ms.assetid: b456448d-1757-48c8-8bbb-2d1c2d6d61e9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bb97e94e55f270331ff99909b5ec7dca6f8683e3
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85901032"
---
# <a name="driver-and-client-connectivity-support-for-availability-groups"></a>Supporto della connettività di driver e client per i gruppi di disponibilità
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

  Questo argomento illustra alcune considerazioni relative alla connettività client a gruppi di disponibilità Always On, tra cui i prerequisiti e le restrizioni e alcune indicazioni per la configurazione e la definizione delle impostazioni client.  
  
 
##  <a name="client-connectivity-support"></a><a name="ClientConnSupport"></a> Supporto della connettività client  
 Nella sezione riportata di seguito vengono fornite informazioni sul supporto di [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] per la connettività client.  
  
 **Supporto driver**  
  
 Nella tabella seguente viene riepilogato il supporto di driver per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]:  
  
|Driver|Failover su più subnet|Finalità dell'applicazione|Routing di sola lettura|Failover su più subnet: failover dell'endpoint su una sola subnet più rapido|Failover su più subnet: risoluzione dell'istanza denominata per le istanze cluster di SQL|  
|------------|----------------------------|------------------------|------------------------|--------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|SQL Native Client 11.0 ODBC|Sì|Sì|Sì|Sì|Sì|  
|SQL Native Client 11.0 OLEDB|No|Sì|Sì|No|No|  
|ADO.NET con .NET Framework 4.0 con patch di connettività*|Sì|Sì|Sì|Sì|Sì|  
|ADO.NET con.NET Framework 3.5 SP1 con patch di connettività**|Sì|Sì|Sì|Sì|Sì|  
|Microsoft JDBC Driver 4.0 per SQL Server|Sì|Sì|Sì|Sì|Sì| 
|Driver Microsoft OLE DB per SQL Server|Sì|Sì|Sì|Sì|Sì| 
  
 *Scaricare la patch di connettività per ADO .NET con .NET Framework 4.0: [https://support.microsoft.com/kb/2600211](https://support.microsoft.com/kb/2600211).  
  
 **Scaricare la patch di connettività per ADO .NET con .NET Framework 3.5 SP1: [https://support.microsoft.com/kb/2654347](https://support.microsoft.com/kb/2654347).  
 
 *Scaricare il nuovo driver Microsoft OLE DB per SQL Server: [https://www.microsoft.com/download/details.aspx?id=56730](https://www.microsoft.com/download/details.aspx?id=56730).  

> [!IMPORTANT]  
>  Per connettersi a un listener del gruppo di disponibilità, un client deve utilizzare una stringa di connessione TCP.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Attività correlate  
  
-   [Creazione e configurazione di gruppi di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md)  
  
-   [Creare o configurare un listener del gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Clustering di failover e gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [Prerequisiti, restrizioni e raccomandazioni per i gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)   
 [Listener del gruppo di disponibilità, connettività client e failover dell'applicazione &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md)   
 [Informazioni sull'accesso alla connessione client per le repliche di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/about-client-connection-access-to-availability-replicas-sql-server.md)   
 [Microsoft SQL Server Always On Solutions Guide for High Availability and Disaster Recovery (Guida alle soluzioni AlwaysOn di Microsoft SQL Server per la disponibilità elevata e il ripristino di emergenza)](https://go.microsoft.com/fwlink/?LinkId=227600)   
 [Blog del team di SQL Server AlwaysOn: blog ufficiale del team di SQL Server AlwaysOn](https://blogs.msdn.microsoft.com/sqlalwayson/)   
 [Si verifica un ritardo prolungato quando si riconnette una connessione IPsec da un computer in cui è in esecuzione Windows Server 2003, Windows Vista, Windows Server 2008, Windows 7 o Windows Server 2008 R2](https://support.microsoft.com/kb/980915)   
 [Il servizio cluster impiega circa 30 secondi per il failover su indirizzi IP IPv6 in Windows Server 2008 R2](https://support.microsoft.com/kb/2578113)   
 [Failover lento se non esiste alcun router tra il cluster e un server applicazioni](https://support.microsoft.com/kb/2582281)  
  
  
