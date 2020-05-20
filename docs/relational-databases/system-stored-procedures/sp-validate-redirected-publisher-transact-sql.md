---
title: sp_validate_redirected_publisher (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_validate_redirected_publisher
- sp_validate_redirected_publisher_TSQL
helpviewer_keywords:
- sp_validate_redirected_publisher
ms.assetid: 2b7fdbad-17e4-4442-b0b2-9b5e8f84b91d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 09ef147b9051ecbacdc1a33468100f4be2b372e9
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82809116"
---
# <a name="sp_validate_redirected_publisher-transact-sql"></a>sp_validate_redirected_publisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Verifica che l'host corrente per il database del server di pubblicazione sia in grado di supportare la replica. Deve essere eseguito da un database di distribuzione. Questa procedura viene chiamata da **sp_get_redirected_publisher**.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      sp_validate_redirected_publisher   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name',   
    [ @redirected_publisher = ] 'new_publisher' output  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @original_publisher = ] 'original_publisher'`Nome dell'istanza di che ha [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pubblicato originariamente il database. *original_publisher* è di **tipo sysname**e non prevede alcun valore predefinito.  
  
`[ @publisher_db = ] 'publisher_db'`Nome del database da pubblicare. *publisher_db* è di **tipo sysname**e non prevede alcun valore predefinito.  
  
`[ @redirected_publisher = ] 'redirected_publisher'`Destinazione del reindirizzamento specificato quando **sp_redirect_publisher** è stato chiamato per la coppia server di pubblicazione/database. *redirected_publisher* è di **tipo sysname**e non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 No.  
  
## <a name="remarks"></a>Commenti  
 Se non esiste alcuna voce per il server di pubblicazione e il database di pubblicazione, **sp_validate_redirected_publisher** restituisce null nel parametro di output * \@ redirected_publisher*. Se una voce esiste, viene restituita nel parametro di output sia nei casi di esito positivo che di esito negativo.  
  
 Se la convalida ha esito positivo, **sp_validate_redirected_publisher** restituisce un'indicazione di esito positivo.  
  
 Se la convalida non riesce, vengono generati gli errori con la relativa descrizione.  
  
## <a name="permissions"></a>Autorizzazioni  
 Il chiamante deve essere un membro del ruolo predefinito del server **sysadmin** , il **db_owner** ruolo predefinito del database per il database di distribuzione o un membro di un elenco di accesso alla pubblicazione per una pubblicazione definita associata al database del server di pubblicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di replica &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_get_redirected_publisher &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-get-redirected-publisher-transact-sql.md)   
 [sp_redirect_publisher &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-redirect-publisher-transact-sql.md)   
 [sp_validate_replica_hosts_as_publishers &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
