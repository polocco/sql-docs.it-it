---
description: catalog.executable_statistics
title: catalog.executable_statistics | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 3dda28d6-10d8-4294-9b5e-a6048c07faf9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b2690d60c080f3a565e45ee1bcc4cac10d07cf42
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88495254"
---
# <a name="catalogexecutable_statistics"></a>catalog.executable_statistics 

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Consente di visualizzare una riga per ogni file eseguibile in esecuzione, inclusa ogni iterazione di un file eseguibile.  
  
 Un eseguibile è un'attività o un contenitore aggiunto al flusso di controllo di un pacchetto.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|Statistics_id|bigint|ID univoco dei dati.|  
|Execution_id|bigint|ID univoco per l'istanza dell'esecuzione.<br /><br /> La vista catalog.executions fornisce informazioni aggiuntive sulle esecuzioni. Per altre informazioni, vedere [catalog.executions &#40;database SSISDB&#41;](../../integration-services/system-views/catalog-executions-ssisdb-database.md).|  
|Executable_id|bigint|ID univoco per il componente del pacchetto.<br /><br /> La vista catalog.executables fornisce informazioni aggiuntive sui file eseguibili. Per altre informazioni, vedere [catalog.executables](../../integration-services/system-views/catalog-executables.md).|  
|Execution_path|nvarchar(max)|Percorso di esecuzione completo del componente del pacchetto, inclusa ogni iterazione del componente.|  
|Start_time|datetimeoffset(7)|Ora in cui il file eseguibile passa nella fase di pre-esecuzione.|  
|End_time|datetimeoffset(7)|Ora in cui il file eseguibile passa nella fase di post-esecuzione.|  
|Execution_duration|INT|Durata di tempo di esecuzione del file eseguibile. Il valore è espresso in millisecondi.|  
|Execution_result|SMALLINT|Di seguito sono indicati i valori possibili:<br /><br /> 0 (Esito positivo)<br /><br /> 1 (Esito negativo)<br /><br /> 2 (Completamento)<br /><br /> 3 (Esecuzione annullata)|  
|Execution_value|sql_variant|Valore restituito dall'esecuzione. Si tratta di un valore definito dall'utente.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Per questa vista è necessaria una delle autorizzazioni seguenti:  
  
-   Autorizzazione READ per l'istanza dell'esecuzione.  
  
-   Appartenenza al ruolo del database **ssis_admin**.  
  
-   Appartenenza al ruolo del server **sysadmin**.  
  
  
