---
description: cdc.ddl_history (Transact-SQL)
title: CDC. ddl_history (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc.ddl_history_TSQL
- cdc.ddl_history
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.ddl_history
ms.assetid: cb97ea71-da2f-441a-bbd2-db1f5f48ab49
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c8583394eb282b24f77bb37a81afa23c91ac50d0
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2020
ms.locfileid: "89544707"
---
# <a name="cdcddl_history-transact-sql"></a>cdc.ddl_history (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Restituisce una riga per ogni modifica DDL (Data Definition Language) apportata a tabelle abilitate per l'acquisizione dei dati delle modifiche. È possibile utilizzare questa tabella per determinare quando si è verificata una modifica DDL su una tabella di origine e la modifica effettuata. Per le tabelle di origine per cui non sono state eseguite modifiche DDL non esistono voci in questa tabella.  
  
 È consigliabile non eseguire una query direttamente sulle tabelle di sistema. Eseguire invece il stored procedure [sys. sp_cdc_get_ddl_history](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-ddl-history-transact-sql.md) .  
   
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**source_object_id**|**int**|ID della tabella di origine alla quale è stata applicata la modifica DDL.|  
|**object_id**|**int**|ID della tabella delle modifiche associata a un'istanza di acquisizione per la tabella di origine.|  
|**required_column_update**|**bit**|Indica che il tipo di dati di una colonna acquisita è stato modificato nella tabella di origine. Questa modifica ha modificato la colonna nella tabella delle modifiche.|  
|**ddl_command**|**nvarchar(max)**|Istruzione DDL applicata alla tabella di origine.|  
|**ddl_lsn**|**binary(10)**|Il numero di sequenza del file di log (LSN) associato all'impegno della modifica DDL.|  
|**ddl_time**|**datetime**|Data e ora di esecuzione della modifica DDL nella tabella di origine.|  
  
## <a name="see-also"></a>Vedere anche  
 [sys. sp_cdc_help_change_data_capture &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)   
 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)  
  
  
