---
description: VERSION - Funzioni per i metadati di Transact SQL
title: VERSION (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 95a79b33-98f2-4929-a1a5-93b522a9e152
author: julieMSFT
ms.author: jrasnick
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 1866248cf8f60f55ab0fd0d809c1ce55f7d24f59
ms.sourcegitcommit: 197a6ffb643f93592edf9e90b04810a18be61133
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/26/2020
ms.locfileid: "91380526"
---
# <a name="version---transact-sql-metadata-functions"></a>VERSION - Funzioni per i metadati di Transact SQL
[!INCLUDE[applies-to-version/asa-pdw](../../includes/applies-to-version/asa-pdw.md)]

 Restituisce la versione di [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] o [!INCLUDE[ssPDW_md](../../includes/sspdw-md.md)] in esecuzione nell'appliance.  
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```syntaxsql
-- Azure Synapse Analytics and Parallel Data Warehouse  
VERSION ( )  
```  
  
## <a name="arguments"></a>Argomenti  
  
## <a name="general-remarks"></a>Osservazioni generali  
Perché questa funzione restituisca risultati, è necessario specificare un nome di tabella in una clausola [FROM](../../t-sql/queries/from-transact-sql.md). Verrà restituita una riga di risultati per ogni riga del set di risultati per la query. Usare [TOP (Transact-SQL)](../../t-sql/queries/top-transact-sql.md) per limitare il numero di righe restituite.  
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente viene restituito il numero di versione.  
  
```sql
SELECT VERSION();  
```  
  
## <a name="see-also"></a>Vedere anche 
[SESSION_ID (Transact-SQL)](../../t-sql/functions/session-id-transact-sql.md)  
[DB_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/db-name-transact-sql.md)  
  
  
