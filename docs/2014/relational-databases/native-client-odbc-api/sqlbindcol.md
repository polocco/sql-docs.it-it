---
title: SQLBindCol | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLBindCol function
ms.assetid: fbd7ba20-d917-4ca9-b018-018ac6af9f98
author: rothja
ms.author: jroth
ms.openlocfilehash: 72d0ca1b0fbad144117e409019d8d2247bbf918f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85022950"
---
# <a name="sqlbindcol"></a>SQLBindCol
  Come regola generale, prendere in considerazione le implicazioni dell'utilizzo di **SQLBindCol** per la conversione dei dati. Le conversioni per associazione sono processi client. Se ad esempio viene recuperato un valore a virgola mobile associato a una colonna di tipo character, nel driver viene eseguita in locale la conversione da float a character quando viene recuperata una riga. La funzione [!INCLUDE[tsql](../../includes/tsql-md.md)] CONVERT può essere utilizzata per riportare il costo della conversione dei dati nel server.  
  
 Un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può restituire più set di righe di risultati in una singola esecuzione dell'istruzione. Ogni set di risultati deve essere associato separatamente. Per ulteriori informazioni sull'associazione per più set di risultati, vedere [SQLMoreResults](sqlmoreresults.md).  
  
 Lo sviluppatore può associare colonne a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipi di dati C specifici di usando il valore *targetType* `SQL_C_BINARY` . Le colonne associate a tipi specifici di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non sono portabili. I tipi di dati ODBC C specifici di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] definiti corrispondono alle definizioni del tipo di DB-Library e gli sviluppatori di DB-Library che si occupano della portabilità delle applicazioni potrebbero sfruttare questa caratteristica.  
  
 Il troncamento dei dati di Reporting è un processo dispendioso per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC di Native Client. È possibile evitare il troncamento assicurandosi che la larghezza di tutti i buffer di dati associati sia sufficiente per restituire i dati. Per i dati di tipo character, la larghezza deve includere lo spazio per un carattere di terminazione della stringa quando viene utilizzato il comportamento predefinito del driver per la terminazione della stringa. Ad esempio, l'associazione di una [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] colonna **char (5)** a una matrice di cinque caratteri comporta un troncamento per ogni valore recuperato. L'associazione della stessa colonna a una matrice di sei caratteri evita il troncamento fornendo un elemento character in cui archiviare il terminatore null. [SQLGetData](sqlgetdata.md) può essere utilizzato per recuperare in modo efficiente dati binari e di tipo carattere lungo senza troncamenti.  
  
 Per i tipi di dati con valori di grandi dimensioni, se il buffer fornito dall'utente non è sufficientemente grande da mantenere l'intero valore della colonna, `SQL_SUCCESS_WITH_INFO` viene restituito e la stringa "data; troncamento a destra. viene generato un avviso. L'argomento `StrLen_or_IndPtr` conterrà il numero di caratteri/byte archiviati nel buffer.  
  
## <a name="sqlbindcol-support-for-enhanced-date-and-time-features"></a>Supporto di SQLBindCol per le caratteristiche avanzate di data e ora  
 I valori della colonna dei risultati dei tipi data/ora vengono convertiti come descritto in [conversioni da SQL a C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md). Si noti che per recuperare le colonne time e DateTimeOffset come strutture corrispondenti ( `SQL_SS_TIME2_STRUCT` e **SQL_SS_TIMESTAMPOFFSET_STRUCT**), *targetType* deve essere specificato come `SQL_C_DEFAULT` o `SQL_C_BINARY` .  
  
 Per ulteriori informazioni, vedere [miglioramenti di data e ora &#40;&#41;ODBC ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlbindcol-support-for-large-clr-udts"></a>Supporto di SQLBindCol per tipi CLR definiti dall'utente di grandi dimensioni  
 **SQLBindCol** supporta i tipi CLR definiti dall'utente di grandi dimensioni. Per ulteriori informazioni, vedere [tipi CLR definiti dall'utente di grandi dimensioni &#40;&#41;ODBC ](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [SQLBindCol (funzione)](https://go.microsoft.com/fwlink/?LinkId=59327)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  
