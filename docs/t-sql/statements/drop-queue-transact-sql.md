---
title: DROP QUEUE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP QUEUE
- DROP_QUEUE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dropping queues
- queues [Service Broker], removing
- deleting queues
- DROP QUEUE statement
- removing queues
ms.assetid: fd866520-ca00-477d-b2e9-0110e9610ed4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7b2d3c9461fb101657d3bf26f2e7bd57baa4dc7a
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2020
ms.locfileid: "81635266"
---
# <a name="drop-queue-transact-sql"></a>DROP QUEUE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Elimina una coda esistente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```syntaxsql
  
DROP QUEUE <object>  
[ ; ]  
  
<object> ::=  
{ database_name.schema_name.queue_name | schema_name.queue_name | queue_name }
```  
  
## <a name="arguments"></a>Argomenti  
 *database_name*  
 Nome del database contenente la coda da eliminare. Se non si specifica *database_name*, per impostazione predefinita viene usato il database corrente.  
  
 *schema_name (object)*  
 Nome dello schema a cui appartiene la coda da eliminare. Se non si specifica *schema_name*, per impostazione predefinita viene usato lo schema predefinito dell'utente corrente.  
  
 *queue_name*  
 Nome della coda da eliminare.  
  
## <a name="remarks"></a>Osservazioni  
 Non è possibile eliminare una coda se esistono servizi che fanno riferimento a essa.  
  
## <a name="permissions"></a>Autorizzazioni  
 L'autorizzazione per eliminare una coda viene assegnata per impostazione predefinita al proprietario della coda, ai membri del ruolo predefinito del database **db_ddladmin** o **db_owner** e ai membri del ruolo predefinito del server **sysadmin**.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente elimina la coda **ExpenseQueue** dal database corrente.  
  
```  
DROP QUEUE ExpenseQueue ;  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE QUEUE &#40;Transact-SQL&#41;](../../t-sql/statements/create-queue-transact-sql.md)   
 [ALTER QUEUE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-queue-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
