---
description: MSrepl_originators (Transact-SQL)
title: MSrepl_originators (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSrepl_originators_TSQL
- MSrepl_originators
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_originators system table
ms.assetid: a3ac20a6-73f6-4fdc-ad5f-5f72746c9871
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 19e66da5cab574e18b592e0636cd9b3412870a10
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2020
ms.locfileid: "89544497"
---
# <a name="msrepl_originators-transact-sql"></a>MSrepl_originators (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  La tabella **MSrepl_originators** contiene una riga per ogni Sottoscrittore aggiornabile da cui ha avuto origine la transazione. Questa tabella è archiviata nel database di distribuzione.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Identifica il Sottoscrittore aggiornabile.|  
|**publisher_database_id**|**int**|Identifica il database di pubblicazione.|  
|**srvname**|**sysname**|Nome del server aggiornabile.|  
|**dbname**|**sysname**|Nome del database aggiornabile.|  
|**publication_id**|**int**|Identifica la pubblicazione.|  
|**DBVERSION**|**int**|Identifica la versione del database.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
