---
title: Funzioni per i cursori (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], cursors
- cursor functions
ms.assetid: 7d9daa10-4c50-4212-9400-42120222b2b8
author: markingmyname
ms.author: maghan
ms.openlocfilehash: d96a29366b5aa81905b3fa81efa6bdf19f51edf8
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85732439"
---
# <a name="cursor-functions-transact-sql"></a>Funzioni per i cursori (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Queste funzioni scalari restituiscono informazioni sui cursori:
  
- [@@CURSOR_ROWS](../../t-sql/functions/cursor-rows-transact-sql.md)
- [@@FETCH_STATUS](../../t-sql/functions/fetch-status-transact-sql.md)
- [CURSOR_STATUS](../../t-sql/functions/cursor-status-transact-sql.md)
  
Tutte le funzioni per i cursori sono non deterministiche, Questo significa che non restituiscono sempre gli stessi risultati ogni volta che vengono eseguite, anche se il set di valori di input è lo stesso. Per altre informazioni sul determinismo delle funzioni, vedere [Funzioni deterministiche e non deterministiche](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).
  
## <a name="see-also"></a>Vedere anche

[Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)
