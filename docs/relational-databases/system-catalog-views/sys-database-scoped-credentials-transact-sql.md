---
title: sys. database_scoped_credentials (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.database_scoped_credentials
- sys.database_scoped_credentials_TSQL
- database_scoped_credentials
- database_scoped_credentials_TSQL
helpviewer_keywords:
- sys.database_scoped_credentials catalog view
ms.assetid: 68e8aa6b-bcdc-42aa-93d8-d498f724c188
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 03687ea50b04c96aa4dbafab9d02d2bbc33a14b3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "68079419"
---
# <a name="sysdatabase_scoped_credentials-transact-sql"></a>sys. database_scoped_credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Restituisce una riga per ogni credenziale con ambito database nel database.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|name|**sysname**|Nome delle credenziali con ambito database. È univoco nel database.|  
|credential_id|**int**|ID delle credenziali con ambito database. È univoco nel database.|  
|principal_id|**int**|ID dell'entità di database proprietaria della sottoscrizione.|  
|credential_identity|**nvarchar(4000)**|Nome dell'identità da utilizzare, in genere corrispondente a un utente di Windows. Non è necessario che sia univoco.|  
|create_date|**datetime**|Ora in cui è stata creata la credenziale con ambito database.|  
|modify_date|**datetime**|Ora dell'Ultima modifica delle credenziali con ambito database.|  
|target_type|**nvarchar (100)**|Tipo di credenziali con ambito database. Restituisce `NULL` per le credenziali con ambito database.|  
|target_id|**int**|ID dell'oggetto a cui è stato eseguito il mapping della credenziale con ambito database. Restituisce 0 per le credenziali con ambito database|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione `CONTROL` per il database.  
  
## <a name="see-also"></a>Vedere anche  
 [Credenziali &#40;motore di database&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREAZIONE di credenziali con ambito DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [ALTER DATABASE SCOPEd CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [DROP DATABASE SCOPEd CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [CREAZIONE di credenziali &#40;&#41;Transact-SQL](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
