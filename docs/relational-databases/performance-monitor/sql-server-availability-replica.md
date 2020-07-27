---
title: Oggetto Availability Replica di SQL Server | Microsoft Docs
description: Informazioni sull'oggetto prestazione SQLServer:Availability Replica, che contiene contatori delle prestazioni sulle repliche di disponibilità nei gruppi di disponibilità Always On.
ms.custom: ''
ms.date: 08/25/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- performance counters [SQL Server], AlwaysOn Availability Groups
- SQLServer:Availability Replica
- Availability Groups [SQL Server], performance counters
ms.assetid: e402f996-c1fb-484a-b804-45c49972f2e0
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: f9bec13f0da210b9b6471a955fc619f7b9aec23a
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2020
ms.locfileid: "86458163"
---
# <a name="sql-server-availability-replica"></a>SQL Server, replica di disponibilità
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  L'oggetto prestazione **SQLServer:Availability Replica** contiene contatori delle prestazioni che forniscono informazioni sulle repliche di disponibilità nei gruppi di disponibilità AlwaysOn di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Tutti i contatori delle prestazioni delle repliche di disponibilità si applicano sia alla replica primaria che alle repliche secondarie con i contatori di invio/ricezione che riflettono la replica locale. In molti casi, la replica primaria invia la maggior parte dei dati e le repliche secondarie ricevono i dati. Tuttavia, le repliche secondarie inviano gli ACK e altro traffico di background alle repliche primarie. Si noti che in alcuni contatori di una replica di disponibilità viene mostrato un valore zero, a seconda del ruolo corrente della replica locale, ovvero primario o secondario.  
  
|Nome contatore|Descrizione|  
|------------------|-----------------|  
|**Byte ricevuti dalla replica/sec**|Numero di byte ricevuti dalla replica di disponibilità al secondo. I ping e gli aggiornamenti di stato comporteranno traffico di rete anche nei database senza aggiornamenti dell'utente.|  
|**Byte inviati alla replica/sec**|Numero di byte inviati alla replica di disponibilità remota al secondo. Nella replica primaria si tratta del numero di byte inviati alla replica secondaria. Nella replica secondaria si tratta del numero di byte inviati alla replica primaria.|  
|**Byte inviati al trasporto/sec**|Numero effettivo di byte inviati, tramite la rete, alla replica di disponibilità remota al secondo. Nella replica primaria si tratta del numero di byte inviati alla replica secondaria. Nella replica secondaria si tratta del numero di byte inviati alla replica primaria.|  
|**Ora controllo di flusso (ms/sec)**|Tempo in millisecondi di attesa prima che i messaggi del flusso di log siano sottoposti a controllo del flusso di invio nell'ultimo secondo.|  
|**Controllo di flusso/sec**|Numero di avvii di controlli di flusso nell'ultimo secondo. **Ora controllo di flusso (ms/sec)** diviso per **Controllo di flusso/sec** è il tempo medio per attesa.|  
|**Ricezioni dalla replica/sec**|Numero di messaggi AlwaysOn ricevuti dalla replica al secondo.|  
|**Messaggi reinviati/sec**|Numero di messaggi AlwaysOn reinviati nell'ultimo secondo.|  
|**Invii alla replica/sec**|Numero di messaggi AlwaysOn inviati alla replica di disponibilità al secondo.|  
|**Invii al trasporto/sec**|Numero effettivo di messaggi AlwaysOn inviati, tramite la rete, alla replica di disponibilità remota al secondo. Nella replica primaria si tratta del numero di messaggi inviati alla replica secondaria. Nella replica secondaria si tratta del numero di messaggi inviati alla replica primaria.|  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio dell'utilizzo delle risorse &#40;Monitor di sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [SQL Server, replica di database](../../relational-databases/performance-monitor/sql-server-database-replica.md)   
 [Gruppi di disponibilità Always On (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
