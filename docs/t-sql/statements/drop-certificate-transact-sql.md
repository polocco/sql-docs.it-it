---
title: DROP CERTIFICATE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/18/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP CERTIFICATE
- DROP_CERTIFICATE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- certificates [SQL Server], removing
- removing certificates
- dropping certificates
- DROP CERTIFICATE statement
- deleting certificates
ms.assetid: 5704aa04-68a3-4b29-b62b-8868af487817
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 53f8461051c02b5046bd15c385acbfffe796047e
ms.sourcegitcommit: edba1c570d4d8832502135bef093aac07e156c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/20/2020
ms.locfileid: "86484938"
---
# <a name="drop-certificate-transact-sql"></a>DROP CERTIFICATE (Transact-SQL)
[!INCLUDE [sql-asdb-asa-pdw](../../includes/applies-to-version/sql-asdb-asa-pdw.md)]

  Rimuove un certificato dal database.  
  
> [!IMPORTANT]  
>  Il backup del certificato utilizzato per la crittografia del database deve essere conservato anche se la crittografia non è più abilitata in un database. Anche se il database non viene più crittografato, è possibile che parti del log delle transazioni restino comunque protette e che il certificato sia necessario per alcune operazioni per l'esecuzione del backup completo del database. Il certificato viene richiesto anche per ripristinare i backup creati con il database crittografato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md) 

  
> [!Note]
> [!INCLUDE [Synapse preview note](../../includes/synapse-preview-note.md)]
  
## <a name="syntax"></a>Sintassi  
  
```synaxsql  
DROP CERTIFICATE certificate_name  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argomenti
 *certificate_name*  
 Nome univoco con il quale il certificato è noto nel database.  
  
## <a name="remarks"></a>Osservazioni  
 I certificati possono essere eliminati solo se a essi non sono associate entità.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione CONTROL per il certificato.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene eliminato il certificato `Shipping04` dal database `AdventureWorks`.  
  
```  
USE AdventureWorks2012;  
DROP CERTIFICATE Shipping04;  
```  
  
## <a name="examples-sspdw"></a>Esempi: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Nell'esempio seguente viene eliminato il certificato `Shipping04`.  
  
```
USE master;  
DROP CERTIFICATE Shipping04;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [Gerarchia di crittografia](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)
