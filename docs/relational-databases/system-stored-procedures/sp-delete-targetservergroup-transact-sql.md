---
description: sp_delete_targetservergroup (Transact-SQL)
title: sp_delete_targetservergroup (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_targetservergroup_TSQL
- sp_delete_targetservergroup
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_targetservergroup
ms.assetid: d8dd838e-64aa-419f-9ccb-ff04908cf3e4
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c1aebbb09f70f0a0cc3756c4cec53decc0cdbf94
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2020
ms.locfileid: "89548115"
---
# <a name="sp_delete_targetservergroup-transact-sql"></a>sp_delete_targetservergroup (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Elimina il gruppo di server di destinazione specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_delete_targetservergroup [ @name = ] 'name'   
```  
  
## <a name="arguments"></a>Argomenti  
`[ @name = ] 'name'` Nome del gruppo di server di destinazione da rimuovere. *Name* è di **tipo sysname**e non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 nessuno  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene rimosso il gruppo di server di destinazione `Servers Processing Customer Orders`.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_delete_targetservergroup  
    @name = N'Servers Processing Customer Orders';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_add_targetservergroup &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql.md)   
 [sp_help_targetservergroup &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql.md)   
 [sp_update_targetservergroup &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql.md)  
  
  
