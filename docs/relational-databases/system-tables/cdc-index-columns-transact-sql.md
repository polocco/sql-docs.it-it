---
description: cdc.index_columns (Transact-SQL)
title: CDC. index_columns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc.index_columns_TSQL
- cdc.index_columns
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.index_columns
ms.assetid: 256ec8a5-3031-40a8-9fdb-99db42ea453d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5cf09c3a66a3db1b7275dfe8017d953aaf57b42d
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2020
ms.locfileid: "89544637"
---
# <a name="cdcindex_columns-transact-sql"></a>cdc.index_columns (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Restituisce una riga per ogni colonna dell'indice associata a una tabella delle modifiche. Le colonne dell'indice vengono utilizzate da Change Data Capture per identificare in modo univoco le righe della tabella di origine. Per impostazione predefinita, vengono incluse le colonne della chiave primaria della tabella di origine. Se tuttavia viene specificato un indice univoco nella tabella di origine quando Change Data Capture è abilitato nella tabella di origine, vengono utilizzate le colonne di tale indice. Nella tabella di origine viene richiesto un indice univoco o una chiave primaria se è abilitato il rilevamento delle modifiche totali. Per ulteriori informazioni, vedere [sys. sp_cdc_enable_table &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md).  
  
 È consigliabile non eseguire una query direttamente sulle tabelle di sistema. Eseguire invece il stored procedure [sys. sp_cdc_help_change_data_capture](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md) .  

  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID della tabella delle modifiche.|  
|**column_name**|**sysname**|Nome della colonna dell'indice.|  
|**index_ordinal**|**tinyint**|Ordinale (in base 1) della colonna all'interno dell'indice.|  
|**column_id**|**int**|ID della colonna della tabella di origine.|  
  
## <a name="see-also"></a>Vedere anche  
 [CDC. change_tables &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/cdc-change-tables-transact-sql.md)  
  
  
