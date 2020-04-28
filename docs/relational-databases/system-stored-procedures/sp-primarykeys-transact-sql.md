---
title: sp_primarykeys (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_primarykeys_TSQL
- sp_primarykeys
dev_langs:
- TSQL
helpviewer_keywords:
- sp_primarykeys
ms.assetid: 0f76dd31-5b7b-4209-9e2e-b9ed5cac164d
author: stevestein
ms.author: sstein
ms.openlocfilehash: ccae0385ef8c9305f4972ff6dcbd7a7960200370
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "68056312"
---
# <a name="sp_primarykeys-transact-sql"></a>sp_primarykeys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce le colonne chiave primaria (una riga per ogni colonna chiave) per la tabella remota specificata.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_primarykeys [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_catalog' ]  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @table_server = ] 'table_server'_`Nome del server collegato da cui si desidera ottenere informazioni sulla chiave primaria. *table_server* è di **tipo sysname**e non prevede alcun valore predefinito.  
  
`[ @table_name = ] 'table_name'`Nome della tabella per cui si desidera ottenere informazioni sulla chiave primaria. *table_name*è di **tipo sysname**e il valore predefinito è null.  
  
`[ @table_schema = ] 'table_schema'`Schema della tabella. *TABLE_SCHEMA* è di **tipo sysname**e il valore predefinito è null. In ambiente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] corrisponde al proprietario della tabella.  
  
`[ @table_catalog = ] 'table_catalog'`Nome del catalogo in cui risiede il *table_name* specificato. In ambiente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] corrisponde al nome del database. *TABLE_CATALOG* è di **tipo sysname**e il valore predefinito è null.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 nessuno  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Catalogo della tabella.|  
|**TABLE_SCHEM**|**sysname**|Schema della tabella.|  
|**TABLE_NAME**|**sysname**|Nome della tabella.|  
|**COLUMN_NAME**|**sysname**|Nome della colonna.|  
|**KEY_SEQ**|**int**|Numero sequenziale della colonna in una chiave primaria a più colonne.|  
|**PK_NAME**|**sysname**|Identificatore della chiave primaria. Se non è applicabile all'origine dei dati, restituisce NULL.|  
  
## <a name="remarks"></a>Osservazioni  
 **sp_primarykeys** viene eseguita eseguendo una query sul set di righe PRIMARY_KEYS dell'interfaccia **IDBSchemaRowset** del provider di OLE DB corrispondente a *table_server*. I parametri *table_name*, *TABLE_SCHEMA*, *TABLE_CATALOG*e *Column* vengono passati a questa interfaccia per limitare le righe restituite.  
  
 **sp_primarykeys** restituisce un set di risultati vuoto se il provider di OLE DB del server collegato specificato non supporta il set di righe PRIMARY_KEYS dell'interfaccia **IDBSchemaRowset** .  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione SELECT per lo schema.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituite le colonne chiave primaria dal server `LONDON1` per la tabella `HumanResources.JobCandidate` nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC sp_primarykeys @table_server = N'LONDON1',   
   @table_name = N'JobCandidate',  
   @table_catalog = N'AdventureWorks2012',   
   @table_schema = N'HumanResources';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure per query distribuite &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_catalogs &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_column_privileges &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_foreignkeys &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_indexes &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_tables_ex &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [sp_table_privileges &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
