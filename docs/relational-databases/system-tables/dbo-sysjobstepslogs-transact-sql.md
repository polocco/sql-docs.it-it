---
title: dbo.sysjobstepslogs (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysjobstepslogs_TSQL
- sysjobstepslogs_TSQL
- sysjobstepslogs
- dbo.sysjobstepslogs
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobstepslogs system table
ms.assetid: 128c25db-0b71-449d-bfb2-38b8abcf24a0
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9da9079ff2890525c56074857edbaa013a193d7b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750334"
---
# <a name="dbosysjobstepslogs-transact-sql"></a>dbo.sysjobstepslogs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Contiene il log dei passaggi del processo per tutti i passaggi dei processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent configurati per la scrittura del relativo output in una tabella. Questa tabella è archiviata nel database **msdb** .  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**log_id**|**int**|ID del log dei passaggi del processo.|  
|**log**|**nvarchar(max)**|Contenuto del log dei passaggi del processo.|  
|**date_created**|**datetime**|Data e ora di creazione del log dei passaggi del processo.|  
|**date_modified**|**datetime**|Data e ora dell'ultima modifica del log dei passaggi del processo.|  
|**log_size**|**int**|Dimensioni in byte del log dei passaggi del processo.|  
|**step_uid**|**uniqueidentifier**|ID univoco del passaggio del processo.|  
  
## <a name="see-also"></a>Vedere anche  
 [sp_help_jobsteplog &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-help-jobsteplog-transact-sql.md)   
 [sp_delete_jobsteplog &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql.md)  
  
  
