---
title: Creare tracce manuali usando stored procedure | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: f6f47fa2-7c17-41d4-9f69-9be144d56832
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e2840dced22ccdba8fe71cc87c05d7fd6fb4be58
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063053"
---
# <a name="create-manual-traces-using-stored-procedures"></a>Creare tracce manuali utilizzando stored procedure
  In Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono disponibili stored procedure di sistema [!INCLUDE[tsql](../../includes/tsql-md.md)] per la creazione di tracce per un'istanza di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. È possibile utilizzare tali stored procedure di sistema all'interno di applicazioni personalizzate per creare tracce in modo manuale anziché tramite [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Ciò consente di creare applicazioni personalizzate in grado di soddisfare esigenze aziendali specifiche.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 Nella tabella seguente sono elencate le stored procedure di sistema per la traccia di un'istanza di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
|Stored procedure|Operazione eseguita|  
|----------------------|--------------------|  
|[sys.fn_trace_geteventinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql)|Restituisce informazioni sugli eventi inclusi in una traccia.|  
|[sys.fn_trace_getinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql)|Restituisce informazioni sulla traccia specificata o sulle tracce esistenti.|  
|[sp_trace_create &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-create-transact-sql)|Crea la definizione di una nuova traccia nello stato arrestato.|  
|[sp_trace_generateevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql)|Crea un evento definito dall'utente.|  
|[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)|Aggiunge una classe di evento o una colonna dati in una traccia oppure rimuove uno di questi elementi dalla traccia.|  
|[sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)|Avvia, arresta o chiude una traccia.|  
|[sys.fn_trace_getfilterinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getfilterinfo-transact-sql)|Restituisce informazioni sui filtri applicati a una traccia.|  
|[sp_trace_setfilter &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql)|Applica a una traccia un nuovo filtro o un filtro modificato.|  
  
 **Per definire una traccia personalizzata tramite stored procedure**  
  
1.  Tramite **sp_trace_setevent**specificare gli eventi da acquisire.  
  
2.  Specificare eventuali filtri per gli eventi. Per altre informazioni, vedere [Impostare un filtro di traccia &#40;Transact-SQL&#41;](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md).  
  
3.  Tramite **sp_trace_create** specificare la destinazione per i dati degli eventi acquisiti.  
  
 Per un esempio dell'uso di stored procedure relative alla traccia, vedere [Creare una traccia &#40;Transact-SQL&#41;](../sql-trace/create-a-trace-transact-sql.md).  
  
 **Per impostare i valori predefiniti per la definizione della traccia**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
 **Per impostare i valori predefiniti per la visualizzazione della traccia**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)  
  
 **Per creare una traccia**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)  
  
 [Transact-SQL](../sql-trace/create-a-trace-transact-sql.md)  
  
 **Per aggiungere o rimuovere eventi da un modello di traccia**  
  
 [SQL Server Profiler](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
 [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
