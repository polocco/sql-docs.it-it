---
title: IS_OBJECTSIGNED (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- IS_OBJECTSIGNED
- IS_OBJECTSIGNED_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IS_OBJECTSIGNED function
ms.assetid: afbc4f7f-8266-4ee6-9802-14a2dbe69ef6
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 94434e3b8e70a7715a3471c04c3dd569172019b1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85784533"
---
# <a name="is_objectsigned-transact-sql"></a>IS_OBJECTSIGNED (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Indica se un oggetto viene firmato da una chiave asimmetrica o da un certificato specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
IS_OBJECTSIGNED (   
'OBJECT', @object_id, @class, @thumbprint  
  )   
```  
  
## <a name="arguments"></a>Argomenti  
 **'OBJECT'**  
 Tipo di classe a protezione diretta.  
  
 *\@object_id*  
 object_id dell'oggetto sottoposto a test. *\@object_id* è di tipo **int**.  
  
 *\@class*  
 Classe dell'oggetto.  
  
-   'certificate'  
  
-   'asymmetric key'  
  
 *\@class* è **sysname**.  
  
 *\@thumbprint*  
 Identificazione digitale SHA dell'oggetto. *\@thumbprint* è di tipo **varbinary(32)** .  
  
## <a name="returned-types"></a>Tipi restituiti  
 **int**  
  
## <a name="remarks"></a>Osservazioni  
 IS_OBJECTSIGNED restituisce i valori seguenti.  
  
|Valore restituito|Descrizione|  
|------------------|-----------------|  
|NULL|L'oggetto non è firmato oppure non è valido.|  
|0|L'oggetto è firmato, ma la firma non è valida.|  
|1|L'oggetto viene firmato.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW DEFINITION per il certificato o la chiave asimmetrica.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-displaying-extended-properties-on-a-database"></a>R. Visualizzazione delle proprietà estese in un database  
 L'esempio seguente verifica se la tabella spt_fallback_db del database **master** è firmata dal certificato di firma dello schema.  
  
```  
USE master;  
-- Declare a variable to hold a thumbprint and an object name  
DECLARE @thumbprint varbinary(20), @objectname sysname;  
  
-- Populate the thumbprint variable with the thumbprint of   
-- the master database schema signing certificate  
SELECT @thumbprint = thumbprint   
FROM sys.certificates   
WHERE name LIKE '%SchemaSigningCertificate%';  
  
-- Populate the object name variable with a table name in master  
SELECT @objectname = 'spt_fallback_db';  
  
-- Query to see if the table is signed by the thumbprint  
SELECT @objectname AS [object name],  
IS_OBJECTSIGNED(  
'OBJECT', OBJECT_ID(@objectname), 'certificate', @thumbprint  
) AS [Is the object signed?] ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sys.fn_check_object_signatures &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-check-object-signatures-transact-sql.md)  
  
  
