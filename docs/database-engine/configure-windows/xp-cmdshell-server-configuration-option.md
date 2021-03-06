---
title: Opzione di configurazione del server xp_cmdshell
description: Informazioni sull'opzione "xp_cmdshell". Scoprire come controlla se SQL Server può eseguire la stored procedure estesa "xp_cmdshell". Informazioni su come attivarla.
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- xp_cmdshell
ms.assetid: c147c9e1-b81d-49c8-b800-3019f4d86a13
author: markingmyname
ms.author: maghan
ms.custom: contperfq4
ms.date: 06/12/2020
ms.openlocfilehash: b2d4364d01b871364fda3ac42d98536e99269c29
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85763943"
---
# <a name="xp_cmdshell-server-configuration-option"></a>Opzione di configurazione del server xp_cmdshell

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Questo articolo descrive come abilitare l'opzione di configurazione di SQL Server **xp_cmdshell**. Questa opzione consente agli amministratori di sistema di controllare se la [stored procedure xp_cmdshell](../../relational-databases/system-stored-procedures/xp-cmdshell-transact-sql.md) può essere eseguita in un sistema. Per impostazione predefinita, nelle nuove installazioni l'opzione **xp_cmdshell** risulta disabilitata.

Prima di abilitare questa opzione, è importante prendere in considerazione le potenziali implicazioni per la sicurezza.

- Si consiglia di non usare la stored procedure **xp_cmdshell** nel nuovo codice sviluppato e in generale deve essere lasciata disabilitata.
- Per alcune applicazioni legacy è necessario abilitare **xp_cmdshell**. Se non possono essere modificate per evitare l'uso di questa stored procedure, è possibile abilitarla come descritto di seguito.

Se è necessario abilitare **xp_cmdshell**, è possibile usare la [gestione basata su criteri](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md) o eseguire la stored procedure di sistema **sp_configure**, come illustrato nell'esempio di codice seguente:  
  
``` sql
-- To allow advanced options to be changed.  
EXECUTE sp_configure 'show advanced options', 1;  
GO  
-- To update the currently configured value for advanced options.  
RECONFIGURE;  
GO  
-- To enable the feature.  
EXECUTE sp_configure 'xp_cmdshell', 1;  
GO  
-- To update the currently configured value for this feature.  
RECONFIGURE;  
GO  
```  
  
## <a name="next-steps"></a>Passaggi successivi

- [Stored procedure estesa xp_cmdshell](../../relational-databases/system-stored-procedures/xp-cmdshell-transact-sql.md)
- [Opzioni di configurazione del server (SQL Server)](server-configuration-options-sql-server.md)
- [Amministrazione di server tramite la gestione basata su criteri](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
