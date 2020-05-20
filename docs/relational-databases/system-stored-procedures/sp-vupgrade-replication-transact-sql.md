---
title: sp_vupgrade_replication (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_vupgrade_replication_TSQL
- sp_vupgrade_replication
helpviewer_keywords:
- sp_vupgrade_replication
ms.assetid: d2c0ed66-07d1-4adc-82e5-a654376879bc
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8c63f54756d3bde1ab3c79a0beee9cc06b709d05
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82808622"
---
# <a name="sp_vupgrade_replication-transact-sql"></a>sp_vupgrade_replication (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Viene attivata dal programma di installazione durante l'aggiornamento di un server di replica. Aggiorna i dati dello schema e di sistema per garantire il supporto della replica al livello del prodotto corrente. Crea nuovi oggetti del sistema di replica nei database di sistema e utente. Questa stored procedure viene eseguita nel computer in cui avrà luogo l'aggiornamento della replica.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_vupgrade_replication [ [@login=] 'login' ]  
    [ , [ @password= ] 'password' ]  
    [ , [ @ver_old= ] 'old_version' ]  
    [ , [ @force_remove= ] 'force_removal' ]  
    [ , [ @security_mode= ] security_mode ]  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @login = ] 'login'`Account di accesso dell'amministratore di sistema da utilizzare per la creazione di nuovi oggetti di sistema nel database di distribuzione. *login* è di tipo **sysname** e il valore predefinito è NULL. Questo parametro non è obbligatorio se *security_mode* è impostato su **1**, ovvero l'autenticazione di Windows.  
  
> [!NOTE]  
>  Questo parametro viene ignorato quando si esegue l'aggiornamento a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive.  
  
`[ @password = ] 'password'`Password dell'amministratore di sistema da utilizzare per la creazione di nuovi oggetti di sistema nel database di distribuzione. *password* è di **tipo sysname**e il valore predefinito è **''** (stringa vuota). Questo parametro non è obbligatorio se *security_mode* è impostato su **1**, ovvero l'autenticazione di Windows.  
  
> [!NOTE]  
>  Questo parametro viene ignorato quando si esegue l'aggiornamento a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive.  
  
`[ @ver_old = ] 'old_version'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 Questa stored procedure è deprecata e verrà rimossa a partire da una delle prossime versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
`[ @force_remove = ] 'force_removal'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @security_mode = ] 'security_mode'`Modalità di sicurezza di accesso da utilizzare per la creazione di nuovi oggetti di sistema nel database di distribuzione. *security_mode* è di **bit** e il valore predefinito è **0**. Se è **0**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verrà utilizzata l'autenticazione. Se è **1**, verrà utilizzata l'autenticazione di Windows.  
  
> [!NOTE]  
>  Questo parametro viene ignorato quando si esegue l'aggiornamento a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Commenti  
 **sp_vupgrade_replication** viene utilizzato per l'aggiornamento di tutti i tipi di replica.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del ruolo predefinito del server **sysadmin** possono eseguire **sp_vupgrade_replication**.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di replica &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [Convalida dei dati replicati](../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  
