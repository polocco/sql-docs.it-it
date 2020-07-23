---
title: Avviare l'Importazione/Esportazione guidata SQL Server
titleSuffix: Integration Services (SSIS)
ms.prod: sql
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Import and Export Wizard
- starting SQL Server Import and Export Wizard
- Import and Export Wizard
- starting Import and Export Wizard
ms.assetid: 5fc4f6d1-1f6f-444e-9aeb-827f85e1c405
author: chugugrace
ms.author: chugu
ms.reviewer: ''
ms.custom: ''
ms.date: 11/18/2019
ms.openlocfilehash: a80b12db0f303ee82f91be9e3eb60c975396063e
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2020
ms.locfileid: "86914358"
---
# <a name="start-the-sql-server-import-and-export-wizard"></a>Avviare l'Importazione/Esportazione guidata SQL Server

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]

Avviare l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in uno dei modi descritti in questo argomento per importare ed esportare dati da qualsiasi origine dati supportata.

> [!IMPORTANT]
> Questo argomento descrive solo come **avviare** la procedura guidata. Per altre informazioni, vedere [Attività e contenuti correlati](#related-tasks-and-content).

È possibile avviare la procedura guidata:

- Dal [menu Start](#start-menu).
- Dal [prompt dei comandi](#command-prompt).
- Da [SQL Server Management Studio (SSMS)](#sql-server-management-studio-ssms).
- Da [Visual Studio con SQL Server Data Tools (SSDT)](#visual-studio).

## <a name="prerequisite---is-the-wizard-installed-on-your-computer"></a>Prerequisito: la procedura guidata è installata nel computer?

Se si vuole eseguire la procedura guidata, ma [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è disponibile nel computer, è possibile installare l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installando SQL Server Data Tools (SSDT). Per altre informazioni, vedere [Scaricare SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx).

> [!NOTE]
> Per usare la versione a 64 bit dell'Importazione/Esportazione guidata SQL Server, è necessario installare SQL Server. SQL Server Data Tools (SSDT) e SQL Server Management Studio (SSMS) sono applicazioni a 32 bit e installano solo i file a 32 bit, inclusa la versione a 32 bit della procedura guidata.

## <a name="start-menu"></a>Menu Start

### <a name="start-the-sql-server-import-and-export-wizard-from-the-start-menu"></a>Avviare l'Importazione/Esportazione guidata SQL Server dal menu Start

1. Nel menu **Start** trovare ed espandere **Microsoft SQL Server 20xx**.
2. Fare clic su una delle opzioni seguenti.
    - **Importazione ed esportazione dati (64 bit) SQL Server 20xx**
    - **Importazione ed esportazione dati (32 bit) SQL Server 20xx**

    Eseguire la versione a 64 bit della procedura guidata a meno che l'origine dati non richieda un provider di dati a 32 bit.

    ![Avviare la procedura guidata da Start](../../integration-services/import-export-data/media/start-wizard-start-64.png)

## <a name="command-prompt"></a>Prompt dei comandi

### <a name="start-the-sql-server-import-and-export-wizard-from-the-command-prompt"></a>Avviare l'Importazione/Esportazione guidata SQL Server dal prompt dei comandi

In una finestra del prompt dei comandi eseguire **DTSWizard.exe** da una delle posizioni seguenti.

- **C:\Programmi\Microsoft SQL Server\140\DTS\Binn** per la versione a 64 bit.
  - *140* = SQL Server 2017.  Questo valore dipende dalla versione di SQL Server in uso.

- **C:\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn** per la versione a 32 bit.
  - *140* = SQL Server 2017.  Questo valore dipende dalla versione di SQL Server in uso.

Eseguire la versione a 64 bit della procedura guidata a meno che l'origine dati non richieda un provider di dati a 32 bit.

![Avviare la procedura guidata dal prompt dei comandi](../../integration-services/import-export-data/media/start-wizard-cmd.png)
  
## <a name="sql-server-management-studio-ssms"></a>SQL Server Management Studio (SSMS)

### <a name="start-the-sql-server-import-and-export-wizard-from-sql-server-management-studio-ssms"></a>Avviare l'Importazione/Esportazione guidata SQL Server da SQL Server Management Studio (SSMS)

1. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].

2. Espandere **Database**.

3. Fare clic con il pulsante destro del mouse su un database.

4. Scegliere **Attività**.

5. Fare clic su una delle opzioni seguenti.

   - **Importazione dei dati**

   - **Esportazione dei dati**  

   ![Avviare la procedura guidata da SQL Server Management Studio](../../integration-services/import-export-data/media/start-wizard-ssms.jpg) 

Se SQL Server non è installato o è installato senza SQL Server Management Studio, vedere [Scaricare SQL Server Management Studio (SSMS)](../../ssms/download-sql-server-management-studio-ssms.md).

## <a name="visual-studio"></a>Visual Studio

### <a name="start-the-sql-server-import-and-export-wizard-from-visual-studio-with-sql-server-data-tools-ssdt"></a>Avviare l'Importazione/Esportazione guidata SQL Server da Visual Studio con SQL Server Data Tools (SSDT)

 In Visual Studio con [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], eseguire una delle operazioni seguenti se è aperto un progetto di Integration Services.

- Scegliere **Importazione ed esportazione guidata di SSIS** dal menu **Progetto**.

   ![Avviare la procedura guidata da un progetto](../../integration-services/import-export-data/media/start-wizard-project.png)

   \- - oppure -

- In Esplora soluzioni fare clic con il pulsante destro del mouse sulla cartella **Pacchetti SSIS** e quindi scegliere **Importazione ed esportazione guidata di SSIS**.

    ![Avviare la procedura guidata da un pacchetto](../../integration-services/import-export-data/media/start-wizard-packages.png)

Se Visual Studio non è installato o è installato senza SQL Server Data Tools, vedere [Scaricare SQL Server Data Tools (SSDT)](../../ssdt/download-sql-server-data-tools-ssdt.md).

## <a name="get-the-wizard"></a>Ottenere la procedura guidata

Se si vuole eseguire la procedura guidata, ma [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è disponibile nel computer, è possibile installare l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installando SQL Server Data Tools (SSDT). Per altre informazioni, vedere [Scaricare SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx).

## <a name="get-help-while-the-wizard-is-running"></a>Visualizzare la Guida durante l'esecuzione della procedura guidata

> [!TIP]
> Premere il tasto F1 da qualsiasi pagina o finestra di dialogo della procedura guidata per visualizzare la documentazione relativa alla pagina corrente.   

## <a name="whats-next"></a>Quali sono le operazioni successive?

La prima pagina visualizzata all'avvio della procedura guidata è **Importazione/Esportazione guidata SQL Server**. Non è necessario eseguire alcuna operazione in questa pagina. Per altre informazioni, vedere [Importazione/Esportazione guidata SQL Server](../../integration-services/import-export-data/welcome-to-sql-server-import-and-export-wizard.md).  
  
## <a name="related-tasks-and-content"></a>Attività e argomenti correlati

Ecco alcune altre attività di base.

- **Vedere un rapido esempio sul funzionamento della procedura guidata.**

  - **Se si preferisce visualizzare screenshot.** Esaminare questo semplice esempio di una singola pagina: [Iniziare con questo semplice esempio dell'Importazione/Esportazione guidata](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md).

  - **Se si preferisce guardare un video.** Questo video di YouTube della durata di quattro minuti illustra la procedura guidata e descrive come importare ed esportare dati in Excel con istruzioni chiare e semplici: [Uso dell'Importazione/Esportazione guidata SQL Server per l'esportazione in Excel](https://go.microsoft.com/fwlink/?linkid=829049) .

  - **Altre informazioni sul funzionamento della procedura guidata.**

  - **Altre informazioni sulla procedura guidata.** Per una panoramica della procedura guidata, vedere [Importare ed esportare dati con l'Importazione/Esportazione guidata SQL Server](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).

  - **Informazioni sui passaggi della procedura guidata.** Per informazioni sui passaggi della procedura guidata, vedere [Passaggi dell'Importazione/Esportazione guidata SQL Server](../../integration-services/import-export-data/steps-in-the-sql-server-import-and-export-wizard.md). Per ogni pagina della procedura guidata è anche disponibile una pagina di documentazione separata.

  - **Informazioni su come connettersi a origini dati e destinazioni.** Se si cercano informazioni su come connettersi ai dati, selezionare la pagina desiderata nell'elenco in [Connettersi a origini dati con l'Importazione/Esportazione guidata SQL Server](../../integration-services/import-export-data/connect-to-data-sources-with-the-sql-server-import-and-export-wizard.md). È disponibile una pagina di documentazione separata per ognuna delle diverse origini dati di uso comune.