---
description: xp_revokelogin (Transact-SQL)
title: xp_revokelogin (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_revokelogin
- xp_revokelogin_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- xp_revokelogin
ms.assetid: b3fa7678-dba4-4537-be94-5ae63ca11f81
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 040560b9d69ecec0388109eaf4c032ac24a60688
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419205"
---
# <a name="xp_revokelogin-transact-sql"></a>xp_revokelogin (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Revoca l'accesso a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a un gruppo o un utente di Windows.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] In alternativa, usare [Drop login](../../t-sql/statements/drop-login-transact-sql.md) .  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
xp_revokelogin {[@loginame=] 'login'}  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @loginame = ] 'login'` Nome dell'utente o del gruppo di Windows da cui revocare l'accesso. l' *account di accesso* deve includere il nome di dominio, ad esempio **[ADVWKS\sylvester1]**. *login* è di **tipo sysname**e non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 0 (operazione completata) o 1 (operazione non riuscita)  
  
## <a name="remarks"></a>Osservazioni  
 In alternativa, usare DROP LOGIN.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione ALTER ANY LOGIN nel server.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_denylogin &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_grantlogin &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_revokelogin &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [Stored procedure di sistema &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Stored procedure estese generali &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [xp_loginconfig &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/xp-loginconfig-transact-sql.md)   
 [xp_logininfo &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md)  
  
  
