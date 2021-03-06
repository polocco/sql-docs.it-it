---
description: sp_script_synctran_commands (Transact-SQL)
title: sp_script_synctran_commands (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_script_synctran_commands
- sp_script_synctran_commands_TSQL
helpviewer_keywords:
- sp_script_synctran_commands
ms.assetid: f132694a-dd05-405b-9d84-21acce9e564a
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f596a02346748cedcc6b99ada4e0a6122b184673
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2020
ms.locfileid: "89541594"
---
# <a name="sp_script_synctran_commands-transact-sql"></a>sp_script_synctran_commands (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Genera uno script che contiene le chiamate **sp_addsynctrigger** da applicare ai sottoscrittori per le sottoscrizioni aggiornabili. È presente una **sp_addsynctrigger** chiamata per ogni articolo della pubblicazione. Lo script generato contiene inoltre le chiamate **sp_addqueued_artinfo** che creano la tabella **MSsubsciption_articles** necessaria per elaborare le pubblicazioni in coda. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_script_synctran_commands [@publication = ] 'publication'  
    [ , [@article = ] 'article']  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @publication = ] 'publication'` Nome della pubblicazione da inserire nello script. *Publication* è di **tipo sysname**e non prevede alcun valore predefinito.  
  
`[ @article = ] 'article'` Nome dell'articolo da inserire nello script. *article* è di **tipo sysname**e il valore predefinito è **All**, che specifica che tutti gli articoli sono inclusi nello script.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="results-set"></a>Set di risultati  
 **sp_script_synctran_commands** restituisce un set di risultati costituito da una singola colonna **nvarchar (4000)** . Il set di risultati forma gli script completi necessari per creare le chiamate **sp_addsynctrigger** e **sp_addqueued_artinfo** da applicare ai sottoscrittori.  
  
## <a name="remarks"></a>Osservazioni  
 **sp_script_synctran_commands** viene utilizzata per la replica snapshot e transazionale.  
  
 **sp_addqueued_artinfo** viene utilizzata per le sottoscrizioni aggiornabili in coda.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del ruolo predefinito del server **sysadmin** o del ruolo predefinito del database **db_owner** possono eseguire **sp_script_synctran_commands**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_addsynctriggers &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sp-addsynctriggers-transact-sql.md)   
 [sp_addqueued_artinfo &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sp-addqueued-artinfo-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
