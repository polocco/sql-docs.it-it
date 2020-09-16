---
description: Analisi dei risultati
title: Analisi dei risultati | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: rene-ye
ms.author: v-reye
manager: kenvh
ms.openlocfilehash: 93e494ceeac791368a0017f919a9676bbc193966
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438333"
---
# <a name="parsing-the-results"></a>Analisi dei risultati

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Questo articolo descrive come SQL Server preveda l'elaborazione completa dei risultati restituiti da qualsiasi query da parte degli utenti.

## <a name="update-counts-and-result-sets"></a>Conteggi aggiornamenti e set di risultati

Questa sezione illustra i due risultati più comuni restituiti da SQL Server: il conteggio aggiornamenti e il set di risultati. In generale, le query eseguite dagli utenti determinano la restituzione di uno di questi risultati. Gli utenti devono gestirli entrambi durante l'elaborazione dei risultati.

Il codice seguente è un esempio di come un utente può eseguire l'iterazione di tutti i risultati restituiti dal server:
```java
try (Connection connection = DriverManager.getConnection(URL); Statement statement = connection.createStatement()) {
    boolean resultsAvailable = statement.execute(USER_SQL);
    int updateCount = -2;
    while (true) {
        updateCount = statement.getUpdateCount();
        if (!resultsAvailable && updateCount == -1)
            break;
        if (resultsAvailable) {
            // handle ResultSet
        } else {
            // handle Update Count
        }
        resultsAvailable = statement.getMoreResults();
    }
}
```

## <a name="exceptions"></a>Eccezioni
Quando si esegue un'istruzione che restituisce un errore o un messaggio informativo, SQL Server risponderà in modo diverso a seconda del fatto che sia in grado o meno di generare un piano di esecuzione. Il messaggio di errore può essere generato immediatamente dopo l'esecuzione dell'istruzione oppure può richiedere un set di risultati distinto. Nel secondo caso, è necessario che le applicazioni analizzino il set di risultati per recuperare l'eccezione.

Quando SQL Server non è in grado di generare un piano di esecuzione, l'eccezione viene generata immediatamente.

```java
String SQL = "SELECT * FROM nonexistentTable;";
try (Statement statement = connection.createStatement();) {
    statement.execute(SQL);
} catch (SQLException e) {
    e.printStackTrace();
}
```

Quando SQL Server restituisce un messaggio di errore in un set di risultati, quest'ultimo deve essere elaborato per recuperare l'eccezione.

```java
String SQL = "SELECT 1/0;";
try (Statement statement = connection.createStatement();) {
    boolean hasResult = statement.execute(SQL);
    if (hasResult) {
        try (ResultSet rs = statement.getResultSet()) {
            // Exception is thrown on next().
            while (rs.next()) {}
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

Se l'esecuzione dell'istruzione genera più set di risultati, è necessario elaborare ogni set di risultati fino a raggiungere quello con l'eccezione.

```java
String SQL = "SELECT 1; SELECT * FROM nonexistentTable;";
try (Statement statement = connection.createStatement();) {
    // Does not throw an exception on execute().
    boolean hasResult = statement.execute(SQL);
    while (hasResult) {
        try (ResultSet rs = statement.getResultSet()) {
            while (rs.next()) {
                System.out.println(rs.getString(1));
            }
        }
        // Moves the next result set that generates the exception.
        hasResult = statement.getMoreResults();
    }
} catch (SQLException e) {
    e.printStackTrace();
}
```

Nel caso di `String SQL = "SELECT * FROM nonexistentTable; SELECT 1;";`, l'eccezione viene generata immediatamente in `execute()` e `SELECT 1` non viene eseguito affatto.

Se l'errore restituito da SQL Server ha una gravità compresa tra `0` e `9`, viene considerato come un messaggio informativo e restituito come `SQLWarning`.

```java
String SQL = "RAISERROR ('WarningLevel5', 5, 2);";
try (Statement statement = connection.createStatement();) {
    boolean hasResult = statement.execute(SQL);
    SQLWarning warning = statement.getWarnings();
    System.out.println(warning);
}
```

## <a name="see-also"></a>Vedere anche

[Panoramica del driver JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)
