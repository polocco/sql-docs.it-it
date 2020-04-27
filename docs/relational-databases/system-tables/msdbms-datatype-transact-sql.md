---
title: MSdbms_datatype (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdbms_datatype
- MSdbms_datatype_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdbms_datatype system table
ms.assetid: 606168cc-79a8-442f-ab43-936f8f884d72
author: stevestein
ms.author: sstein
ms.openlocfilehash: 301aa5af9aa34031f381235341f1e7d461675432
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "67907517"
---
# <a name="msdbms_datatype-transact-sql"></a>MSdbms_datatype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La tabella **MSdbms_datatype** contiene l'elenco completo dei tipi di dati nativi in ogni sistema di gestione di database (DBMS) supportato utilizzato come server di pubblicazione o sottoscrittore nella replica di database eterogenei. Questa tabella è archiviata nel database **msdb** .  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**datatype_id**|**int**|Identifica ogni tipo di dati univoco.|  
|**dbms_id**|**int**|Identifica il sistema DBMS al quale appartiene il tipo.|  
|**type**|**sysname**|Nome del tipo di dati (nativo).|  
|**CreateParams**|**int**|Mappa di bit che descrive la combinazione di lunghezza, precisione e scala valida per ogni tipo di dati, che include:<br /><br /> **0x1** = Precision.<br /><br /> **0x2** = scala.<br /><br /> **0x4** = length.|  
  
## <a name="remarks"></a>Osservazioni  
 Questa tabella contiene le voci per i tipi di dati di SQL Server in quanto un'istanza di SQL Server può sottoscrivere un database non SQL Server e pubblicare in un Sottoscrittore non SQL Server.  
  
## <a name="see-also"></a>Vedi anche  
 [Replica di database eterogenei](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Specificare i mapping dei tipi di dati per un server di pubblicazione Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Tabelle di replica &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
