---
title: Creare un avviso del database di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- database performance [SQL Server], alerts
- alerts [SQL Server], creating
- thresholds [SQL Server]
- database alerts [SQL Server]
- tuning databases [SQL Server], alerts
- monitoring performance [SQL Server], alerts
- monitoring server performance [SQL Server], alerts
- database monitoring [SQL Server], alerts
- server performance [SQL Server], alerts
ms.assetid: 0511136a-1b6b-4095-aa45-39e77b67aba2
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 971f9519208f9af67d8d1d1af63737ed876bfff1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85787487"
---
# <a name="create-a-sql-server-database-alert"></a>Creare un avviso del database di SQL Server
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  È possibile utilizzare Monitoraggio di sistema per creare un avviso da generare quando viene raggiunto un valore soglia specificato per un contatore di Monitoraggio di sistema. In risposta all'avviso, Monitoraggio di sistema avvia un'applicazione, ad esempio un'applicazione personalizzata programmata per gestire la condizione dell'avviso. Ad esempio, è possibile creare un avviso che viene generato quando il numero di deadlock supera un determinato valore.  
  
 È inoltre possibile definire avvisi utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Per altre informazioni, vedere [Avvisi](../../ssms/agent/alerts.md).  
  
 Per altre informazioni sull'uso di Monitoraggio di sistema per impostare un avviso del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Impostazione di un avviso del database di SQL Server &#40;Windows&#41;](../../relational-databases/performance/set-up-a-sql-server-database-alert-windows.md).  
  
## <a name="see-also"></a>Vedere anche  
 [sp_add_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sys.sysperfinfo &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql.md)  
  
  
