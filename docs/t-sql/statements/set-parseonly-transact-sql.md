---
title: SET PARSEONLY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- PARSEONLY_TSQL
- SET_PARSEONLY_TSQL
- PARSEONLY
- SET PARSEONLY
dev_langs:
- TSQL
helpviewer_keywords:
- parsing [SQL Server], SET PARSEONLY statement
- checking syntax
- PARSEONLY option
- syntax [SQL Server], verifying
- verifying syntax
- SET PARSEONLY statement
ms.assetid: 514ab042-c53e-4d96-be71-fb08fcc6ef3c
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 69d2027a590c2e01a409460bce153a850740f36e
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87395096"
---
# <a name="set-parseonly-transact-sql"></a>SET PARSEONLY (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Esamina la sintassi di ogni istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] e restituisce eventuali messaggi di errore senza compilare o eseguire l'istruzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```syntaxsql
  
SET PARSEONLY { ON | OFF }  
```  
  
## <a name="remarks"></a>Osservazioni  
 Quando l'opzione SET PARSEONLY è impostata su ON, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esegue soltanto l'analisi dell'istruzione. Quando l'opzione SET PARSEONLY è impostata su OFF, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compila ed esegue l'istruzione.  
  
 L'opzione SET PARSEONLY viene impostata in fase di analisi, non in fase di esecuzione.  
  
 Non utilizzare l'opzione PARSEONLY in una stored procedure o in un trigger. SET PARSEONLY restituisce valori di offset se l'opzione OFFSETS è impostata su ON e non si verificano errori.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET OFFSETS &#40;Transact-SQL&#41;](../../t-sql/statements/set-offsets-transact-sql.md)  
  
  
