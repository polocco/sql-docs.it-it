---
title: sys. fn_PageResCracker (Transact-SQL) | Microsoft Docs
description: Informazioni sulla funzione di sistema sys. fn_PageResCracker. Vedere gli esempi e visualizzare altre risorse disponibili.
ms.custom: ''
ms.date: 09/18/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_PageResCracker
- sys.fn_PageResCracker_TSQL
- fn_PageResCracker_TSQL
- sys.fn_PageResCracker
- sys.dm_db_page_info
dev_langs:
- TSQL
helpviewer_keywords:
- fn_PageResCracker function
- page_resource
- sys.fn_PageResCracker function
- sys.dm_db_page_info
- page info
author: bluefooted
ms.author: pamela
manager: amitban
ms.openlocfilehash: a48b5ba06223130a83980bf6cf8ec410bd58e5a1
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/28/2020
ms.locfileid: "87247580"
---
# <a name="sysfn_pagerescracker-transact-sql"></a>sys. fn_PageResCracker (Transact-SQL)
[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

Restituisce `db_id` , `file_id` e `page_id` per il `page_resource` valore specificato. 
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
```  
sys.fn_PageResCracker ( page_resource )  
```  
  
## <a name="arguments"></a>Argomenti  
*page_resource*    
Formato esadecimale a 8 byte di una risorsa della pagina del database.
  
## <a name="tables-returned"></a>Tabelle restituite  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|db_id|**int**|ID database|  
|file_id|**int**|ID file|  
|page_id|**int**|ID pagina|  
  
## <a name="remarks"></a>Commenti  
`sys.fn_PageResCracker`viene utilizzato per convertire la rappresentazione esadecimale a 8 byte di una pagina di database in un set di righe che contiene l'ID del database, l'ID file e l'ID pagina della pagina.   

È possibile ottenere una risorsa di pagina valida dalla `page_resource` colonna della vista a gestione dinamica [sys. Dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md) o dai [processisys.sys&#40;vista di sistema Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md) . Se viene usata una risorsa di pagina non valida, il valore restituito è NULL.  
L'utilizzo principale di `sys.fn_PageResCracker` consiste nel semplificare i join tra queste viste e [sys. Dm_db_page_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md) funzione a gestione dinamica per ottenere informazioni sulla pagina, ad esempio l'oggetto a cui appartiene.
  
## <a name="permissions"></a>Autorizzazioni  
L'utente deve disporre dell' `VIEW SERVER STATE` autorizzazione per il server.  
  
## <a name="examples"></a>Esempio  
La `sys.fn_PageResCracker` funzione può essere utilizzata insieme a [sys. dm_db_page_info &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md) per risolvere i problemi relativi alle attese e al blocco correlati alle pagine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  Lo script seguente è un esempio di come è possibile usare queste funzioni per raccogliere informazioni sulla pagina del database per tutte le richieste attive attualmente in attesa di un tipo di risorsa di pagina. 
  
```sql  
SELECT page_info.* 
FROM sys.dm_exec_requests AS d  
CROSS APPLY sys.fn_PageResCracker (d.page_resource) AS r  
CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id, 1) AS page_info
```  
  
## <a name="see-also"></a>Vedere anche  
 [sys. dm_db_page_info &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md)  
 [Processi disys.sys&#40;&#41;Transact-SQL](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
  
