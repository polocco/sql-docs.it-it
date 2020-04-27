---
title: Monitorare l'uso del disco | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- database monitoring [SQL Server], disk usage
- disks [SQL Server]
- monitoring performance [SQL Server], disk usage
- server performance [SQL Server], disk usage
- monitoring [SQL Server], disk activity
- excess paging [SQL Server]
- tuning databases [SQL Server], disk usage
- I/O [SQL Server], monitoring
- disks [SQL Server], monitoring activity
- isolating disk activity [SQL Server]
- database performance [SQL Server], disk usage
- monitoring server performance [SQL Server], disk usage
ms.assetid: 1525449c-ea7d-4222-b294-1ba1fe99c9ac
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 81f0169f8235d94ef2d12753c3164462fcbad44c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "63032263"
---
# <a name="monitor-disk-usage"></a>Monitoraggio dell'utilizzo del disco
  In Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono utilizzate le chiamate di input/output (I/O) del sistema operativo Microsoft Windows per eseguire operazioni di lettura e scrittura sul disco. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gestisce i tempi e le modalità di esecuzione delle operazioni di I/O, ma è il sistema operativo Windows a eseguire le operazioni di I/O sottostanti. Il sottosistema di I/O include il bus di sistema, le schede dei controller dei dischi, i dischi, le unità a nastro, l'unità CD-ROM e numerosi altri dispositivi di I/O. L'attività di I/O su disco rappresenta frequentemente la causa di colli di bottiglia in un sistema.  
  
 Il monitoraggio dell'attività del disco si concentra su due aree:  
  
-   Monitoraggio dell'I/O su disco e rilevamento del paging eccessivo  
  
-   Isolamento dell'attività del disco creata da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
 Per ulteriori informazioni, vedere la pagina relativa al [monitoraggio dell'utilizzo del disco](https://social.technet.microsoft.com/wiki/contents/articles/monitoring-disk-usage.aspx)  
  
  
