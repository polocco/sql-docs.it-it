---
title: MSSQLSERVER_8712 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8712 (Database Engine error)
ms.assetid: 292fb3bc-062e-41e4-a566-b5d3d0b21977
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b956a9f51e013ce03801ff870e27f337c738b3c6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62762061"
---
# <a name="mssqlserver_8712"></a>MSSQLSERVER_8712
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|8712|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|USEPLAN_ERR_NO_INDEX|  
|Testo del messaggio|L'indice '%.*ls' specificato nell'hint USE PLAN non esiste. Specificare un indice esistente o creare un indice con il nome specificato.|  
  
## <a name="explanation"></a>Spiegazione  
 Un indice specificato nell'hint USE PLAN non esiste.  
  
## <a name="user-action"></a>Azione dell'utente  
 Verificare che tutti gli indici specificati nell'hint USE PLAN esistano.  
  
## <a name="see-also"></a>Vedere anche  
 [Hint per la query &#40;&#41;Transact-SQL](/sql/t-sql/queries/hints-transact-sql-query)   
 [Guide di piano](../performance/plan-guides.md)  
  
  
