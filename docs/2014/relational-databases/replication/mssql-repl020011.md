---
title: MSSQL_REPL020011 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_REPL020011 error
ms.assetid: f72072d7-bbb6-48ad-ac88-afa74aeb4d58
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 646f25740ebb007f8d04a89690d3b712781efcc8
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85060721"
---
# <a name="mssql_repl020011"></a>MSSQL_REPL020011
    
## <a name="message-details"></a>Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|20011|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Impossibile eseguire '%1' in '%2'.|  
  
## <a name="explanation"></a>Spiegazione  
 Questo errore può essere generato in diverse circostanze durante l'elaborazione della replica transazionale, ad esempio quando il agente di lettura log viene eseguito **sp_replcmds** (il processo non è stato in grado di eseguire ' sp_replcmds ' in \<ServerName> ) o **sp_repldone** (il processo non è stato in grado di eseguire ' sp_repldone ' in \<ServerName> ).  
  
## <a name="user-action"></a>Azione dell'utente  
 Se l'errore viene generato in un database che è appena stato ripristinato da un backup, verificare di aver eseguito i passaggi descritti nella documentazione relativa al backup e al ripristino e di aver eseguito **sp_replrestart** , se appropriato. Per altre informazioni, vedere [Strategie per il backup e il ripristino della replica snapshot e della replica transazionale](administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md).  
  
 Si tratta di un errore di elaborazione interna. Se viene generato in circostanze diverse dal ripristino, in genere indica che è necessario rimuovere o riconfigurare la replica. Se non è possibile rimuovere la replica, rivolgersi al supporto tecnico.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento a errori ed eventi &#40;replica&#41;](errors-and-events-reference-replication.md)   
 [sp_replcmds &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql)   
 [sp_repldone &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-repldone-transact-sql)  
  
  
