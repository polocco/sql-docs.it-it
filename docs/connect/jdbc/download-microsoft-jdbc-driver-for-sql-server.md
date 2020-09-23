---
title: Scaricare Microsoft JDBC Driver per SQL Server
description: Scaricare Microsoft JDBC Driver per SQL Server per sviluppare applicazioni Java che si connettono a SQL Server e al database SQL di Azure.
ms.date: 08/24/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 451181b8-11e6-4d01-b547-9ac5aada8238
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d48c3f0384a805debe13472fae1841515207d160
ms.sourcegitcommit: 9be0047805ff14e26710cfbc6e10d6d6809e8b2c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "89042444"
---
# <a name="download-microsoft-jdbc-driver-for-sql-server"></a>Scaricare Microsoft JDBC Driver per SQL Server

Microsoft JDBC Driver per SQL Server è un driver JDBC di tipo 4 che offre connettività di database tramite le API JDBC standard disponibili nella piattaforma Java. I download dei driver sono disponibili per tutti gli utenti senza costi aggiuntivi. Forniscono l'accesso a SQL Server da qualsiasi applicazione Java, server applicazioni o applet abilitata per Java.

## <a name="download"></a>Download

La versione 8.4 è la versione con disponibilità generale più recente. Supporta Java 8, 11 e 14. Se è necessario eseguire in un runtime Java precedente, vedere la [matrice di supporto per le specifiche Java e JDBC](microsoft-jdbc-driver-for-sql-server-support-matrix.md#java-and-jdbc-specification-support) per verificare se è disponibile una versione del driver supportata che è possibile usare. Il supporto per la connettività Java è in continuo miglioramento. Di conseguenza, è consigliabile usare la versione più recente di Microsoft JDBC Driver.

**[![Download](../../ssms/media/download-icon.png) Scaricare Microsoft JDBC Driver 8.4 per SQL Server (zip)](https://go.microsoft.com/fwlink/?linkid=2137600)**  
**[![Download](../../ssms/media/download-icon.png) Scaricare Microsoft JDBC Driver 8.4 per SQL Server (tar.gz)](https://go.microsoft.com/fwlink/?linkid=2137502)**  

### <a name="version-information"></a>Informazioni sulla versione

- Numero di versione: 8.4.1
- Resa disponibile: 27 agosto 2020

Quando si Scarica il driver sono presenti più file JAR. Il nome del file JAR indica la versione di Java supportata.

> [!Note]
> Se si accede a questa pagina da una versione non in lingua inglese e si vuole visualizzare il contenuto più aggiornato, visitare la [versione in inglese del sito](https://aka.ms/downloadmssqljdbcenglish). È possibile scaricare una versione del sito diversa da quella in lingua inglese selezionando [available languages](#available-languages) (lingue disponibili).

## <a name="available-languages"></a>Lingue disponibili

Questa versione di Microsoft JDBC Driver per SQL Server è disponibile nelle lingue seguenti:

Microsoft JDBC Driver 8.4.1 per SQL Server (zip): [Cinese (semplificato)](https://go.microsoft.com/fwlink/?linkid=2137600&clcid=0x804) | [Cinese (tradizionale)](https://go.microsoft.com/fwlink/?linkid=2137600&clcid=0x404) | [Inglese (Stati Uniti)](https://go.microsoft.com/fwlink/?linkid=2137600&clcid=0x409) | [Francese](https://go.microsoft.com/fwlink/?linkid=2137600&clcid=0x40c) | [Tedesco](https://go.microsoft.com/fwlink/?linkid=2137600&clcid=0x407) | [Italiano](https://go.microsoft.com/fwlink/?linkid=2137600&clcid=0x410) | [Giapponese](https://go.microsoft.com/fwlink/?linkid=2137600&clcid=0x411) | [Coreano](https://go.microsoft.com/fwlink/?linkid=2137600&clcid=0x412) | [Portoghese (Brasile)](https://go.microsoft.com/fwlink/?linkid=2137600&clcid=0x416) | [Russo](https://go.microsoft.com/fwlink/?linkid=2137600&clcid=0x419) | [Spagnolo](https://go.microsoft.com/fwlink/?linkid=2137600&clcid=0x40a)

Microsoft JDBC Driver 8.4.1 per SQL Server (tar.gz): [Cinese (semplificato)](https://go.microsoft.com/fwlink/?linkid=2137502&clcid=0x804) | [Cinese (tradizionale)](https://go.microsoft.com/fwlink/?linkid=2137502&clcid=0x404) | [Inglese (Stati Uniti)](https://go.microsoft.com/fwlink/?linkid=2137502&clcid=0x409) | [Francese](https://go.microsoft.com/fwlink/?linkid=2137502&clcid=0x40c) | [Tedesco](https://go.microsoft.com/fwlink/?linkid=2137502&clcid=0x407) | [Italiano](https://go.microsoft.com/fwlink/?linkid=2137502&clcid=0x410) | [Giapponese](https://go.microsoft.com/fwlink/?linkid=2137502&clcid=0x411) | [Coreano](https://go.microsoft.com/fwlink/?linkid=2137502&clcid=0x412) | [Portoghese (Brasile)](https://go.microsoft.com/fwlink/?linkid=2137502&clcid=0x416) | [Russo](https://go.microsoft.com/fwlink/?linkid=2137502&clcid=0x419) | [Spagnolo](https://go.microsoft.com/fwlink/?linkid=2137502&clcid=0x40a)

### <a name="release-notes"></a>Note sulla versione

Per informazioni dettagliate su questa versione, vedere [le note sulla versione](release-notes-for-the-jdbc-driver.md) e [i requisiti di sistema](system-requirements-for-the-jdbc-driver.md).

### <a name="previous-releases"></a>Versioni precedenti

Per scaricare le versioni precedenti, vedere [Versioni precedenti di Microsoft JDBC Driver per SQL Server](release-notes-for-the-jdbc-driver.md#previous-releases).

## <a name="using-the-jdbc-driver-with-maven-central"></a>Uso del driver JDBC con Maven Central

Il driver JDBC può essere aggiunto a un progetto Maven aggiungendolo come dipendenza nel file POM.xml con il codice seguente:

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>8.4.1.jre11</version>
</dependency>
```  

## <a name="unsupported-drivers"></a>Driver non supportati

Le versioni non supportate dei driver non sono disponibili per il download in questo contesto. Il supporto per la connettività Java è in continuo miglioramento, Di conseguenza, è consigliabile usare la versione più recente di Microsoft JDBC Driver.  
  
## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su Microsoft JDBC Driver per SQL Server, vedere [Panoramica del driver JDBC](overview-of-the-jdbc-driver.md) e il [repository GitHub del driver JDBC](https://github.com/microsoft/mssql-jdbc/blob/dev/README.md).
