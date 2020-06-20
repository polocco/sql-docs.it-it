---
title: Oggetto Memory Manager di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Memory Manager
- Memory Manager object
ms.assetid: dbf49000-eeb0-4e9c-a361-5092363920dc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 06b58b9b6bb8a5c13e0b220ba9eeea5818682abf
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85066954"
---
# <a name="sql-server-memory-manager-object"></a>Oggetto Memory Manager di SQL Server
  L'oggetto **Memory Manager** di Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] include contatori per il monitoraggio dell'utilizzo complessivo della memoria del server. Tale monitoraggio che consente di misurare l'attività degli utenti e l'utilizzo delle risorse può risultare utile per identificare eventuali colli di bottiglia. Con il monitoraggio dell'utilizzo della memoria da parte di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è possibile rilevare le situazioni seguenti:  
  
-   Presenza di colli di bottiglia in seguito a quantità di memoria fisica non sufficiente per l'archiviazione nella cache dei dati di accesso frequente. Nel caso di memoria insufficiente, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve recuperare i dati dal disco.  
  
-   È possibile migliorare le prestazioni delle query aggiungendo memoria o rendendo disponibile una maggiore quantità di memoria per la cache dei dati o le strutture interne di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="memory-manager-counters"></a>Contatori Memory Manager  
 Nella tabella seguente vengono descritti i contatori dell'oggetto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Memory Manager**di**.  
  
|Contatori Memory Manager di SQL Server|Descrizione|  
|----------------------------------------|-----------------|  
|**Memoria connessioni (KB)**|Specifica la quantità totale di memoria dinamica utilizzata dal server per gestire le connessioni.|  
|**Memoria cache di database (KB)**|Specifica la quantità totale di memoria attualmente utilizzata dal server per la cache delle pagine del database.|  
|**Memoria disponibile (KB)**|Specifica la quantità di memoria allocata attualmente non utilizzata dal server.|  
|**Memoria area di lavoro concessa (KB)**|Specifica la quantità totale di memoria concessa per l'esecuzione di processi, quali operazioni di hashing, ordinamento, copia bulk e creazione di indici.|  
|**Blocchi di blocco**|Specifica il numero corrente di blocchi di blocco in uso nel server (valore aggiornato periodicamente). Un blocco di blocco rappresenta una singola risorsa bloccata, ad esempio una tabella, una pagina o una riga.|  
|**Blocchi di blocco allocati**|Specifica il numero corrente di blocchi di blocco allocati. All'avvio del server il numero dei blocchi di blocco allocati più il numero dei blocchi dei proprietari di blocco allocati varia a seconda dell'opzione di configurazione  **Locks** di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se è necessario un maggior numero di blocchi di blocco, il valore aumenta.|  
|**Memoria blocchi (KB)**|Specifica la quantità totale di memoria dinamica utilizzata dal server per i blocchi.|  
|**Blocchi proprietari di blocco**|Specifica il numero di blocchi dei proprietari di blocco in uso nel server (valore aggiornato periodicamente). Un blocco di proprietario di blocco rappresenta la detenzione della proprietà di un blocco su un oggetto da parte di un singolo thread. Di conseguenza, se tre thread dispongono ciascuno di un blocco condiviso (S) su una pagina, saranno presenti tre blocchi dei proprietari di blocco.|  
|**Blocchi proprietari di blocco allocati**|Specifica il numero corrente di blocchi dei proprietari di blocco allocati. All'avvio del server il numero dei blocchi dei proprietari di blocco allocati e il numero dei blocchi di blocco allocati varia a seconda dell'opzione di configurazione  **Locks** di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se è necessario un maggior numero di blocchi dei proprietari di blocco, il valore aumenta in modo dinamico.|  
|**Memoria massima area di lavoro (KB)**|Indica la quantità massima di memoria disponibile per l'esecuzione di processi, quali operazioni di hashing, ordinamento, copia bulk e creazione di indici.|  
|**Concessioni di memoria in attesa**|Specifica il numero totale di processi a cui è stata concessa memoria per l'area di lavoro.|  
|**Concessioni di memoria in sospeso**|Specifica il numero totale di processi in attesa di ottenere memoria per l'area di lavoro.|  
|**Memoria Query Optimizer (KB)**|Specifica la quantità totale di memoria dinamica utilizzata dal server per l'ottimizzazione delle query.|  
|**Memoria server riservata (KB)**|Indica la quantità di memoria che il server ha riservato per l'utilizzo futuro. Questo contatore indica la quantità di memoria corrente non utilizzata e inizialmente concessa indicata in **Memoria area di lavoro concessa (KB)**.|  
|**Memoria cache SQL (KB)**|Specifica la quantità totale di memoria dinamica utilizzata dal server per la cache SQL dinamica.|  
|**Memoria server prelevata (KB)**|Specifica la quantità di memoria utilizzata dal server per fini diversi dalle pagine del database.|  
|**Memoria prevista server (KB)**|Indica la quantità totale di memoria dinamica disponibile per il server.|  
|**Memoria totale server (KB)**|Specifica la quantità totale di memoria riservata dal server tramite Gestione memoria.|  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare l'utilizzo delle risorse &#40;monitoraggio di sistema&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server, oggetto Gestione buffer](sql-server-buffer-manager-object.md)   
 [sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
