---
title: Classe di evento Broker:Activation | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Broker:Activation event class
ms.assetid: 481d5b13-657e-4b51-8783-ccac3595bd45
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f2562f3931f98c040bb3dc475e3863bb6396dbbf
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62664347"
---
# <a name="brokeractivation-event-class"></a>Broker:Activation - classe di evento
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] genera un evento **Broker:Activation** quando un monitoraggio di coda avvia una stored procedure di attivazione o invia una notifica QUEUE_ACTIVATION oppure quando è presente una stored procedure di attivazione avviata da un monitoraggio di coda.  
  
## <a name="brokeractivation-event-class-data-columns"></a>Colonne di dati della classe di evento Broker:Activation  
  
|Colonna di dati|Type|Descrizione|Numero di colonna|Filtrabile|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ClientProcessID**|`int`|ID assegnato dal computer host al processo in cui è in esecuzione l'applicazione client. Questa colonna di dati viene popolata se l'ID del processo client viene fornito dal client.|9|Sì|  
|**DatabaseID**|`int`|ID del database specificato dall'istruzione USE *database* oppure ID del database predefinito, se per una determinata istanza non viene eseguita alcuna istruzione USE *database*. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] visualizza il nome del database se la colonna di dati **ServerName** è acquisita nella traccia e il server è disponibile. Determinare il valore per un database utilizzando la funzione DB_ID.|3|Sì|  
|**EventClass**|`int`|Tipo di classe di evento acquisita. Sempre **163** per **Broker:Activation**.|27|No|  
|**EventSequence**|`int`|Numero di sequenza dell'evento.|51|No|  
|**EventSubClass**|`nvarchar`|Azione specifica indicata dall'evento. Uno dei valori seguenti:<br /><br /> **inizio**: <br />                [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha avviato una stored procedure di attivazione.<br /><br /> **terminato**: la stored procedure di attivazione è stata chiusa normalmente.<br /><br /> **interrotto**: l'attivazione stored procedure terminata con un errore.|21|No|  
|**HostName**|`nvarchar`|Nome del computer in cui è in esecuzione il client. Questa colonna di dati viene popolata se il nome host viene fornito dal client. Per determinare il nome host, usare la funzione HOST_NAME.|8|Sì|  
|**IntegerData**|`int`|Numero di attività in corso nella coda.|25|No|  
|**IsSystem**|`int`|Indica se l'evento è stato generato per un processo di sistema o un processo utente. 1 = sistema, 0 = utente.|60|No|  
|**LoginSid**|`image`|ID di sicurezza (SID) dell'utente connesso. Il SID è univoco per ogni account di accesso nel server.|41|Sì|  
|**NTDomainName**|`nvarchar`|Dominio di Windows a cui appartiene l'utente.|7|Sì|  
|**NTUserName**|`nvarchar`|Nome dell'utente proprietario della connessione che ha generato questo evento.|6|Sì|  
|**ObjectID**|`int`|Coda associata all'evento.|22|No|  
|**ServerName**|`nvarchar`|Nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracciata.|26|No|  
|**SPID**|`int`|ID del processo server assegnato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] al processo associato al client.|12|Sì|  
|**StartTime**|`datetime`|Ora di inizio dell'evento, se disponibile.|14|Sì|  
|**TransactionID**|`bigint`|ID della transazione assegnato dal sistema.|4|No|  
  
  
