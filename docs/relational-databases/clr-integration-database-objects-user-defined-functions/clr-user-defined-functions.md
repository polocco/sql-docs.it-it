---
title: Funzioni CLR definite dall'utente | Microsoft Docs
description: SQL Server integrazione con CLR consente di creare funzioni di aggregazione, con valori di tabella e con valori scalari definiti dall'utente in qualsiasi linguaggio di programmazione .NET Framework.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- building database objects [CLR integration], user-defined functions
- functions [CLR integration]
- common language runtime [SQL Server], user-defined functions
- database objects [CLR integration], user-defined functions
- user-defined functions [CLR integration]
ms.assetid: 6f7491f1-9a46-4146-ae09-056248634de2
author: rothja
ms.author: jroth
ms.openlocfilehash: fe481b1a49f8eba69bbf913e49f398c86244b952
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727857"
---
# <a name="clr-user-defined-functions"></a>Funzioni CLR definite dall'utente
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Le funzioni definite dall'utente sono routine che possono accettare parametri, eseguire calcoli o altre azioni e restituire un risultato. A partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], è possibile scrivere le funzioni definite dall'utente in qualsiasi linguaggio di programmazione [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework, ad esempio [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET o [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C#.  
  
 Esistono due tipi di funzioni: scalari, che restituiscono un solo valore, e con valori di tabella, che restituiscono un set di righe.  
  
 Nella tabella seguente vengono elencati gli argomenti disponibili in questa sezione.  
  
 [Funzioni a valori scalari CLR](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-scalar-valued-functions.md)  
 Vengono descritti i requisiti di implementazione e vengono forniti esempi delle funzioni scalari e con valori di tabella.  
  
 [Funzioni CLR con valori di tabella](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-table-valued-functions.md)  
 Viene illustrato come implementare e utilizzare funzioni valutate a livello di tabella (TVF) e vengono discusse le differenze tra le funzioni TVF CLR (Common Language Runtime) e [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 [Aggregazioni CLR definite dall'utente](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)  
 Viene descritto come implementare e utilizzare le aggregazioni definite dall'utente.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni definite dall'utente](../../relational-databases/user-defined-functions/user-defined-functions.md)  
  
  
