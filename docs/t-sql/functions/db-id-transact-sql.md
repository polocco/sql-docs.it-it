---
title: DB_ID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/13/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DB_ID_TSQL
- DB_ID
dev_langs:
- TSQL
helpviewer_keywords:
- viewing database ID numbers
- IDs [SQL Server], databases
- database IDs [SQL Server]
- identification numbers [SQL Server], databases
- displaying database ID numbers
- DB_ID function
ms.assetid: 7b3aef89-a6fd-4144-b468-bf87ebf381b8
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 56408c607d9e1ecf5b03fc3bd135d0eae706c9e3
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86007609"
---
# <a name="db_id-transact-sql"></a>DB_ID (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Questa funzione restituisce il numero di identificazione (ID) di un database specificato.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DB_ID ( [ 'database_name' ] )   
```  
  
## <a name="arguments"></a>Argomenti  
'*database_name*'  
Nome del database il cui numero di ID database verrà restituito da `DB_ID`. Se la chiamata a `DB_ID` omette *database_name*, `DB_ID` restituisce l'ID del database corrente.
  
## <a name="return-types"></a>Tipi restituiti
**int**

## <a name="remarks"></a>Osservazioni
`DB_ID` può essere usato solo per restituire l'identificatore del database corrente nel database SQL di Azure. Se il nome del database specificato è diverso da quello del database corrente, viene restituito NULL.

> [!NOTE]
> Se usato con il database SQL di Azure, `DB_ID` potrebbe non restituire lo stesso risultato della query di `database_id` da **sys.databases**. Se il chiamante di `DB_ID` confronta il risultato con altre viste **sys**, è necessario eseguire una query su **sys.databases**.
  
## <a name="permissions"></a>Autorizzazioni  
Se il chiamante di `DB_ID` non è proprietario di un database non **master** o non **tempdb** specifico, sono necessarie almeno le autorizzazioni a livello di server `ALTER ANY DATABASE` o `VIEW ANY DATABASE` per visualizzare la riga `DB_ID` corrispondente. Per il database **master**, `DB_ID` necessita almeno dell'autorizzazione `CREATE DATABASE`. Il database a cui si connette il chiamante verrà sempre visualizzato in **sys.databases**.
  
> [!IMPORTANT]  
>  Per impostazione predefinita, il ruolo public ha l'autorizzazione `VIEW ANY DATABASE`, che consente a tutti gli account di accesso di visualizzare informazioni sul database. Per impedire a un account di accesso di rilevare un database, usare `REVOKE` per revocare l'autorizzazione `VIEW ANY DATABASE` da public o `DENY` per negare l'autorizzazione `VIEW ANY DATABASE` per i singoli account di accesso.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-the-database-id-of-the-current-database"></a>R. Restituzione dell'ID del database corrente  
Questo esempio restituisce l'ID del database corrente.
  
```sql
SELECT DB_ID() AS [Database ID];  
GO  
```  
  
### <a name="b-returning-the-database-id-of-a-specified-database"></a>B. Restituzione dell'ID di un database specifico  
Questo esempio restituisce l'ID del database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].
  
```sql
SELECT DB_ID(N'AdventureWorks2008R2') AS [Database ID];  
GO  
```  
  
### <a name="c-using-db_id-to-specify-the-value-of-a-system-function-parameter"></a>C. Utilizzo di DB_ID per specificare il valore di un parametro di una funzione di sistema  
Questo esempio usa l'istruzione `DB_ID` per restituire l'ID del database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] nella funzione di sistema `sys.dm_db_index_operational_stats`. La funzione utilizza un ID di database come primo parametro.
  
```sql
DECLARE @db_id int;  
DECLARE @object_id int;  
SET @db_id = DB_ID(N'AdventureWorks2012');  
SET @object_id = OBJECT_ID(N'AdventureWorks2012.Person.Address');  
IF @db_id IS NULL   
  BEGIN;  
    PRINT N'Invalid database';  
  END;  
ELSE IF @object_id IS NULL  
  BEGIN;  
    PRINT N'Invalid object';  
  END;  
ELSE  
  BEGIN;  
    SELECT * FROM sys.dm_db_index_operational_stats(@db_id, @object_id, NULL, NULL);  
  END;  
GO  
```  
  
## <a name="examples-sssdwfull-and-sspdw"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-return-the-id-of-the-current-database"></a>D. Restituire l'ID del database corrente  
Questo esempio restituisce l'ID del database corrente.
  
```sql
SELECT DB_ID();  
```  
  
### <a name="e-return-the-id-of-a-named-database"></a>E. Restituire l'ID di un database denominato.  
Questo esempio restituisce l'ID del database AdventureWorksDW2012.
  
```sql
SELECT DB_ID('AdventureWorksPDW2012');  
```  
  
## <a name="see-also"></a>Vedere anche
[DB_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/db-name-transact-sql.md)  
[Funzioni per i metadati &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)  
[sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
[sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)
  
  

