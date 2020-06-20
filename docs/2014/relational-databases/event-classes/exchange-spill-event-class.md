---
title: Classe di evento Exchange Spill | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Exchange Spill event class
ms.assetid: fb876cec-f88d-4975-b3fd-0fb85dc0a7ff
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5a59679fc2c48e2c5eabc4be73b186d5267897e3
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85052977"
---
# <a name="exchange-spill-event-class"></a>Exchange Spill - classe di evento
  La classe di evento **Exchange Spill** indica che i buffer di comunicazione in un piano di query parallele sono stati inseriti temporaneamente nel database **tempdb** . Questa classe viene generata raramente e solo quando un piano di query include più analisi di intervalli.  
  
 In genere, la query [!INCLUDE[tsql](../../includes/tsql-md.md)] che genera tali analisi di intervalli include molti operatori BETWEEN, ognuno dei quali seleziona un intervallo di righe di una tabella o di un indice. In alternativa, è possibile ottenere più intervalli utilizzando espressioni, ad esempio (T. a > 10 e T. a \< 20) OR (T.a > 100 e t. a \< 120). I piani di query richiedono inoltre che l'analisi di tali intervalli venga eseguita in ordine perché esiste una clausola ORDER BY relativa a T.a oppure perché un iteratore all'interno del piano richiede che le tuple vengano utilizzate in base all'ordinamento stabilito.  
  
 Quando un piano relativo a tale query include più operatori **Parallelism** , i buffer di comunicazione della memoria utilizzati dagli operatori **Parallelism** si riempiono, con conseguente arresto dell'esecuzione della query. In questo caso, uno degli operatori **Parallelism** inserisce il buffer di output in **tempdb** mediante un'operazione denominata *spill di scambio*, in modo da consentire l'uso delle righe di alcuni buffer di input. Infine, le righe di cui è stato eseguito lo spill vengono restituite al consumer quando questo è pronto per utilizzarle.  
  
 In rarissimi casi, è possibile che all'interno dello stesso piano di esecuzione vengano eseguiti più spill di scambio, causando un rallentamento della query. Se si nota che l'esecuzione dello stesso piano di query include più di cinque spill, contattare il supporto tecnico.  
  
 Talvolta, gli spill di scambio sono temporanei e possono interrompersi quando viene modificata la distribuzione dei dati.  
  
 Esistono diversi modi per evitare gli eventi di spill di scambio:  
  
-   Omettere la clausola ORDER BY se non è necessario ordinare il set di risultati.  
  
