---
description: Risultati restituiti dall'attività Script
title: Restituzione di risultati dall'attività Script | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], status information
- ExecutionValue property
- status information [Integration Services]
- TaskResult property
- SSIS Script task, status information
ms.assetid: ac06805b-c2db-44bd-af5c-5a0debe36dd7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d0cd2a7b3b8672e4e309c3293b8694f7968d5991
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88391127"
---
# <a name="returning-results-from-the-script-task"></a>Risultati restituiti dall'attività Script

[!INCLUDE[sqlserver-ssis](../../../includes/applies-to-version/sqlserver-ssis.md)]


  L'attività Script utilizza la proprietà <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> e la proprietà facoltativa <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> per restituire informazioni sullo stato al runtime di [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] che è possibile utilizzare per determinare il percorso del flusso di lavoro al termine dell'attività Script.  
  
## <a name="taskresult"></a>TaskResult  
 La proprietà <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> indica l'esito positivo o negativo dell'attività. Ad esempio:  
  
 `Dts.TaskResult = ScriptResults.Success`  
  
## <a name="executionvalue"></a>ExecutionValue  
 La proprietà <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> restituisce facoltativamente un oggetto definito dall'utente che quantifica o fornisce ulteriori informazioni sull'esito positivo o negativo dell'attività Script. Ad esempio, l'attività FTP utilizza la proprietà <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> per restituire il numero di file trasferiti. L'attività Esegui SQL restituisce il numero di righe interessate dall'attività. La proprietà <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> può anche essere utilizzata per determinare il percorso del flusso di lavoro. Ad esempio:  
  
 `Dim rowsAffected as Integer`  
  
 `...`  
  
 `rowsAffected = 1000`  
  
 `Dts.ExecutionValue = rowsAffected`  
