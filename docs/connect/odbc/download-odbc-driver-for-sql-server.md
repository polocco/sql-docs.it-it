---
title: Scaricare ODBC Driver for SQL Server
description: Scaricare Microsoft ODBC Driver for SQL Server per sviluppare applicazioni in codice nativo che si connettono a SQL Server e al database SQL di Azure.
ms.date: 07/31/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 53b09784-bb9d-4fd4-99d3-0492b3308ac4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b1f77ce4eb0b329fdb6911bd38f6e120e4ff7d3d
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/05/2020
ms.locfileid: "91727522"
---
# <a name="download-odbc-driver-for-sql-server"></a>Scaricare ODBC Driver for SQL Server

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Microsoft ODBC Driver for SQL Server è una libreria di collegamento dinamico (DLL) contenente il supporto di runtime per applicazioni che usano API di codice nativo per la connessione a SQL Server. Usare Microsoft ODBC Driver 17 for SQL Server per creare nuove applicazioni o migliorare le applicazioni esistenti per sfruttare le nuove funzionalità di SQL Server.

## <a name="download-for-windows"></a>Download per Windows

Il programma di installazione ridistribuibile per Microsoft ODBC Driver 17 for SQL Server installa i componenti client necessari in fase di esecuzione per sfruttare le funzionalità di SQL Server più recenti. Installa facoltativamente i file di intestazione necessari per sviluppare un'applicazione che usa l'API ODBC. A partire dalla versione 17.4.2, il programma di installazione include anche e installa Microsoft Active Directory Authentication Library (ADAL.dll).

La versione 17.6.1 è la versione con disponibilità generale più recente. Se è installata una versione precedente di Microsoft ODBC Driver 17 per SQL Server, l'installazione della versione 17.6.1 eseguirà l'aggiornamento della versione precedente a 17.6.1.

