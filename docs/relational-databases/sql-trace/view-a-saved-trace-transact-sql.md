---
description: Visualizzare una traccia salvata (Transact-SQL)
title: Visualizzare una traccia salvata (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], viewing
- displaying traces
- viewing traces
ms.assetid: 3a95a816-aa89-4d5f-858c-968a9cb3ee87
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c2d709b76d5039560f3f55a720f7f96891aea548
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88324894"
---
# <a name="view-a-saved-trace-transact-sql"></a>Visualizzare una traccia salvata (Transact-SQL)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  In questo argomento viene illustrato l'utilizzo delle funzioni predefinite per visualizzare una traccia salvata.  
  
### <a name="to-view-a-specific-trace"></a>Per visualizzare una traccia specifica  
  
1.  Eseguire **fn_trace_getinfo** specificando l'ID della traccia su cui si vuole ottenere informazioni. Questa funzione restituisce una tabella in cui sono indicate la traccia, la proprietà della traccia e le informazioni sulla proprietà.  

     Richiamare la funzione nel modo seguente:  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(trace_id)  
    ```  
  
### <a name="to-view-all-existing-traces"></a>Per visualizzare tutte le tracce esistenti  
  
1.  Eseguire **fn_trace_getinfo** specificando `0` o `default`. Questa funzione restituisce una tabella in cui sono indicate tutte le tracce, le relative proprietà e le informazioni su tali proprietà.  
  
     Di seguito è illustrato come richiamare la funzione:  
  
    ```  
    SELECT *  
    FROM ::fn_trace_getinfo(default)  
    ```  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 Per eseguire la funzione predefinita **fn_trace_getinfo**, è necessaria l'autorizzazione seguente:  
  
 ALTER TRACE nel server.  
  
## <a name="see-also"></a>Vedere anche  
 [sys.fn_trace_getinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [Visualizzare e analizzare le tracce con SQL Server Profiler](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)  
  
  
