---
title: Pulizia dei metadati di merge (SP di replica)
description: Rimuovere i dati nelle tabelle di replica di tipo merge a livello di programmazione usando le stored procedure di replica
ms.custom: seo-lt-2019
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- metadata [SQL Server replication]
- sp_mergemetadataretentioncleanup
ms.assetid: 9b88baea-b7c6-4e5d-88f9-93d6a0ff0368
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3b11994be2889cce85b2be739dad5e991a5c55b3
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85897945"
---
# <a name="clean-up-merge-metadata-replication-transact-sql-programming"></a>Pulizia dei metadati di merge (programmazione Transact-SQL della replica)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  La rimozione dei metadati della replica di tipo merge viene eseguita periodicamente dall'agente di merge in base all'impostazione di memorizzazione per la pubblicazione. Nel server di pubblicazione e nel Sottoscrittore ciò avviene nelle tabelle di sistema [MSmerge_genhistory](../../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), [MSmerge_contents](../../../relational-databases/system-tables/msmerge-contents-transact-sql.md), [MSmerge_tombstone](../../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md), [MSmerge_past_partition_mappings](../../../relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql.md)e [MSmerge_current_partition_mappings](../../../relational-databases/system-tables/msmerge-current-partition-mappings.md) . È inoltre possibile rimuovere i dati in tali tabelle a livello di programmazione utilizzando le stored procedure di replica.  
  
### <a name="to-manually-clean-up-merge-metadata"></a>Per pulire manualmente i metadati di merge  
  
1.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_mergemetadataretentioncleanup](../../../relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql.md).  
  
2.  (Facoltativo) Tenere presente il numero di righe rimosse nel passaggio 1 dalle tabelle di sistema [MSmerge_genhistory](../../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), [MSmerge_contents](../../../relational-databases/system-tables/msmerge-contents-transact-sql.md)e [MSmerge_tombstone](../../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md). Tali valori sono restituiti rispettivamente nei parametri di output `@num_genhistory_rows``@num_contents_rows` e `@num_tombstone_rows`.  
  
3.  Ripetere i passaggi 1 e 2 nel Sottoscrittore per eseguire la pulizia dei metadati nel database di sottoscrizione.  
  
## <a name="see-also"></a>Vedere anche  
 [Scadenza e disattivazione delle sottoscrizioni](../../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  
