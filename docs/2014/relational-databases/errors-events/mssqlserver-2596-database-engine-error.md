---
title: MSSQLSERVER_2596 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2596 (Database Engine error)
ms.assetid: 49ab892f-8ba3-4ba1-b562-ddf205019802
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 21f0f7fdbfc1658ccff24e9610ca96857de159ce
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551866"
---
# <a name="mssqlserver_2596"></a>MSSQLSERVER_2596
    
## <a name="details"></a>Dettagli  
  
|Attributo|valore|  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|2596|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC_DATABASE_IN_READ_ONLY_MODE|  
|Testo del messaggio|L'istruzione di correzione non è stata elaborata. Il database non può essere in modalità sola lettura.|  
  
## <a name="explanation"></a>Spiegazione  
 Il messaggio indica che il database è in modalità sola lettura. Non è possibile implementare correzioni quando un database si trova in tale modalità.  
  
## <a name="user-action"></a>Azione dell'utente  
 Impostare il database per l'accesso in lettura/scrittura utilizzando ALTER DATABASE e quindi eseguire nuovamente il comando DBCC.  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
