---
title: MSSQLSERVER_2546 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2546 (Database Engine error)
ms.assetid: c8f0e1b4-c7c4-45f2-9221-746714172313
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ca1a8af843d0183acd46a8b11e00427738d59d0e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62868852"
---
# <a name="mssqlserver_2546"></a>MSSQLSERVER_2546
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|2546|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC_INDEX_MARKED_DISABLED|  
|Testo del messaggio|L'indice 'INDEX_NAME' della tabella 'OBJECT_NAME' è contrassegnato come disabilitato. Ricompilare l'indice per riportarlo online.|  
  
## <a name="explanation"></a>Spiegazione  
 L'indice specificato è contrassegnato come offline oppure è disabilitato e pertanto non può essere controllato.  
  
## <a name="user-action"></a>Azione dell'utente  
 Ricompilare l'indice utilizzando ALTER INDEX.  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)   
 [Riorganizzare e ricompilare gli indici](../indexes/indexes.md)  
  
  
