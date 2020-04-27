---
title: Esecuzione di stored procedure | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- stored procedures [ODBC], running
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], executing
ms.assetid: 866b6dd3-2acd-4dfb-aeca-a0352b2d4c6a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6bdf66ed9214a151886caedcf2247935a07f7811
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "68206735"
---
# <a name="running-stored-procedures"></a>Esecuzione delle stored procedure
  Una stored procedure è un oggetto eseguibile archiviato in un database. Supporti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Stored procedure:  
  
     Una o più istruzioni SQL precompilate in una sola stored procedure eseguibile.  
  
-   Stored procedure estese:  
  
     DLL C o C++ scritte nell'API ODS di SQL Server per le stored procedure estese. L'API ODS amplia le funzionalità delle stored procedure per includere il codice C o C++.  
  
 Durante l'esecuzione delle istruzioni, la chiamata a una stored procedure sull'origine dati, in alternativa all'esecuzione o alla preparazione diretta di un'istruzione nell'applicazione client, può offrire:  
  
-   Prestazioni più elevate  
  
     Le istruzioni SQL vengono analizzate e compilate durante la creazione delle stored procedure. Questo overhead viene quindi salvato durante l'esecuzione delle stored procedure.  
  
-   Overhead di rete ridotto  
  
     L'esecuzione di una stored procedure in alternativa all'invio di query complesse in rete può ridurre il traffico di rete. Se un'applicazione ODBC utilizza la sintassi ODBC {CALL} per eseguire una stored procedure, il driver ODBC esegue ulteriori ottimizzazioni che eliminano la necessità di convertire i dati dei parametri.  
  
-   Maggiore coerenza  
  
     Se le regole di un'organizzazione vengono implementate in una risorsa centrale, ad esempio una stored procedure, possono essere codificate, testate e sottoposte a debug una volta. I singoli programmatori possono quindi utilizzare le stored procedure testate anziché sviluppare implementazioni personalizzate.  
  
-   Maggiore precisione  
  
     Poiché le stored procedure vengono in genere sviluppate da programmatori esperti, sono più efficienti e contengono un numero di errori inferiore rispetto al codice sviluppato più volte da programmatori meno competenti.  
  
-   Maggior numero di funzionalità  
  
     Le stored procedure estese possono utilizzare le caratteristiche C e C++ non disponibili nelle istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
     Per un esempio di come chiamare una stored procedure, vedere [elaborare i codici restituiti e i parametri di Output &#40;&#41;ODBC ](../native-client-odbc-how-to/running-stored-procedures-process-return-codes-and-output-parameters.md).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
-   [Chiamata di una stored procedure](calling-a-stored-procedure.md)  
  
-   [Invio in batch di chiamate a stored procedure](batching-stored-procedure-calls.md)  
  
-   [Risultati dell'elaborazione delle stored procedure](processing-stored-procedure-results.md)  
  
## <a name="see-also"></a>Vedi anche  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)   
 [Procedure per l'esecuzione di stored procedure &#40;ODBC&#41;](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)  
  
  
