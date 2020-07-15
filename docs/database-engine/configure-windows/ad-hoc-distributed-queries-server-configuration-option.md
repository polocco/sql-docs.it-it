---
title: Opzione di configurazione del server ad hoc distributed queries | Microsoft Docs
description: Informazioni su come abilitare le query distribuite ad hoc in SQL Server. È quindi possibile usare OPENROWSET e OPENDATASOURCE per connettersi alle origini dati OLE DB remote.
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- OPENROWSET function, ad hoc distributed queries option
- Ad Hoc Distributed Queries option
- ad hoc distributed queries
- 7415 (Database Engine Error)
- OPENDATASOURCE function, ad hoc distributed queries option
- ad hoc access
ms.assetid: 5b982015-e196-44c3-83b8-275fb9d769b2
author: markingmyname
ms.author: maghan
ms.openlocfilehash: d05a89446b42feb09d46f1b407991226a7d234db
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85698268"
---
# <a name="ad-hoc-distributed-queries-server-configuration-option"></a>Opzione di configurazione del server ad hoc distributed queries
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Per impostazione predefinita, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non prevede l'utilizzo query distribuite ad hoc contenenti le funzioni OPENROWSET e OPENDATASOURCE. Quando questa opzione è impostata su 1, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è possibile l'accesso ad hoc. Quando questa opzione non è impostata o è impostata su 0, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è possibile l'accesso ad hoc.  
  
 Le query distribuite ad hoc utilizzano le funzioni OPENROWSET e OPENDATASOURCE per connettersi alle origini dei dati remote che utilizzano OLE DB. È consigliabile utilizzare le funzioni OPENROWSET e OPENDATASOURCE solo per fare riferimento a origini dei dati OLE DB a cui si accede raramente. Per le origini dei dati a cui è necessario accedere con maggiore frequenza, è possibile definire un server collegato.  
  
> [!IMPORTANT]  
>  Se si consente l'utilizzo dei nomi ad hoc, tutti gli account di accesso a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autenticati potranno accedere al provider. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] richiede che gli amministratori abilitino questa funzionalità per i provider a cui è possibile accedere in modo sicuro tramite qualsiasi account di accesso locale.  
  
## <a name="remarks"></a>Osservazioni  
 Se si prova a eseguire una connessione ad hoc con l'opzione **Query distribuite ad hoc abilitate** non abilitata, viene restituito l'errore: Messaggio 7415, livello 16, stato 1, riga 1  
  
 L'accesso ad hoc al provider OLE DB "Microsoft.ACE.OLEDB.12.0" è stato negato. Accedere al provider tramite un server collegato.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene abilitata l'opzione ad hoc distributed queries e, successivamente, viene eseguita una query su un server denominato `Seattle1` utilizzando la funzione `OPENROWSET` .  
  
```  
sp_configure 'show advanced options', 1;  
RECONFIGURE;
GO 
sp_configure 'Ad Hoc Distributed Queries', 1;  
RECONFIGURE;  
GO  
  
SELECT a.*  
FROM OPENROWSET('SQLNCLI', 'Server=Seattle1;Trusted_Connection=yes;',  
     'SELECT GroupName, Name, DepartmentID  
      FROM AdventureWorks2012.HumanResources.Department  
      ORDER BY GroupName, Name') AS a;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Server collegati &#40;Motore di database&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)   
 [OPENDATASOURCE &#40;Transact-SQL&#41;](../../t-sql/functions/opendatasource-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)  
  
  
