---
title: MSSQLSERVER_21899 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21899 (Database Engine error)
ms.assetid: 32b87a7c-5380-4638-b147-dd78618f6625
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d40ee92b98999cd6b88a469a02f290e68ca06559
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62915019"
---
# <a name="mssqlserver_21899"></a>MSSQLSERVER_21899
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|21899|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SQLErrorNum21899|  
|Testo del messaggio|Impossibile eseguire la query sul server di pubblicazione reindirizzato '%s' per determinare la presenza di voci sysserver per i Sottoscrittori del server di pubblicazione originale '%s'. Errore '%d', messaggio di errore '%s'.|  
  
## <a name="explanation"></a>Spiegazione  
 In `sp_validate_redirected_publisher` vengono eseguite le query sulle tabelle di metadati delle sottoscrizioni del database del server di pubblicazione sul server remoto per determinare i sottoscrittori associati. L'errore 21899 viene restituito in caso di errore di questa query. La query della convalida richiede l'accesso al database pubblicato sul server di pubblicazione reindirizzato. Se l'accesso, specificato quando `sp_adddistpublisher` viene chiamato per il server di pubblicazione originale, non è autorizzato ad accedere al database pubblicato sul server di pubblicazione reindirizzato, viene restituito l'errore 21899.  
  
## <a name="user-action"></a>Azione dell'utente  
 Controllare il messaggio di errore citato per determinare la causa dell'errore ed eseguire azioni correttive appropriate  
  
  
