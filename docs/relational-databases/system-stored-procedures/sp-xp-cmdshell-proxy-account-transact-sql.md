---
title: sp_xp_cmdshell_proxy_account (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_xp_cmdshell_proxy_account
- sp_xp_cmdshell_proxy_account_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_xp_cmdshell_proxy_account
- xp_cmdshell
ms.assetid: f807c373-7fbc-4108-a2bd-73b48a236003
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e908d0bfb70e60330ce47377a8537ebe25f80f09
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827465"
---
# <a name="sp_xp_cmdshell_proxy_account-transact-sql"></a>sp_xp_cmdshell_proxy_account (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Crea una credenziale proxy per **xp_cmdshell**.  
  
> [!NOTE]  
>  **xp_cmdshell** è disabilitato per impostazione predefinita. Per abilitare **xp_cmdshell**, vedere [opzione di configurazione del server xp_cmdshell](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_xp_cmdshell_proxy_account [ NULL | { 'account_name' , 'password' } ]  
```  
  
## <a name="arguments"></a>Argomenti  
 NULL  
 Specifica che la credenziale proxy deve essere eliminata.  
  
 *account_name*  
 Specifica un account di accesso di Windows da utilizzare come proxy.  
  
 *password*  
 Specifica la password dell'account di Windows.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 0 (operazione completata) o 1 (operazione non riuscita)  
  
## <a name="remarks"></a>Commenti  
 La credenziale proxy verrà chiamata **# #xp_cmdshell_proxy_account # #**.  
  
 Quando viene eseguita utilizzando l'opzione NULL, **sp_xp_cmdshell_proxy_account** Elimina la credenziale del proxy.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione CONTROL SERVER.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-creating-the-proxy-credential"></a>R. Creazione delle credenziali proxy  
 Nell'esempio seguente viene illustrata la creazione di una credenziale proxy per un account di Windows denominato `ADVWKS\Max04` con la password `ds35efg##65`.  
  
```  
EXEC sp_xp_cmdshell_proxy_account 'ADVWKS\Max04', 'ds35efg##65';  
GO  
```  
  
### <a name="b-dropping-the-proxy-credential"></a>B. Rimozione delle credenziali proxy  
 Nell'esempio seguente la credenziale proxy viene rimossa dall'archivio delle credenziali.  
  
```  
EXEC sp_xp_cmdshell_proxy_account NULL;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [xp_cmdshell &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/xp-cmdshell-transact-sql.md)   
 [CREAZIONE di credenziali &#40;&#41;Transact-SQL](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys. Credentials &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)   
 [Stored procedure di sistema &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Stored procedure di sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)  
  
  
