---
description: Classe di evento FT:Crawl Started
title: Classe di evento FT:Crawl Started | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Crawl Started event class
ms.assetid: 2535b856-97e8-4fb2-8ba0-5d5446355fa6
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d1e069b4fca1f7fb675f802a3d009d59962444af
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491084"
---
# <a name="ftcrawl-started-event-class"></a>Classe di evento FT:Crawl Started
[!INCLUDE [SQL Server - ASDB](../../includes/applies-to-version/sql-asdb.md)]
   La classe di evento **FT:Crawl Started** indica l'avvio di una ricerca per indicizzazione (popolamento) full-text. Utilizzare questa classe di evento per verificare che una richiesta di ricerca per indicizzazione venga effettivamente accolta dalle attività di lavoro.  
  
## <a name="ft-crawl-started-event-class-data-columns"></a>Colonne di dati della classe di evento FT:Crawl Started  
  
|Nome colonna di dati|Tipo di dati|Descrizione|ID colonna|Filtrabile|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|ID del database in cui è stata avviata la ricerca per indicizzazione full-text. Determinare il valore per un database utilizzando la funzione DB_ID.|3|Sì|  
|**EventClass**|**int**|Tipo di evento = 155.|27|No|  
|**EventSequence**|**int**|Sequenza di un determinato evento all'interno della richiesta.|51|No|  
|**IsSystem**|**int**|Indica se l'evento è stato generato per un processo di sistema o un processo utente. 1 = sistema, 0 = utente.|60|Sì|  
|**ObjectID**|**int**|ID dell'oggetto assegnato dal sistema. La ricerca per indicizzazione full-text è stata avviata sull'indice full-text in questo oggetto.|22|Sì|  
|**SessionLoginName**|**nvarchar**|Nome dell'account di accesso dell'utente che ha avviato la sessione. Se ad esempio si stabilisce la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con l'account di accesso Login1 e si esegue un'istruzione con l'account di accesso Login2, **SessionLoginName** indica Login1 e **LoginName** indica Login2. In questa colonna vengono visualizzati sia gli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che quelli di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.|64|Sì|  
|**SPID**|**int**|ID della sessione in cui si è verificato l'evento.|12|Sì|  
|**StartTime**|**datetime**|Ora di inizio dell'evento, se disponibile.|14|Sì|  
|**TextData**|**ntext**|Tipo di ricerca per indicizzazione full-text. I valori possibili sono Completa, Incrementale, Manuale o Automatica.|1|Sì|  
|**TransactionID**|**bigint**|ID della transazione assegnato dal sistema.|4|Sì|  
  
## <a name="see-also"></a>Vedere anche  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
