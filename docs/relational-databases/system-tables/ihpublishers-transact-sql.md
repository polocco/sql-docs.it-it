---
description: IHpublishers (Transact-SQL)
title: IHpublishers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublishers
- IHpublishers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublishers system table
ms.assetid: 77007246-f10b-4b87-8edf-7afc3c2096af
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 03d8633b8e859df67d60e8b535cb18c01d031a1e
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551035"
---
# <a name="ihpublishers-transact-sql"></a>IHpublishers (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  La tabella di sistema **IHpublishers** contiene una riga per ogni server di pubblicazione non SQL Server che utilizza il server di distribuzione corrente. Questa tabella è archiviata nel database di distribuzione.  
  
## <a name="definition"></a>Definizione  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Identifica un server di pubblicazione non SQL Server.|  
|**fornitore**|**sysname**|Nome del fornitore per il database non di SQL Server.|  
|**publisher_guid**|**uniqueidentifier**|GUID che identifica il server di pubblicazione non SQL Server.|  
|**flush_request_time**|**datetime**|Indica la data e l'ora in cui è stata apportata l'ultima modifica ai metadati dell'articolo che ha comportato l'aggiornamento da parte dell'agente di lettura log della propria cache dei metadati.|  
|**version**|**sysname**|Stringa di testo che caratterizza la versione del server di pubblicazione non SQL Server.|  
  
## <a name="see-also"></a>Vedere anche  
 [Replica di database eterogenei](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Tabelle di replica &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste di replica &#40;&#41;Transact-SQL ](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_adddistpublisher &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_changedistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_helpdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)  
  
  