**[![Download](../../ssms/media/download-icon.png) Scaricare Microsoft ODBC Driver 17 per SQL Server (x64)](https://go.microsoft.com/fwlink/?linkid=2137027)**  
**[![Download](../../ssms/media/download-icon.png) Scaricare Microsoft ODBC Driver 17 per SQL Server (x86)](https://go.microsoft.com/fwlink/?linkid=2137028)**  

### <a name="version-information"></a>Informazioni sulla versione

- Numero di versione: 17.6.1.1
- Resa disponibile: 31 luglio 2020

> [!Note]
> Se si accede a questa pagina da una versione non in lingua inglese e si vuole visualizzare il contenuto più aggiornato, visitare la [versione in inglese del sito](). È possibile scaricare una versione del sito diversa da quella in lingua inglese selezionando [available languages](#available-languages) (lingue disponibili).

## <a name="available-languages"></a>Lingue disponibili

Questa versione di Microsoft ODBC Driver for SQL Server può essere installata nelle lingue seguenti:

Microsoft ODBC Driver 17.6.1 per SQL Server (x64):  
[Cinese (semplificato)](https://go.microsoft.com/fwlink/?linkid=2137027&clcid=0x804) | [Cinese (tradizionale)](https://go.microsoft.com/fwlink/?linkid=2137027&clcid=0x404) | [Inglese (Stati Uniti)](https://go.microsoft.com/fwlink/?linkid=2137027&clcid=0x409) | [Francese](https://go.microsoft.com/fwlink/?linkid=2137027&clcid=0x40c) | [Tedesco](https://go.microsoft.com/fwlink/?linkid=2137027&clcid=0x407) | [Italiano](https://go.microsoft.com/fwlink/?linkid=2137027&clcid=0x410) | [Giapponese](https://go.microsoft.com/fwlink/?linkid=2137027&clcid=0x411) | [Coreano](https://go.microsoft.com/fwlink/?linkid=2137027&clcid=0x412) | [Portoghese (Brasile)](https://go.microsoft.com/fwlink/?linkid=2137027&clcid=0x416) | [Russo](https://go.microsoft.com/fwlink/?linkid=2137027&clcid=0x419) | [Spagnolo](https://go.microsoft.com/fwlink/?linkid=2137027&clcid=0x40a)

Microsoft ODBC Driver 17.6.1 per SQL Server (x86):  
[Cinese (semplificato)](https://go.microsoft.com/fwlink/?linkid=2137028&clcid=0x804) | [Cinese (tradizionale)](https://go.microsoft.com/fwlink/?linkid=2137028&clcid=0x404) | [Inglese (Stati Uniti)](https://go.microsoft.com/fwlink/?linkid=2137028&clcid=0x409) | [Francese](https://go.microsoft.com/fwlink/?linkid=2137028&clcid=0x40c) | [Tedesco](https://go.microsoft.com/fwlink/?linkid=2137028&clcid=0x407) | [Italiano](https://go.microsoft.com/fwlink/?linkid=2137028&clcid=0x410) | [Giapponese](https://go.microsoft.com/fwlink/?linkid=2137028&clcid=0x411) | [Coreano](https://go.microsoft.com/fwlink/?linkid=2137028&clcid=0x412) | [Portoghese (Brasile)](https://go.microsoft.com/fwlink/?linkid=2137028&clcid=0x416) | [Russo](https://go.microsoft.com/fwlink/?linkid=2137028&clcid=0x419) | [Spagnolo](https://go.microsoft.com/fwlink/?linkid=2137028&clcid=0x40a)

### <a name="release-notes-for-windows"></a>Note sulla versione per Windows

Per informazioni dettagliate su questa versione in Windows, vedere le [note sulla versione di Windows](windows\release-notes-odbc-sql-server-windows.md).

### <a name="previous-releases-for-windows"></a>Versioni precedenti per Windows

Per scaricare le versioni precedenti per Windows, vedere [Versioni precedenti di Microsoft ODBC Driver for SQL Server](windows\release-notes-odbc-sql-server-windows.md#previous-releases).

## <a name="download-for-linux-and-macos"></a>Download per Linux e macOS

Microsoft ODBC Driver for SQL Server può essere scaricato e installato usando le gestioni pacchetti per Linux e macOS seguendo le istruzioni di installazione pertinenti:  
[Installare ODBC for SQL Server (Linux)](linux-mac\installing-the-microsoft-odbc-driver-for-sql-server.md)  
[Installare ODBC for SQL Server (macOS)](linux-mac\install-microsoft-odbc-driver-sql-server-macos.md)  

Se è necessario scaricare i pacchetti per l'installazione offline, tutte le versioni sono disponibili tramite i collegamenti seguenti.

> [!Note]
> I pacchetti denominati `msodbcsql17-*` sono la versione più recente. I pacchetti denominati `msodbcsql-*` sono la versione 13 del driver.

### <a name="alpine"></a>Alpine

- [Pacchetto Alpine 17.6.1.1](https://download.microsoft.com/download/e/4/e/e4e67866-dffd-428c-aac7-8d28ddafb39b/msodbcsql17_17.6.1.1-1_amd64.apk) ([firma PGP](https://download.microsoft.com/download/e/4/e/e4e67866-dffd-428c-aac7-8d28ddafb39b/msodbcsql17_17.6.1.1-1_amd64.sig))
- [Pacchetto Alpine 17.5.2.2 ](https://download.microsoft.com/download/e/4/e/e4e67866-dffd-428c-aac7-8d28ddafb39b/msodbcsql17_17.5.2.2-1_amd64.apk) ([firma PGP](https://download.microsoft.com/download/e/4/e/e4e67866-dffd-428c-aac7-8d28ddafb39b/msodbcsql17_17.5.2.2-1_amd64.sig))
- [Pacchetto Alpine 17.5.2.1 ](https://download.microsoft.com/download/e/4/e/e4e67866-dffd-428c-aac7-8d28ddafb39b/msodbcsql17_17.5.2.1-1_amd64.apk) ([firma PGP](https://download.microsoft.com/download/e/4/e/e4e67866-dffd-428c-aac7-8d28ddafb39b/msodbcsql17_17.5.2.1-1_amd64.sig))
- [Pacchetto Alpine 17.5.1.1 ](https://download.microsoft.com/download/e/4/e/e4e67866-dffd-428c-aac7-8d28ddafb39b/msodbcsql17_17.5.1.1-1_amd64.apk) ([firma PGP](https://download.microsoft.com/download/e/4/e/e4e67866-dffd-428c-aac7-8d28ddafb39b/msodbcsql17_17.5.1.1-1_amd64.sig))

### <a name="debian"></a>Debian

- [Pacchetti DEB Debian 10](https://packages.microsoft.com/debian/10/prod/pool/main/m/msodbcsql17/)
- [Pacchetti DEB Debian 9](https://packages.microsoft.com/debian/9/prod/pool/main/m/msodbcsql17/)
- [Pacchetti DEB Debian 8](https://packages.microsoft.com/debian/8/prod/pool/main/m/msodbcsql17/)
- [Pacchetti DEB Debian 8 (msodbcsql 13.x)](https://packages.microsoft.com/debian/8/prod/pool/main/m/msodbcsql/)

### <a name="redhat"></a>RedHat

- [Pacchetti RPM RedHat 8](https://packages.microsoft.com/rhel/8/prod/)
- [Pacchetti RPM RedHat 7](https://packages.microsoft.com/rhel/7/prod/)
- [Pacchetti RPM RedHat 6](https://packages.microsoft.com/rhel/6/prod/)

### <a name="suse"></a>SUSE

- [Pacchetti RPM SuSE 15](https://packages.microsoft.com/sles/15/prod/)
- [Pacchetti RPM SuSE 12](https://packages.microsoft.com/sles/12/prod/)
- [Pacchetti RPM SuSE 11](https://packages.microsoft.com/sles/11/prod/)

### <a name="ubuntu"></a>Ubuntu

- [Pacchetti DEB Ubuntu 20.04](https://packages.microsoft.com/ubuntu/20.04/prod/pool/main/m/msodbcsql17/)
- [Pacchetti DEB Ubuntu 18.04](https://packages.microsoft.com/ubuntu/18.04/prod/pool/main/m/msodbcsql17/)
- [Pacchetti DEB Ubuntu 16.04](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql17/)
- [Pacchetti DEB Ubuntu 14.04](https://packages.microsoft.com/ubuntu/14.04/prod/pool/main/m/msodbcsql17/)
- [Pacchetti DEB Ubuntu 16.04 (msodbcsql 13.x)](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql/)
- [Pacchetti DEB Ubuntu 14.04 (msodbcsql 13.x)](https://packages.microsoft.com/ubuntu/14.04/prod/pool/main/m/msodbcsql/)

Vedere anche [Installazione del driver Linux](linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md).

### <a name="macos"></a>macOS

- Per informazioni dettagliate, vedere la [formula Homebrew](https://github.com/Microsoft/homebrew-mssql-release).

Vedere anche [Installazione del driver macOS](linux-mac/install-microsoft-odbc-driver-sql-server-macos.md).

### <a name="older-linux-releases"></a>Versioni precedenti di Linux

- **Red Hat Enterprise Linux 5 e 6 (a 64 bit)**  - [Download di Microsoft ODBC Driver 11 for SQL Server - Red Hat Linux](https://go.microsoft.com/fwlink/?LinkId=267321)  
- **SUSE Linux Enterprise 11 Service Pack 2 (a 64 bit)**  - [Download di Microsoft ODBC Driver 11 Preview for SQL Server - SUSE Linux](https://go.microsoft.com/fwlink/?LinkId=264916)

### <a name="release-notes-for-linux-and-macos"></a>Note sulla versione per Linux e macOS

Per informazioni dettagliate sulle versioni per Linux e macOS, vedere le [note sulla versione di Linux e macOS](linux-mac\release-notes-odbc-sql-server-linux-mac.md).