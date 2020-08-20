---
description: sysmail_help_configure_sp (Transact-SQL)
title: sysmail_help_configure_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_configure_sp
- sysmail_help_configure_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_configure_sp
ms.assetid: e598d4c8-3041-4965-b046-dce3a8e3d3e0
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c030fbc4ee2c329f8c13e525c07961794b28608e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88488959"
---
# <a name="sysmail_help_configure_sp-transact-sql"></a>sysmail_help_configure_sp (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Visualizza le impostazioni di configurazione per Posta elettronica database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sysmail_help_configure_sp  [ [ @parameter_name = ] 'parameter_name' ]  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @parameter_name = ] 'parameter_name'` Nome dell'impostazione di configurazione da recuperare. Quando specificato, il valore dell'impostazione di configurazione viene restituito nel parametro di output ** \@ parameter_value** . Quando non viene specificato alcun ** \@ parameter_name** , questo stored procedure restituisce un set di risultati contenente tutte le impostazioni di configurazione posta elettronica database nell'istanza di.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Quando non viene specificato alcun ** \@ parameter_name** , restituisce un set di risultati con le colonne seguenti.  
  
| Nome colonna | Tipo di dati | Descrizione |
| ----------- | --------- | ----------- |
|**paramName**|**nvarchar(256)**|Nome del parametro di configurazione.|  
|**paramValue**|**nvarchar(256)**|Valore del parametro di configurazione.|  
|**description**|**nvarchar(256)**|Descrizione del parametro di configurazione.|  
  
## <a name="remarks"></a>Osservazioni  
 Nell'stored procedure **sysmail_help_configure_sp** sono elencate le impostazioni di configurazione posta elettronica database correnti per l'istanza di.  
  
 Quando si specifica un ** \@ parameter_name** , ma non viene fornito alcun parametro di output per ** \@ parameter_value**, questo stored procedure non produce alcun output.  
  
 Il stored procedure **sysmail_help_configure_sp** si trova nel database **msdb** ed è di proprietà dello schema **dbo** . La procedura deve essere richiamata con un nome in tre parti se il database corrente non è **msdb**.  
  
## <a name="permissions"></a>Autorizzazioni  
 Le autorizzazioni di esecuzione per questa procedura vengono assegnate per impostazione predefinita ai membri del ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono visualizzate le impostazioni di configurazione di Posta elettronica database per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
EXECUTE msdb.dbo.sysmail_help_configure_sp ;  
```  
  
 Quello che segue è un set di risultati di esempio, modificato per adattarlo alla lunghezza di riga.  
  
```  
paramname                       paramvalue      description  
------------------------------- --------------- -----------------------------------------------------------------------------  
AccountRetryAttempts            1               Number of retry attempts for a mail server  
AccountRetryDelay               5000            Delay between each retry attempt to mail server  
DatabaseMailExeMinimumLifeTime  600             Minimum process lifetime in seconds  
DefaultAttachmentEncoding       MIME            Default attachment encoding  
LoggingLevel                    2               Database Mail logging level: normal - 1, extended - 2 (default), verbose - 3  
MaxFileSize                     1000000         Default maximum file size  
ProhibitedExtensions            exe,dll,vbs,js  Extensions not allowed in outgoing mails  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Posta elettronica database](../../relational-databases/database-mail/database-mail.md)   
 [Stored procedure di Posta elettronica database &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
