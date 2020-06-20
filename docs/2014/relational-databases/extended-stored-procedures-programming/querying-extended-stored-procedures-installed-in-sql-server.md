---
title: Esecuzione di query su stored procedure estese installate in SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], querying
ms.assetid: e02348e6-dba6-438a-98b6-684244bb034d
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f44db9053ad18c3a6902a30aaab4f81610c5a8c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050833"
---
# <a name="querying-extended-stored-procedures-installed-in-sql-server"></a>Esecuzione di query su stored procedure estese installate in SQL Server
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utente autenticato può visualizzare le stored procedure estese attualmente definite e il nome della dll a cui appartiene, eseguendo la procedura **sp_helpextendedproc** sistema. Nell'esempio seguente viene restituita la DLL a cui appartiene **xp_hello** :  
  
```  
sp_helpextendedproc 'xp_hello'  
```  
  
 Se **sp_helpextendedproc** viene eseguita senza specificare una stored procedure estesa, vengono visualizzate tutte le stored procedure estese e le relative dll.  
  
> [!IMPORTANT]  
>  Verranno restituite le informazioni solo per le stored procedure estese di cui l'utente connesso è il proprietario o di cui dispone delle autorizzazioni appropriate. Solo i membri del ruolo predefinito del server **sysadmin** e del **db_owner**, **db_securityadmin**e i ruoli predefiniti del database **db_ddladmin** possono visualizzare le informazioni relative a tutte le stored procedure estese.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_helpextendedproc &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql)   
 [sp_addextendedproc &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
