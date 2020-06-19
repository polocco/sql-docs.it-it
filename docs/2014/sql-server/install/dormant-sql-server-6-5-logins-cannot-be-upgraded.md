---
title: Non è possibile aggiornare gli account di accesso SQL Server 6,5 inattivi | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- passwords [SQL Server], dormant logins
- dormant logins
- logins [SQL Server], upgrading dormant logins
- identifying dormant logins
- password hashes [SQL Server]
ms.assetid: ebe18a74-0375-4df4-b894-239f8fdabb64
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: f78bca9bf2b99b2ab6f530613b64bc0e46c4001c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054823"
---
# <a name="dormant-sql-server-65-logins-cannot-be-upgraded"></a>Impossibile aggiornare gli account di accesso di SQL Server 6.5 inattivi
  Preparazione aggiornamento ha rilevato un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la cui password non può essere direttamente aggiornata a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Per attivare questo account di accesso, è necessario reimpostarne la password. Utilizzare ALTER LOGIN per reimpostare la password.  
  
```  
ALTER LOGIN <login name> WITH PASSWORD = '<new password>' MUST_CHANGE  
```  
  
 La nuova password verrà convalidata in base ai criteri di complessità delle password del sistema, a meno che il controllo dei criteri non sia disabilitato. È consigliabile utilizzare password complesse e non disabilitare il controllo dei criteri. L'opzione MUST_CHANGE impone all'utente la selezione di una nuova password. Tale procedura non è necessaria ma è consigliabile.  
  
 Per identificare gli account di accesso inattivi utilizzare la query seguente:  
  
```  
SELECT * FROM sysxlogins WHERE (xstatus & 2048) = 2048;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 preparazione aggiornamento &#91;nuova&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
