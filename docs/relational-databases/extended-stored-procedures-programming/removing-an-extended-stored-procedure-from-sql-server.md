---
description: Rimozione di una stored procedure estesa da SQL Server
title: Rimozione di una stored procedure estesa
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- deleting extended stored procedures
- removing extended stored procedures
- extended stored procedures [SQL Server], removing
- dropping extended stored procedures
ms.assetid: 7827e574-3f59-4279-9a9b-532582e041cb
author: rothja
ms.author: jroth
ms.custom: seo-dt-2019
ms.openlocfilehash: d7296391a9105c9831ed8652f7b63e234ac4f6df
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88460768"
---
# <a name="removing-an-extended-stored-procedure-from-sql-server"></a>Rimozione di una stored procedure estesa da SQL Server
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilizzare invece la funzionalità di integrazione con CLR.  
  
 Per eliminare ogni funzione di stored procedure estesa in una DLL di stored procedure estesa definita dall'utente, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è necessario che un amministratore di sistema esegua il stored procedure di sistema **sp_dropextendedproc** , specificando il nome della funzione e il nome della dll in cui risiede la funzione. Ad esempio, questo comando rimuove la funzione **xp_hello**, che si trova in una DLL denominata xp_hello.dll, da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
```  
sp_dropextendedproc 'xp_hello'  
```  
  
 A partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , **sp_dropextendedproc** non elimina le stored procedure estese di sistema. L'amministratore di sistema deve invece negare l'autorizzazione EXECUTE per il stored procedure esteso al ruolo **public** .  
  
## <a name="see-also"></a>Vedere anche  
 [sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
  
  
