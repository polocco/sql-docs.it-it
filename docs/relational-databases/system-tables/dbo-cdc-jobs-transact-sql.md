---
description: dbo.cdc_jobs (Transact-SQL)
title: dbo. cdc_jobs (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc_jobs
- cdc_jobs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dbo.cdc_jobs
ms.assetid: 85e2d580-1c54-4b81-b7e6-2e12997199fd
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5c7b71f64a66adaf829bd4041a0a14f4e91e30dc
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551070"
---
# <a name="dbocdc_jobs-transact-sql"></a>dbo.cdc_jobs (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Archivia i parametri di configurazione dell'acquisizione dei dati delle modifiche per processi di acquisizione e pulizia. Questa tabella è archiviata in **msdb**.  
  
 
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|ID del database nel quale viene eseguito il processo.|  
|**job_type**|**nvarchar (20)**|Tipo di processo, "acquisizione" o "pulizia".|  
|**job_id**|**uniqueidentifier**|ID univoco associato al processo.|  
|**maxtrans**|**int**|Numero massimo di transazioni da elaborare in ogni ciclo di analisi.<br /><br /> **maxtrans** è valido solo per i processi di acquisizione.|  
|**maxscans**|**int**|Numero massimo di cicli di analisi da eseguire per estrarre tutte le righe dal log.<br /><br /> **maxscans** è valido solo per i processi di acquisizione.|  
|**continuo**|**bit**|Flag che indica se l'esecuzione del processo di acquisizione deve essere continua (1) o come singola occorrenza (0). Per ulteriori informazioni, vedere [sys. sp_cdc_add_job &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md).<br /><br /> **Continuous** è valido solo per i processi di acquisizione.|  
|**PollingInterval**|**bigint**|Numero di secondi tra cicli di analisi del log.<br /><br /> **pollingInterval** è valido solo per i processi di acquisizione.|  
|**conservazione**|**bigint**|Numero di minuti per i quali vengono conservate le righe delle modifiche nelle tabelle delle modifiche.<br /><br /> la **conservazione** è valida solo per i processi di pulizia.|  
|**threshold**|**bigint**|Numero massimo di voci che possono essere eliminate utilizzando un'unica istruzione nel processo di pulizia.|  
  
## <a name="see-also"></a>Vedere anche  
 [sys. sp_cdc_add_job &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)   
 [sys. sp_cdc_change_job &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql.md)   
 [sys. sp_cdc_help_jobs &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md)   
 [sys. sp_cdc_drop_job &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sys-sp-cdc-drop-job-transact-sql.md)  
  
  
