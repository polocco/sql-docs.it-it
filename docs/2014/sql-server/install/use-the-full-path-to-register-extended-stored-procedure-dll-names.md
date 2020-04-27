---
title: Usare il percorso completo per registrare i nomi delle DLL di stored procedure estese | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- registering DLL names
- extended stored procedures [SQL Server], registering
- DLL names [SQL Server]
- full path DLL name registration [SQL Server]
ms.assetid: f648d57c-af32-4c71-9882-47b6766f3c2b
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e560ec0fd617d4da46235803da8cbd69ef4f80d5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66091286"
---
# <a name="use-the-full-path-to-register-extended-stored-procedure-dll-names"></a>Utilizzare il percorso completo per registrare i nomi delle DLL delle stored procedure estese
  Le stored procedure estese registrate precedentemente senza il percorso completo per il nome DLL possono non funzionare dopo l'aggiornamento a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Descrizione  
 Le stored procedure estese registrate precedentemente senza il percorso completo per il nome DLL possono non funzionare dopo l'aggiornamento, poiché la vecchia directory BINN non viene aggiunta al nuovo percorso durante il processo di aggiornamento. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può non essere in grado di trovare le stored procedure estese.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Prima di eseguire l'aggiornamento, attenersi alla procedura seguente per ogni stored procedure estesa non registrata utilizzando un percorso completo:  
  
1.  Per eliminare la stored procedure estesa eseguire sp_dropextendedproc.  
  
2.  Per registrare la stored procedure estesa con il percorso completo eseguire sp_addextendedproc.  
  
## <a name="see-also"></a>Vedi anche  
 [Problemi di aggiornamento motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 preparazione aggiornamento &#91;nuova&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
