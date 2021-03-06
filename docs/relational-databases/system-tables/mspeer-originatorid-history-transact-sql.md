---
description: MSpeer_originatorid_history (Transact-SQL)
title: MSpeer_originatorid_history (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_originatorid_history_TSQL
- MSpeer_originatorid_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_originatorid_history
ms.assetid: c1f53d0f-4080-43ff-be38-2b10395c68c9
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 05ba5720a45bc8d448fe1ed24d6bdc950dcf290d
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545521"
---
# <a name="mspeer_originatorid_history-transact-sql"></a>MSpeer_originatorid_history (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Contiene una riga per ogni ID origine definito nella topologia. Include gli ID dei nodi che non sono più attivi. La tabella viene utilizzata quando si configura un nuovo nodo per il rilevamento dei conflitti per assicurarsi che l'ID origine specificato non sia già stato utilizzato. Questa tabella è archiviata nel database di pubblicazione. Per ulteriori informazioni sul rilevamento dei conflitti, vedere [rilevamento dei conflitti nella replica peer-to-peer](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|originator_publication|**sysname**|Pubblicazione per cui è stato specificato l'ID origine.|  
|originator_id|**int**|Numero che identifica ogni nodo nella topologia per consentire il rilevamento dei conflitti.|  
|originator_node|**sysname**|Istanza del server per cui è stato specificato l'ID origine.|  
|originator_db|**sysname**|Database di pubblicazione per cui è stato specificato l'ID origine.|  
|originator_db_version|**int**|Identifica il numero di versione del database di origine.|  
|originator_version|**int**|Identifica il numero di versione del server di pubblicazione.|  
|inserted_date|**datetime**|Data e ora in cui la riga per l'ID origine è stata inserita in questa tabella.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
