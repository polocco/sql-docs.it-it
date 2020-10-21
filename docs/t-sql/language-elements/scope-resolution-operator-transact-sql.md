---
description: ":: (risoluzione dell'ambito) (Transact-SQL)"
title: ":: (risoluzione dell'ambito) (Transact-SQL) | Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 764d8f91-957b-4037-997b-a9b6b533c504
author: rothja
ms.author: jroth
ms.openlocfilehash: 6c319d0e7e67605f09954e88434842be9b8ae1df
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2020
ms.locfileid: "92195464"
---
# <a name="-scope-resolution-transact-sql"></a>:: (risoluzione dell'ambito) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  L'operatore di risoluzione dell'ambito **::** fornisce l'accesso ai membri statici di un tipo di dati composto. Un tipo di dati composito contiene più metodi e tipi di dati semplici. I tipi di dati compositi includono i tipi CLR predefiniti e i tipi definiti dall'utente SQLCLR.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene indicato come utilizzare l'operatore di risoluzione dell'ambito per accedere al membro `GetRoot()` di tipo `hierarchyid`.  
  
```sql  
DECLARE @hid hierarchyid;  
SELECT @hid = hierarchyid::GetRoot();  
PRINT @hid.ToString();  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `/`  
  
## <a name="see-also"></a>Vedere anche  
 [Operatori &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)  
 
