---
title: Opzione di configurazione del server Affinity Mask I/O | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- affinity I/O mask option
- processor affinity [SQL Server]
- binding processors [SQL Server]
- CPU affinity mask option
ms.assetid: 9950a8c9-9fe0-4003-95df-6f0d1becb0e7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 65e412a3dfdfc71931e6af4d449c5be88ae351b7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62813679"
---
# <a name="affinity-input-output-mask-server-configuration-option"></a>Opzione di configurazione del server Affinity Mask I/O
  Per implementare l'elaborazione multitasking, talvolta [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 e Windows Server 2003 spostano i thread dei processi tra diversi processori. Anche se in questo modo viene garantita una maggiore efficienza del sistema operativo, questa attività può comportare una riduzione delle prestazioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel caso di carichi di lavoro elevati, poiché la cache di ogni processore viene ricaricata più volte con dati. In tali condizioni, l'assegnazione dei processori a specifici thread può aumentare le prestazioni eliminando il ricaricamento dei processori. Questa associazione tra un thread e un processore è definita affinità processori.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta l'affinità processori per mezzo di due opzioni affinity mask: **affinity mask** (nota anche come **CPU affinity mask**) e **affinity I/O mask**. Per altre informazioni sull'opzione **affinity mask** , vedere [Opzione di configurazione del server affinity mask](affinity-mask-server-configuration-option.md). Il supporto di CPU e Affinity I/O per server con 33 fino a 64 processori richiede rispettivamente l'uso aggiuntivo dell' [opzione di configurazione del server affinity64 mask](affinity64-mask-server-configuration-option.md) e dell' [opzione di configurazione del server affinity64 Input-Output mask](affinity64-input-output-mask-server-configuration-option.md) .  
  
> [!NOTE]  
>  Il supporto dell'affinità nei server dotati di un numero di processori compreso tra 33 e 64 è disponibile solo su sistemi operativi a 64 bit.  
  
 L'opzione **affinity I/O mask** associa l'I/O su disco di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a un subset specificato di CPU. Negli ambienti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di fascia alta con elaborazione delle transazioni online (OLTP), questa estensione può migliorare le prestazioni dei thread di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che generano operazioni di I/O. Questa funzionalità avanzata non supporta affinità hardware per singoli dischi o controller del disco.  
  
 Il valore di **affinity I/O mask** specifica quali CPU di un computer multiprocessore sono idonee a elaborare le operazioni di I/O su disco di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . La maschera è costituita da una mappa di bit nella quale il primo bit a destra specifica la CPU di ordine inferiore (ovvero CPU(0)), il bit alla sua immediata sinistra specifica la CPU di ordine successivo (ovvero CPU(1)) e così via. Per configurare più di 32 processori, impostare sia l'opzione **affinity I/O mask** che l'opzione **affinity64 I/O mask**.  
  
 I valori di **affinity I/O mask** sono i seguenti:  
  
-   L'uso di una **affinity I/O mask** da 1 byte copre fino a 8 CPU in un computer multiprocessore.  
  
-   L'uso di una **affinity I/O mask** da 2 byte copre fino a 16 CPU in un computer multiprocessore.  
  
-   L'uso di una **affinity I/O mask** da 3 byte copre fino a 24 CPU in un computer multiprocessore.  
  
-   L'uso di una **affinity I/O mask** da 4 byte copre fino a 32 CPU in un computer multiprocessore.  
  
-   Per coprire più di 32 CPU, configurare una **affinity I/O mask** da 4 byte per le prime 32 CPU e una **affinity64 I/O mask** fino a 4 byte per le CPU rimanenti.  
  
 Un bit 1 nello schema della maschera di affinità di I/O indica che la CPU corrispondente è idonea all'esecuzione di operazioni di I/O su disco di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , mentre un bit 0 indica che per la CPU corrispondente non deve essere pianificata alcuna operazione di I/O su disco di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Quando tutti i bit sono impostati su zero oppure l'opzione **affinity I/O mask** non è specificata, le operazioni di I/O su disco di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono pianificate per una qualsiasi CPU idonea a elaborare i thread di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 L'impostazione dell'opzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]affinity I/O mask**di** è un'attività complessa, che è consigliabile eseguire solo in caso di necessità. Nella maggior parte dei casi l'affinità predefinita di Windows 2000 o Windows Server 2003 garantisce livelli di prestazioni ottimali.  
  
 Quando si specifica l'opzione **affinity I/O mask** , è necessario usarla insieme all'opzione di configurazione **affinity mask** . Non abilitare la stessa CPU sia nell'opzione **affinity I/O mask** che nell'opzione **affinity mask** . I bit corrispondenti alle singole CPU devono rispettare uno dei tre stati seguenti:  
  
-   0 sia nell'opzione **affinity I/O mask** che nell'opzione **affinity mask** .  
  
-   1 nell'opzione **affinity I/O mask** e 0 nell'opzione **affinity mask** .  
  
-   0 nell'opzione **affinity I/O mask** e 1 nell'opzione **affinity mask** .  
  
 L'opzione **affinity I/O mask** è un'opzione avanzata. Se si usa il `sp_configure` stored procedure di sistema per modificare l'impostazione, è possibile modificare **affinity I/O mask** solo quando il valore di **Show Advanced Options** è impostato su 1. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], per riconfigurare l'opzione **affinity I/O mask** è necessario riavviare l'istanza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!CAUTION]  
>  Non configurare l'affinità di CPU nel sistema operativo Windows e contemporaneamente l'opzione affinity mask in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le due impostazioni mirano a ottenere lo stesso risultato e, se le configurazioni sono incoerenti, potrebbero causare risultati imprevisti. La configurazione ottimale dell'affinità di CPU in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può essere ottenuta utilizzando l'opzione `sp_configure` di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio dell'utilizzo delle risorse &#40;Monitor di sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Opzioni di configurazione del server &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
