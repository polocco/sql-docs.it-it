---
title: syspolicy_policy_execution_history (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_execution_history_TSQL
- syspolicy_policy_execution_history
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policy_execution_history view
ms.assetid: b13c44a7-6d49-4d50-abe1-e657fc52bb05
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9e6f8200b1c49bfe5e4977dc1e8f093537fc950e
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85900570"
---
# <a name="syspolicy_policy_execution_history-transact-sql"></a>syspolicy_policy_execution_history (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Visualizza l'ora in cui i criteri sono stati eseguiti, il risultato di ogni esecuzione e le informazioni su eventuali errori. Nella tabella seguente sono descritte le colonne contenute nella vista syspolicy_policy_execution_history.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|history_id|**bigint**|Identificatore del record. Ogni record indica i criteri e l'ora in cui è stato avviato.|  
|policy_id|**int**|Identificatore dei criteri.|  
|start_date|**datetime**|Data e ora in cui è stato effettuato un tentativo di esecuzione di questi criteri.|  
|end_date|**datetime**|Ora in cui è terminata l'esecuzione di questi criteri.|  
|result|**bit**|Esito positivo o negativo dei criteri. 0 = esito negativo, 1 = esito positivo.|  
|exception_message|**nvarchar(max)**|Messaggio generato da un'eventuale eccezione.|  
|exception|**nvarchar(max)**|Descrizione dell'eventuale eccezione.|  
  
## <a name="remarks"></a>Osservazioni  
 Nella visualizzazione [syspolicy_policy_execution_history_details](../../relational-databases/system-catalog-views/syspolicy-policy-execution-history-details-transact-sql.md) sono contenuti dettagli correlati sulle destinazioni dei criteri e sulle espressioni di condizione testate.  
  
## <a name="permissions"></a>Autorizzazioni  
 È necessaria l'appartenenza al ruolo PolicyAdministratorRole nel database msdb.  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrare i server tramite la gestione basata su criteri](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [Viste di Gestione basata su criteri &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
