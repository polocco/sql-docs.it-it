---
title: sp_add_targetsvrgrp_member (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_targetsvrgrp_member
- sp_add_targetsvrgrp_member_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_targetsvrgrp_member
ms.assetid: 5021ed5b-acca-4f8b-b9db-18733059c359
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: fb35ca1a700390b51776333e5a62280d5de842ff
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82826286"
---
# <a name="sp_add_targetsvrgrp_member-transact-sql"></a>sp_add_targetsvrgrp_member (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aggiunge il server di destinazione specificato a un determinato gruppo di server di destinazione.  
   
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_add_targetsvrgrp_member [ @group_name = ] 'group_name' , [ @server_name = ] 'server_name'   
```  
  
## <a name="arguments"></a>Argomenti  
`[ @group_name = ] 'group_name'`Nome del gruppo. *group_name* è di **tipo sysname**e non prevede alcun valore predefinito.  
  
`[ @server_name = ] 'server_name'`Nome del server che deve essere aggiunto al gruppo specificato. *server_name* è di **tipo nvarchar (30)** e non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Un server di destinazione può essere membro di più gruppi di server di destinazione.  
  
## <a name="permissions"></a>Autorizzazioni  
 Questa procedura può essere eseguita solo dai membri del ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempio  
 Nell'esempio seguente viene aggiunto il gruppo `Servers Maintaining Customer Information` e viene aggiunto il server `LONDON1` al gruppo specificato.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_targetsvrgrp_member  
   @group_name = N'Servers Maintaining Customer Information',  
   @server_name = N'LONDON1' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_delete_targetsvrgrp_member &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-delete-targetsvrgrp-member-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
