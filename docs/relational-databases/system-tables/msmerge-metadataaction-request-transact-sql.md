---
description: MSmerge_metadataaction_request (Transact-SQL)
title: MSmerge_metadataaction_request (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_metadataaction_request
- MSmerge_metadataaction_request_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_metadataaction_request system table
ms.assetid: cd31a114-900a-4218-ab58-d959e547c647
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 7e616cea34c3c2b440decaec14ac20be3a6bcc30
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2020
ms.locfileid: "89547066"
---
# <a name="msmerge_metadataaction_request-transact-sql"></a>MSmerge_metadataaction_request (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  La tabella **MSmerge_metadataaction_request** archivia una riga per ogni azione di compensazione richiesta. Utilizzando la sincronizzazione Web, se si verifica un errore e la sincronizzazione deve essere ripetuta, viene apportata una voce in **MSmerge_metadataaction_request**. Durante la fase di caricamento del merge successivo, le richieste di tutti gli articoli facenti parte della pubblicazione in fase di sincronizzazione vengono recuperate da questa tabella e caricate. Quando la sincronizzazione viene completata correttamente, viene eliminata la riga corrispondente nella tabella **MSmerge_metadataaction_request** . Questa tabella è archiviata nel database di pubblicazione del server di pubblicazione e nel database di sottoscrizione del Sottoscrittore.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|Nome alternativo della tabella pubblicata.|  
|**rowguid**|**uniqueidentifier**|Identificatore della riga specificata.|  
|**action**|**tinyint**|Identifica l'azione di compensazione necessaria.|  
|**generazione**|**bigint**|Valore della generazione per cui l'azione di compensazione è necessaria.|  
|**modificato**|**int**|Solo per uso interno.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste di replica &#40;&#41;Transact-SQL ](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [Sincronizzazione Web per la replica di tipo merge](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  
