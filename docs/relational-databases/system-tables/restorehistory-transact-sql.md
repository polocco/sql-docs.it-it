---
description: restorehistory (Transact-SQL)
title: restorehistory (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- restorehistory
- restorehistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- restorehistory system table
ms.assetid: 9140ecc1-d912-4d76-ae70-e2a857da6d44
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 03b5887ee905d5a39bce5ef9e73e78e27b581972
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2020
ms.locfileid: "89540841"
---
# <a name="restorehistory-transact-sql"></a>restorehistory (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Contiene una riga per ogni operazione di ripristino. Questa tabella è archiviata nel database **msdb** .  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**restore_history_id**|**int**|Numero di identificazione univoco che identifica ogni operazione di ripristino. Identità, chiave primaria.|  
|**restore_date**|**datetime**|Data e ora dell'avvio dell'operazione di ripristino. Può essere NULL.|  
|**destination_database_name**|**nvarchar(128)**|Nome del database di destinazione per l'operazione di ripristino. Può essere NULL.|  
|**user_name**|**nvarchar(128)**|Nome dell'utente che ha eseguito l'operazione di ripristino. Può essere NULL.|  
|**backup_set_id**|**int**|Numero di identificazione univoco che identifica il set di backup ripristinato. Fa riferimento a **backupset (backup_set_id)**.|  
|**restore_type**|**char(1)**|Tipo di operazione di ripristino:<br /><br /> D = Database<br /><br /> F = File<br /><br /> G = Filegroup<br /><br /> I = Differenziale<br /><br /> L = Log<br /><br /> V = Solo verifica<br /><br /> Può essere NULL.|  
|**replace**|**bit**|Indica se per l'operazione di ripristino è specificata l'opzione REPLACE:<br /><br /> 1 = Specificata<br /><br /> 0 = Non specificata<br /><br /> Può essere NULL.<br /><br /> Quando un database viene ripristinato come snapshot di database, l'unica opzione è 0.|  
|**recovery**|**bit**|Indica se per l'operazione di ripristino è specificata l'opzione RECOVERY o NORECOVERY:<br /><br /> 1 = RECOVERY<br /><br /> Può essere NULL.<br /><br /> Quando un database viene ripristinato in uno snapshot del database, 1 è l'unica opzione.<br /><br /> 0 = NORECOVERY|  
|**restart**|**bit**|Indica se per l'operazione di ripristino è specificata l'opzione RESTART:<br /><br /> 1 = Specificata<br /><br /> 0 = Non specificata<br /><br /> Può essere NULL.<br /><br /> Quando un database viene ripristinato come snapshot di database, l'unica opzione è 0.|  
|**stop_at**|**datetime**|Ora in cui il database è stato recuperato. Può essere NULL.|  
|**device_count**|**tinyint**|Numero di dispositivi coinvolti nell'operazione di ripristino. Questo numero può essere inferiore al numero dei gruppi di supporti utilizzati per il backup. Può essere NULL.<br /><br /> Quando un database viene ripristinato come snapshot di database, l'unica opzione è 1.|  
|**stop_at_mark_name**|**nvarchar(128)**|Indica il recupero nella transazione contenente il contrassegno specificato. Può essere NULL.<br /><br /> Quando un database viene ripristinato come snapshot di database, questo valore è NULL.|  
|**stop_before**|**bit**|Indica se la transazione contenente il contrassegno specificato è inclusa nell'operazione di recupero:<br /><br /> 0 = L'operazione di recupero viene interrotta prima della transazione contrassegnata.<br /><br /> 1 = Nell'operazione di recupero è inclusa la transazione contrassegnata.<br /><br /> Può essere NULL.<br /><br /> Quando un database viene ripristinato come snapshot di database, questo valore è NULL.|  
  
## <a name="remarks"></a>Osservazioni  
 Per ridurre il numero di righe in questa tabella e in altre tabelle di backup e di cronologia, eseguire la [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) stored procedure.  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di backup e ripristino &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [restorefile &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/restorefile-transact-sql.md)   
 [restorefilegroup &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)   
 [Tabelle di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
