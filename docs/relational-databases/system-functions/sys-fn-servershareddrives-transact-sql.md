---
description: sys.fn_servershareddrives (Transact-SQL)
title: sys.fn_servershareddrives (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_servershareddrives
- fn_servershareddrives_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_servershareddrives function
- shared drives [SQL Server]
- names [SQL Server], shared drives
- sys.fn_serversharedrives function
ms.assetid: ff01eff7-8cb6-460c-ba7a-6a52bda6d471
author: rothja
ms.author: jroth
ms.openlocfilehash: d3fa98a1e24e20469da6fd39bf64db61451582d3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88474625"
---
# <a name="sysfn_servershareddrives-transact-sql"></a>sys.fn_servershareddrives (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Restituisce i nomi delle unità condivise utilizzate dal server del cluster.  
  
> [!IMPORTANT]  
>  Questa funzione di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è inclusa per garantire la compatibilità con le versioni precedenti. Si consiglia di utilizzare [sys. dm_io_cluster_valid_path_names &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql.md) .  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
fn_servershareddrives()  
```  
  
## <a name="tables-returned"></a>Tabelle restituite  
 Se il server corrente è un server del cluster, **fn_servershareddrives** restituisce il nome dell'unità delle unità condivise.  
  
 Se l'istanza del server corrente non è un server cluster, **fn_servershareddrives** restituisce un set di righe vuoto.  
  
## <a name="remarks"></a>Osservazioni  
 La funzione `fn_servershareddrives` restituisce l'elenco delle unità condivise utilizzate dal server del cluster corrente. Queste unità condivise appartengono allo stesso gruppo di cluster della [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] risorsa. A sua volta, la risorsa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dipende da queste unità.  
  
 Questa funzione risulta utile per l'identificazione delle unità disponibili agli utenti.  
  
## <a name="permissions"></a>Autorizzazioni  
 L'utente deve disporre dell'autorizzazione VIEW SERVER STATE per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente la funzione `fn_servershareddrives` viene utilizzata per eseguire una query su un'istanza del server del cluster.  
  
```  
SELECT * FROM fn_servershareddrives();  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 DriveName  
  
 -------\-  
  
 m  
  
 n  
  
## <a name="see-also"></a>Vedere anche  
 [sys. dm_io_cluster_valid_path_names &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql.md)   
 [sys. dm_io_cluster_shared_drives &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-shared-drives-transact-sql.md)   
 [sys.fn_virtualservernodes &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-virtualservernodes-transact-sql.md)  
  
  
