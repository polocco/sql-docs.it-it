---
description: MSpeer_response (Transact-SQL)
title: MSpeer_response (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_response
- MSpeer_response_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_response system table
ms.assetid: 510e24cf-0292-47a9-b1d9-71a30fef030f
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 7e6133bee999ad828516f908aaf770321a59ec3c
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545576"
---
# <a name="mspeer_response-transact-sql"></a>MSpeer_response (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  La tabella **MSpeer_response** viene utilizzata nella replica peer-to-peer per archiviare la risposta di ogni nodo a una richiesta di stato della pubblicazione. Questa tabella è archiviata nel database di pubblicazione.  
  
## <a name="definition"></a>Definizione  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**request_id**|**int**|Identifica una voce della richiesta di stato nella tabella [MSpeer_request](../../relational-databases/system-tables/mspeer-request-transact-sql.md) .|  
|**peer**|**sysname**|Peer che ha generato la risposta.|  
|**peer_db**|**sysname**|Database di sottoscrizione del peer che ha generato la risposta.|  
|**received_date**|**datetime**|Data e ora di ricezione della richiesta peer.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