-   Se la clausola ORDER BY è necessaria, eliminare la colonna che partecipa a più analisi di intervalli (T.a nell'esempio precedente) da tale clausola.  
  
-   Mediante un hint per l'indice, forzare Query Optimizer a utilizzare un percorso di accesso diverso per la tabella in questione.  
  
-   Riscrivere la query per generare un piano di esecuzione diverso.  
  
-   Forzare l'esecuzione seriale della query aggiungendo l'opzione MAXDOP = 1 alla fine della query o dell'operazione sull'indice. Per altre informazioni, vedere [Configurare l'opzione di configurazione del server max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) e [Configurare operazioni parallele sugli indici](../indexes/configure-parallel-index-operations.md).  
  
> [!IMPORTANT]  
>  Per determinare la posizione in cui si verifica l'evento **Exchange Spill** quando Query Optimizer genera un piano di esecuzione, è inoltre consigliabile acquisire una classe di evento Showplan nella traccia. È possibile scegliere qualsiasi classe di evento Showplan ad eccezione delle classi di evento **Showplan Text** e **Showplan Text (Unencoded)** , poiché non consentono la restituzione di alcun ID nodo. Nelle classi Showplan gli ID nodo identificano ogni operazione eseguita da Query Optimizer quando genera un piano di esecuzione della query. Queste operazioni vengono denominate operatori e a ogni operatore presente in una classe Showplan è associato un ID nodo. La colonna **ObjectID** per gli eventi **Exchange Spill** corrisponde all'ID nodo nelle classi Showplan, in modo che sia possibile determinare l'operatore o l'operazione che sta provocando l'errore.  
  
## <a name="exchange-spill-event-class-data-columns"></a>Colonne di dati della classe di evento Exchange Spill  
  
|Nome colonna di dati|Tipo di dati|Descrizione|ID colonna|Filtrabile|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Nome dell'applicazione client in cui è stata creata la connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|10|Sì|  
|**ClientProcessID**|**int**|ID assegnato dal computer host al processo in cui è in esecuzione l'applicazione client. Questa colonna di dati viene popolata se tramite il client viene indicato l'ID del processo client.|9|Sì|  
|**DatabaseID**|**int**|ID del database specificato nell'istruzione di *database* USE oppure il database predefinito se per un'istanza specifica l'istruzione di *database* USE non è stata eseguita. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] visualizza il nome del database se la colonna di dati **ServerName** è acquisita nella traccia e il server è disponibile. Determinare il valore per un database utilizzando la funzione DB_ID.|3|Sì|  
|**DatabaseName**|**nvarchar**|Nome del database nel quale viene eseguita l'istruzione dell'utente.|35|Sì|  
|**EventClass**|**int**|Tipo di evento = 127.|27|No|  
|**EventSequence**|**int**|Sequenza di un determinato evento all'interno della richiesta.|51|No|  
|**EventSubClass**|**int**|Tipo di sottoclasse di evento.<br /><br /> 1=Inizio dello spill<br /><br /> 2=Fine dello spill|21|Sì|  
|**GroupID**|**int**|ID del gruppo del carico di lavoro in cui viene generato l'evento di Traccia SQL.|66|Sì|  
|**HostName**|**nvarchar**|Nome del computer in cui viene eseguito il client. Questa colonna di dati viene popolata se il client fornisce il nome host. Per determinare il nome host, usare la funzione HOST_NAME.|8|Sì|  
|**IsSystem**|**int**|Indica se l'evento è stato generato per un processo di sistema o un processo utente. 1 = sistema, 0 = utente.|60|Sì|  
|**LoginName**|**nvarchar**|Nome dell'account di accesso dell'utente (account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sicurezza di o credenziali di accesso di Windows nel formato * \<DOMAIN> \\<nome utente \> *).|11|Sì|  
|**LoginSid**|**image**|ID di sicurezza (SID) dell'utente connesso. Tali informazioni sono disponibili nella tabella **syslogins** del database **master** . Il SID è univoco per ogni account di accesso nel server.|41|Sì|  
|**NTDomainName**|**nvarchar**|Dominio Windows di appartenenza dell'utente.|7|Sì|  
|**NTUserName**|**nvarchar**|Nome utente di Windows.|6|Sì|  
|**ObjectID**|**int**|ID dell'oggetto assegnato dal sistema. Corrisponde al nodo di ID nelle classi di evento Showplan.|22|Sì|  
|**RequestID**|**int**|ID della richiesta contenente l'istruzione.|49|Sì|  
|**ServerName**|**nvarchar**|Nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracciata.|26|No|  
|**SessionLoginName**|**nvarchar**|Nome dell'account di accesso dell'utente che ha avviato la sessione. Se ad esempio si stabilisce la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con l'account di accesso Login1 e si esegue un'istruzione con l'account di accesso Login2, **SessionLoginName** indica Login1 e **LoginName** indica Login2. In questa colonna sono visualizzati sia gli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che quelli di Windows.|64|Sì|  
|**SPID**|**int**|ID della sessione in cui si è verificato l'evento.|12|Sì|  
|**StartTime**|**datetime**|Ora di inizio dell'evento, se disponibile.|14|Sì|  
|**TransactionID**|**bigint**|ID della transazione assegnato dal sistema.|4|Sì|  
|**XactSequence**|**bigint**|Token utilizzato per descrivere la transazione corrente.|50|Sì|  
  
## <a name="see-also"></a>Vedere anche  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Impostare le opzioni di indice](../indexes/set-index-options.md)   
 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)  
  
  
