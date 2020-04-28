---
title: sp_addremotelogin (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addremotelogin_TSQL
- sp_addremotelogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addremotelogin
ms.assetid: 71b7cd36-a17d-4b12-b102-10aeb0f9268b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: eb45ce1c3e1786eb5a9a3cd630741dd4df773c40
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "68030966"
---
# <a name="sp_addremotelogin-transact-sql"></a>sp_addremotelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aggiunge un nuovo ID di accesso remoto nel server locale. Ciò consente ai server remoti di connettersi ed eseguire chiamate di procedure remote.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Utilizzare i server collegati e le stored procedure per i server collegati in alternativa.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_addremotelogin [ @remoteserver = ] 'remoteserver'   
     [ , [ @loginame = ] 'login' ]   
     [ , [ @remotename = ] 'remote_name' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @remoteserver **=** ] **'**_RemoteServer_**'**  
 Nome del server remoto a cui fa riferimento l'account di accesso remoto. *RemoteServer* è di **tipo sysname**e non prevede alcun valore predefinito. Se si specifica solo *RemoteServer* , viene eseguito il mapping di tutti gli utenti in *RemoteServer* a account di accesso esistenti con lo stesso nome nel server locale. Il server deve essere noto al server locale. Il server viene aggiunto tramite sp_addserver. Quando gli utenti di *RemoteServer* si connettono al server locale [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che esegue per eseguire una stored procedure remota, si connettono come account di accesso locale corrispondente al proprio account di accesso in *RemoteServer*. *RemoteServer* è il server che avvia la chiamata RPC.  
  
 [ @loginame **=** ] **'**_login_**'**  
 ID dell'account di accesso dell'utente nell'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *login* è di tipo **sysname** e il valore predefinito è NULL. l' *account di accesso*deve esistere già nell'istanza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]locale di. Se si specifica *login* , viene eseguito il mapping di tutti gli utenti in *RemoteServer* a tale account di accesso locale specifico. Quando gli utenti di *RemoteServer* si connettono all' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza locale di per eseguire una stored procedure remota, si connettono come *account di accesso*.  
  
 [ @remotename **=** ] **'**_remote_name_**'**  
 ID dell'account di accesso dell'utente nel server remoto. *remote_name* è di **tipo sysname**e il valore predefinito è null. *remote_name* deve esistere in *RemoteServer*. Se *remote_name* viene specificato, viene eseguito il mapping del *remote_name* utente specifico all' *account di accesso* nel server locale. Quando *remote_name* su *RemoteServer* si connette all'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per eseguire una stored procedure remota, si connette come *account di accesso*. L'ID di accesso di *remote_name* può essere diverso dall'ID di accesso nel server remoto, *login*.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 0 (operazione completata) o 1 (operazione non riuscita)  
  
## <a name="remarks"></a>Osservazioni  
 Per eseguire query distribuite, utilizzare sp_addlinkedsrvlogin.  
  
 La stored procedure sp_addremotelogin non può essere utilizzata in una transazione definita dall'utente.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del ruolo predefinito del server sysadmin o securityadmin possono eseguire sp_addremotelogin.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-mapping-one-to-one"></a>R. Mapping uno-a-uno  
 Nell'esempio seguente viene eseguito il mapping dei nomi remoti ai nomi locali quando nel server remoto `ACCOUNTS` e in quello locale sono disponibili gli stessi account di accesso.  
  
```  
EXEC sp_addremotelogin 'ACCOUNTS';  
```  
  
### <a name="b-mapping-many-to-one"></a>B. Mapping molti-a-uno  
 Nell'esempio seguente viene creata una voce per mappare tutti gli utenti del server remoto `ACCOUNTS` all'ID di accesso locale `Albert`.  
  
```  
EXEC sp_addremotelogin 'ACCOUNTS', 'Albert';  
```  
  
### <a name="c-using-explicit-one-to-one-mapping"></a>C. Utilizzo del mapping uno-a-uno esplicito  
 Nell'esempio seguente un account di accesso dell'utente remoto `Chris` nel server remoto `ACCOUNTS` viene mappato all'utente locale `salesmgr`.  
  
```  
EXEC sp_addremotelogin 'ACCOUNTS', 'salesmgr', 'Chris';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_addlinkedsrvlogin &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addlogin &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_addserver &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_dropremotelogin &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md)   
 [sp_grantlogin &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_helpremotelogin &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [sp_helpserver &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_remoteoption &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-remoteoption-transact-sql.md)   
 [sp_revokelogin &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
