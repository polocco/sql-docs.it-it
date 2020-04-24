---
title: MOVE CONVERSATION (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- MOVE_CONVERSATION_TSQL
- MOVE CONVERSATION
- MOVE_TSQL
- MOVE
dev_langs:
- TSQL
helpviewer_keywords:
- moving conversations
- MOVE CONVERSATION statement
- relocating conversations
- conversations [Service Broker], groups
- conversations [Service Broker], moving
ms.assetid: 1da4d2c9-e767-434e-b49b-615711a7f626
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3fe3d20adcfb17026f4a2ca56038a964b1b38c56
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2020
ms.locfileid: "81633241"
---
# <a name="move-conversation-transact-sql"></a>MOVE CONVERSATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Sposta una conversazione in un gruppo di conversazioni diverso.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```syntaxsql
  
MOVE CONVERSATION conversation_handle  
   TO conversation_group_id  
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *conversation_handle*  
 Variabile o costante contenente l'handle di conversazione della conversazione da spostare. *conversation_handle* deve essere di tipo **uniqueidentifier**.  
  
 TO *conversation_group_id*  
 Variabile o costante contenente l'identificatore del gruppo di conversazioni in cui si trova la conversazione da spostare. *conversation_group_id* deve essere di tipo **uniqueidentifier**.  
  
## <a name="remarks"></a>Osservazioni  
 L'istruzione MOVE CONVERSATION sposta la conversazione specificata da *conversation_handle* nel gruppo di conversazioni identificato da *conversation_group_id*. I dialoghi possono essere reindirizzati solo tra gruppi di conversazioni associati alla stessa coda.  
  
> [!IMPORTANT]  
>  Se l'istruzione MOVE CONVERSATION non è la prima istruzione in un batch o in una stored procedure, l'istruzione precedente deve terminare con un punto e virgola ( **;** ), ovvero il terminatore di istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 L'istruzione MOVE CONVERSATION blocca il gruppo di conversazioni associato a *conversation_handle* e il gruppo di conversazioni specificato da *conversation_group_id* finché non viene eseguito il commit o il rollback della transazione contenente l'istruzione.  
  
 MOVE CONVERSATION non è un'istruzione valida in una funzione definita dall'utente.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per spostare una conversazione, l'utente corrente deve essere il proprietario della conversazione e del gruppo di conversazioni, un membro del ruolo predefinito del server sysadmin o un membro del ruolo predefinito del database db_owner.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente una conversazione viene spostata in un gruppo di conversazioni diverso.  
  
```  
DECLARE @conversation_handle UNIQUEIDENTIFIER,  
        @conversation_group_id UNIQUEIDENTIFIER ;  
  
SET @conversation_handle =  
    <retrieve conversation handle from database> ;  
SET @conversation_group_id =  
    <retrieve conversation group ID from database> ;  
  
MOVE CONVERSATION @conversation_handle TO @conversation_group_id ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [BEGIN DIALOG CONVERSATION &#40;Transact-SQL&#41;](../../t-sql/statements/begin-dialog-conversation-transact-sql.md)   
 [GET CONVERSATION GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/get-conversation-group-transact-sql.md)   
 [END CONVERSATION &#40;Transact-SQL&#41;](../../t-sql/statements/end-conversation-transact-sql.md)   
 [sys.conversation_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-conversation-groups-transact-sql.md)   
 [sys.conversation_endpoints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-conversation-endpoints-transact-sql.md)  
  
  
