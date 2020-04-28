---
title: Installare o disinstallare il componente aggiuntivo Reporting Services per SharePoint (SharePoint 2010 e SharePoint 2013) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c2804a9a-08ea-4f4a-805d-a2c19c68733d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 63f45fa174296e4ce79985236da2d97d3f11e937
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "79289439"
---
# <a name="install-or-uninstall-the-reporting-services-add-in-for-sharepoint-sharepoint-2010-and-sharepoint-2013"></a>Installare o disinstallare il componente aggiuntivo Reporting Services per SharePoint (SharePoint 2010 e SharePoint 2013)
  Eseguire il componente aggiuntivo [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] del pacchetto di installazione per prodotti SharePoint (sprsSharePoint. msi) in server SharePoint [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per abilitare le funzionalità di in una distribuzione di SharePoint. In queste funzionalità sono inclusi Power View, una Web part Visualizzatore report, un endpoint proxy per URL, tipi di contenuto e pagine di applicazione che consentono di creare, visualizzare e gestire report, modelli di report, origini dati e altri contenuti del server di report in un sito di SharePoint. Il componente aggiuntivo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per prodotti SharePoint 2010 è un componente obbligatorio per un server di report eseguito in modalità SharePoint. È possibile installare il componente aggiuntivo mediante l'installazione guidata di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] o scaricando rsSharePoint.msi dal Feature Pack di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Per un elenco delle versioni del componente aggiuntivo e le pagine di download, vedere [Posizione in cui trovare il componente aggiuntivo Reporting Services per prodotti SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).

||
|-|
|**[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013 &#124; SharePoint 2010|

 **Contenuto dell'argomento:**

-   [Prerequisiti](#bkmk_prereq)

-   [Informazioni sull'installazione del componente aggiuntivo](#bkmk_whatinstalled)

-   [Panoramica dei metodi di installazione](#bkmk_3ways_to_install)

-   [Installare il componente aggiuntivo utilizzando il file di installazione rsSharePoint. msi](#bkmk_install_rssharepoint)

    -   [Installazione di tipo "solo file"](#bkmk_files_only_installation)

-   [Procedura: Rimozione del componente aggiuntivo di Reporting Services](#bkmk_remove_addin)

-   [Procedura: Ripristino di rssharepoint.msi dalla riga di comando](#bkmk_repair)

-   [File di log del programma di installazione](#bkmk_logfiles)

-   [Aggiornamento](#bkmk_upgrade)

-   [rsCustomAction.exe](#bkmk_rscustomaction)

##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> Prerequisiti
 L'installazione del componente aggiuntivo di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] rappresenta uno dei diversi passaggi necessari per l'integrazione di un server di report in un'istanza di un prodotto SharePoint. Per altre informazioni sul set di requisiti completo per l'utilizzo della modalità SharePoint, vedere [Hardware and Software Requirements for Reporting Services in SharePoint Mode](../../../2014/sql-server/install/hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode.md). Per ulteriori informazioni sull'installazione e la [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]configurazione di, vedere [Install Reporting Services SharePoint Mode for SharePoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md).

-   Se si integra [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in una farm di SharePoint in cui sono presenti più applicazioni front-end Web, installare il componente aggiuntivo in ogni computer nella farm in cui è presente un server front-end Web. Eseguire questa operazione solo per i front-end Web che verranno utilizzati per accedere al contenuto del server di report.

-   Per installare il componente aggiuntivo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è necessario essere un amministratore del computer. Se, ad esempio, si eseguirà rsSharePoint.msi al prompt dei comandi, è consigliabile aprire il prompt con i privilegi di amministratore utilizzando l'opzione **Esegui come amministratore** .

-   Per installare il componente aggiuntivo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , è necessario essere un membro del gruppo di amministratori della farm di SharePoint.

-   È necessario essere un amministratore della raccolta siti per attivare la funzionalità di integrazione con [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .

-   Per i diagrammi di distribuzioni di esempio con il componente aggiuntivo, vedere [topologie di distribuzione per SQL Server le funzionalità di business intelligence in SharePoint](../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).

##  <a name="what-does-the-add-in-install"></a><a name="bkmk_whatinstalled"></a>Che cosa comporta l'installazione del componente aggiuntivo?
 Il processo di installazione del componente aggiuntivo è costituito da due fasi. Entrambe vengono completate automaticamente al termine di un'installazione standard:

-   La prima fase consiste nell'installazione dei file nelle cartelle appropriate. Si tratta di cartelle standard per le distribuzioni di SharePoint. Uno dei file installati è rsCustomAction.exe.

-   La seconda fase dell'installazione consiste nell'esecuzione di un set di azioni personalizzate che consente di registrare i file [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] con SharePoint. Le azioni personalizzate vengono eseguite da rsCustomAction.exe. Il file exe viene rimosso al termine dell'installazione in due fasi. È possibile eseguire un'installazione di tipo **"solo file"** ; in questo caso rsCustomAction.exe non viene eseguito e alla fine dell'installazione non viene rimosso dall'unità.

## <a name="the-reporting-services-installation-order"></a>Ordine dell'installazione di Reporting Services
 È possibile installare il componente aggiuntivo prima o dopo l'installazione di SharePoint. L'installazione del componente aggiuntivo segue gli standard di pre-distribuzione di SharePoint e installa file nei percorsi utilizzati dall'installazione di SharePoint.

> [!NOTE]
>  Il vantaggio di installare il componente aggiuntivo prima dei prodotti SharePoint consiste nel fatto che se alla farm vengono aggiunti nuovi server, il componente aggiuntivo Reporting Services verrà configurato e attivato dalla farm di SharePoint.

 **SharePoint 2010**

-   Lo strumento di preparazione prodotti SharePoint 2010 installa la versione [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] del componente aggiuntivo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] è inclusa una nuova versione di questo componente aggiuntivo richiesta per le funzionalità di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].

     Se si esegue l'Utilità preparazione prodotti SharePoint, è necessario comunque installare la versione [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] del componente aggiuntivo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].

-   Se prima si installa la versione [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] del componente aggiuntivo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], quando si esegue l'Utilità preparazione prodotti SharePoint verrà visualizzata la finestra di dialogo riportata di seguito. In essa viene indicato che la versione precedente del componente aggiuntivo non è stata installata dall'utilità in questione poiché è stata rilevata una versione più recente. Tale comportamento è previsto.

     ![Il componente aggiuntivo SSRS è già installato.](../../../2014/sql-server/install/media/rs-sharepointprereq-complete.gif "Il componente aggiuntivo SSRS è già installato.")

 **SharePoint 2013**

 Lo strumento di preparazione prodotti SharePoint 20103 **non** installa il [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] componente aggiuntivo per prodotti SharePoint.

##  <a name="overview-of-the-installation-methods"></a><a name="bkmk_3ways_to_install"></a> Panoramica sui metodi di installazione
 Il [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] componente aggiuntivo per prodotti SharePoint può essere installato utilizzando uno dei due metodi seguenti:

-   **Installazione guidata:** ![si noti](../../../2014/reporting-services/media/rs-fyinote.png "nota") [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]che il componente aggiuntivo può essere installato mediante l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installazione guidata di. Scegliere **Componente aggiuntivo Reporting Services per prodotti SharePoint** nella pagina **Selezione funzionalità** della procedura guidata.

-   **rsSharepoint.msi:** il file del componente aggiuntivo può essere installato direttamente dal supporto di installazione o scaricato e installato. Il file rsSharepoint.msi supporta sia l'installazione tramite interfaccia utente grafica che quella da riga di comando. È necessario eseguire il file con estensione msi con privilegi di amministratore aprendo innanzitutto una finestra del prompt dei comandi con autorizzazioni elevate ed eseguendo quindi rsSharepoint.msi dalla riga di comando. Per altre informazioni, vedere [Posizione in cui trovare il componente aggiuntivo Reporting Services per prodotti SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).

    > [!NOTE]
    >  Se si usa l'opzione **/q** per un'installazione da riga di comando invisibile all'utente, il contratto di licenza con l'utente finale non viene visualizzato. Indipendentemente dal metodo di installazione, l'utilizzo di questo software è governato da un contratto di licenza e l'utente è tenuto a rispettarlo.

##  <a name="install-the-add-in-using-the-installation-file-rssharepointmsi"></a><a name="bkmk_install_rssharepoint"></a> Installare il componente aggiuntivo utilizzando il file di installazione rsSharePoint.msi
 In questa sezione vengono fornite informazioni relative all'installazione diretta di rssharepoint.msi, mediante l'installazione guidata msi o un'installazione da riga di comando. Se il componente aggiuntivo è stato installato utilizzando l'installazione guidata di SQL Server, non è necessario effettuare i passaggi riportati di seguito.

 È possibile visualizzare un elenco completo di opzioni della riga di comando eseguendo il comando seguente:

```
Rssharepoint.msi /?
```

1.  Scaricare il programma di installazione`rsSharepoint.msi`() per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] il componente aggiuntivo. Per altre informazioni, vedere [Posizione in cui trovare il componente aggiuntivo Reporting Services per prodotti SharePoint](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).

2.  Eseguire `rsSharepoint.msi` come amministratore per avviare l'Installazione guidata. Verranno visualizzati una pagina iniziale, le condizioni di licenza software e una pagina contenente le informazioni per la registrazione. Durante l'installazione, le cartelle vengono create nel percorso indicato di seguito e i file vengono copiati in tali cartelle:

     `%program files%\common files\Microsoft Shared\Web Server Extensions\14\`

     o

     `%program files%\common files\Microsoft Shared\Web Server Extensions\15\`

3.  Nell'Amministrazione centrale SharePoint configurare le impostazioni e l'attivazione delle funzionalità del server di report. . Per ulteriori informazioni sull'installazione e sulla [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] configurazione della modalità SharePoint di, vedere [Install Reporting Services SharePoint mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).

###  <a name="files-only-installation"></a><a name="bkmk_files_only_installation"></a>Installazione di solo file
 Per installare i file ignorando la fase di installazione delle azioni personalizzate, eseguire rssharepoint.msi dalla riga di comando con l'opzione SKIPCA:

1.  Aprire un prompt dei comandi **con autorizzazioni di amministratore**.

2.  Eseguire il comando seguente:

    ```cmd
    Msiexec.exe /i rsSharePoint.msi SKIPCA=1
    ```

 L'interfaccia utente dell'installazione viene visualizzata ed eseguita normalmente. Il file `rsCustomAction.exe` viene installato. Tuttavia, il file .exe non viene eseguito al termine dell'installazione e `rsCustomAction.exe` rimane sul computer.

### <a name="use-a-two-step-installation-to-troubleshoot-installation-issues-or-install-the-content-types"></a>Usare un'installazione in due passaggi per risolvere i problemi di installazione o installare i tipi di contenuto
 Se si verificano errori durante l'installazione o se non vengono visualizzati i tipi di contenuto di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nelle impostazioni di raccolta documenti, sarà possibile eseguire l'installazione come processo in due passaggi dalla riga di comando:

1.  Aprire un prompt dei comandi **con autorizzazioni di amministratore** ed eseguire un'installazione di tipo "solo file" come descritto nella sezione precedente.

2.  Eseguire il file eseguibile di azioni personalizzate:

    1.  Passare alla cartella in cui è incluso il file `rsCustomAction.exe`. Questo file viene copiato nel computer dal programma di installazione di tipo " solo file " del componente aggiuntivo. `rsCustomAction.exe`si trova nella directory **% Temp%** . Per passare al file, al prompt dei comandi digitare:

         **CD %temp%**.

         Il file si trova in: **\Users\\<nome utente\>\AppData\Local\Temp**

    2.  Digitare il comando seguente. Il completamento di questo passaggio di configurazione richiede alcuni minuti. Durante questo processo verrà riavviato il servizio W3SVC. Verranno memorizzati diversi messaggi di stato durante la copia dei file, la registrazione dei componenti e l'esecuzione della Configurazione guidata del prodotto SharePoint.

        ```cmd
        rsCustomAction.exe /i
        ```

    3.  La quantità di tempo necessaria per rendere effettive le modifiche varia a seconda dell'ambiente server. È inoltre possibile eseguire **iisreset** per forzare un aggiornamento più rapido.

### <a name="quiet-installation-for-scripting"></a>Installazione non interattiva per lo scripting
 È possibile utilizzare le opzioni **/q** o **/quiet** per un'installazione "non interattiva" in cui non vengono visualizzate finestre di dialogo o avvisi. L'installazione non interattiva è utile se si desidera creare uno script dell'installazione del componente aggiuntivo.

> [!NOTE]
>  Se si usa l'opzione **/q** per un'installazione da riga di comando invisibile all'utente, il contratto di licenza con l'utente finale non viene visualizzato. Indipendentemente dal metodo di installazione, l'utilizzo di questo software è governato da un contratto di licenza e l'utente è tenuto a rispettarlo.

 Per eseguire un'installazione non interattiva:

1.  Aprire un prompt dei comandi **con autorizzazioni di amministratore**.

2.  Eseguire il comando seguente:

    ```cmd
    Msiexec.exe /i rsSharePoint.msi /q
    ```

##  <a name="how-to-remove-the-reporting-services-add-in"></a><a name="bkmk_remove_addin"></a>Come rimuovere il componente aggiuntivo Reporting Services
 È possibile disinstallare il componente aggiuntivo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per prodotti SharePoint dal Pannello di controllo o dalla riga di comando di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.

1.  Se si utilizza il Pannello di controllo verrà eseguita una disinstallazione completa dei file nel computer corrente **E** verranno rimossi l'oggetto e le funzionalità di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dalla farm di SharePoint. Quando l'oggetto e le funzionalità di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] vengono rimossi, non sarà più possibile verificare e aggiornare i report.

2.  Il metodo della riga di comando per disinstallare il componente aggiuntivo consente all'utente di usare il parametro LocalOnly per rimuovere solo i file del componente aggiuntivo dal computer locale, mentre l'oggetto e le funzionalità di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nella farm non saranno modificati.

 Durante la disinstallazione del componente aggiuntivo verranno rimosse anche le funzionalità di integrazione del server utilizzate per l'elaborazione di report in un server di report. Verranno inoltre rimosse le pagine di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] da Amministrazione centrale SharePoint e le altre pagine personalizzate di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . È possibile rimuovere anche tutti i report e gli altri elementi del server di report non più utilizzati nei siti di SharePoint interessati che non potranno più essere eseguiti dopo la disinstallazione del componente aggiuntivo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .

 Per disinstallare il componente aggiuntivo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], è necessario disporre di un'installazione di [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] o [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] ancora in esecuzione. Se si disinstalla prima SharePoint 2010, per disinstallare il componente aggiuntivo di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sarà necessario reinstallarlo.

 Per disinstallare il componente aggiuntivo, è possibile usare la stessa procedura sia nei server autonomi che nelle server farm. Verranno rimossi tutti i file di programma e le impostazioni di configurazione aggiunti durante l'installazione.

 La disinstallazione del componente aggiuntivo non comporterà la rimozione degli elementi seguenti:

-   Account di accesso creati per l'account del servizio del server di report utilizzato per accedere ai database di configurazione e del contenuto di SharePoint. È necessario eliminare tutti gli account di accesso per l'account del servizio del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] server di report dall'istanza di utilizzata per ospitare i database di SharePoint.

-   Autorizzazioni o gruppi creati per gli utenti dei report. Se sono stati creati livelli di autorizzazione personalizzati o gruppi di SharePoint per consentire l'accesso alle funzionalità del server di report, sarà necessario revocare tutte le autorizzazioni non più necessarie.

-   File di dati caricati nelle raccolte di SharePoint, inclusi i file di definizione dei report (con estensione rdl), i file delle origini dati condivise (con estensione sds) e i file degli elementi dei report pubblicati (con estensione rsc). Tali file non vengono eliminati, ma non potranno più essere eseguiti. I file dovranno essere eliminati manualmente.

-   Il programma di installazione non elimina il database del server di report né modifica l'istanza del server di report utilizzata per le operazioni in modalità integrata.

### <a name="to-uninstall-from-windows-control-panel"></a>Per eseguire la disinstallazione dal Pannello di controllo di Windows
 Per avviare la procedura guidata dal Pannello di controllo di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows e rimuovere il componente aggiuntivo:

1.  In **Programmi**nel Pannello di controllo selezionare **Disinstalla un programma**

2.  Selezionare **Componente aggiuntivo Microsoft SQL Server RS per SharePoint**. È inoltre possibile avviare la disinstallazione guidata eseguendo **rssharepoint.msi** dal prompt dei comandi senza opzioni.

3.  Scegliere **Rimuovi**.

### <a name="uninstall-from-the-command-line"></a>Eseguire la disinstallazione dalla riga di comando
 Per disinstallare il componente aggiuntivo dalla riga di comando:

1.  Aprire un prompt dei comandi **con autorizzazioni di amministratore**.

2.  Eseguire il comando seguente:

    ```cmd
    msiexec.exe /uninstall rsSharePoint.msi
    ```

3.  Verrà visualizzata una finestra di messaggio di conferma. Fare clic su **Sì**.

### <a name="uninstall-the-add-in-from-the-local-server-only"></a>Disinstallare il componente aggiuntivo solo dal server locale
 Con metodi di disinstallazione del componente aggiuntivo illustrati sarà possibile rimuovere le funzionalità e l'oggetto di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dalla farm. Se si dispone di una farm multiserver e si desidera disinstallare il componente aggiuntivo solo dal computer locale lasciando la farm di SharePoint in uno stato funzionale, completare i passaggi seguenti:

1.  Aprire un prompt dei comandi **con autorizzazioni di amministratore**.

2.  Eseguire il comando seguente:

    ```cmd
    Msiexec.exe /uninstall rsSharePoint.msi LocalOnly=1
    ```

 Questa operazione consente di annullare la registrazione dei componenti di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] da SharePoint e rimuovere i file unicamente per il computer locale.

 Per annullare la registrazione delle funzionalità di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] da SharePoint senza rimuovere i file dal disco, per utilizzarli in un secondo momento, completare i passaggi seguenti:

1.  Aprire un prompt dei comandi **con autorizzazioni di amministratore**.

2.  Eseguire il comando seguente:

    ```cmd
    rsCustomAction.exe /p
    ```

 I passaggi precedenti presuppongono il completamento di un'installazione del file con estensione msi con SkipCA=1 e la disponibilità del file rscusstomaction.exe. Per altre informazioni, vedere la sezione relativa all'installazione di tipo "solo file".

##  <a name="how-to-repair-rssharepointmsi-from-the-command-line"></a><a name="bkmk_repair"></a>Come ripristinare rsSharepoint. msi dalla riga di comando
 Per ripristinare o disinstallare il componente aggiuntivo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilizzando la riga di comando, completare i passaggi seguenti:

1.  Aprire un prompt dei comandi **con autorizzazioni di amministratore**.

2.  Eseguire il comando seguente:

    ```cmd
    msiexec.exe /f rssharepoint.msi
    ```

##  <a name="setup-log-files"></a><a name="bkmk_logfiles"></a>File di log del programma di installazione
 Durante l'esecuzione, il programma di installazione consente di registrare le informazioni in un file di log nella cartella **%temp%** per l'utente che ha installato il componente aggiuntivo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Ad esempio **c:\Users\\<nomeutente\>\AppData\Local\Temp**. Il nome del file è **RS_SP_\<numero>.log**, ad esempio **RS_SP_0.log**. Tutti gli errori nel log iniziano con la stringa "SSRSCustomActionError".

> [!NOTE]
>  AppData è una cartella nascosta del sistema operativo Windows. Potrebbe essere necessario modificare le impostazioni delle cartelle di Esplora risorse per poter visualizzare file e cartelle nascosti.

#### <a name="view-a-log-file-with-windows-notepad"></a>Visualizzare un file di log con il Blocco note di Windows

1.  I comandi seguenti permettono di modificare il percorso del prompt dei comandi, elencare i file di log rs e quindi aprire uno dei file con il Blocco note di Windows:

    ```cmd
    cd %temp%
    ```

    ```cmd
    dir rs_sp*.log
    ```

    ```cmd
    notepad rs_sp_3.log
    ```

#### <a name="view-a-log-file-with-powershell"></a>Visualizzare un file di log con PowerShell

1.  Digitare il comando seguente nella shell di gestione SharePoint per ottenere un elenco filtrato di righe del file contenenti "ssrscustomactionerror":

    ```powershell
    Get-Content -Path C:\Users\<UserName\AppData\Local\Temp\rs_sp_0.log | Select-String "ssrscustomactionerror"
    ```

2.  Il risultato sarà simile al seguente:

     `2011-05-23 12:40:12: SSRSCustomActionError: SharePoint is installed, but not configured`.

##  <a name="upgrade"></a><a name="bkmk_upgrade"></a>Aggiornamento
 Se si dispone di un'installazione esistente del componente aggiuntivo di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , è possibile eseguire l'aggiornamento alla versione corrente. Durante l'installazione del componente aggiuntivo verrà rilevata la versione esistente e verrà richiesto di confermare l'aggiornamento. Il messaggio sarà simile al seguente:

 **Nel sistema è stata rilevata una versione precedente di questo prodotto. Aggiornare l'installazione esistente?**

 In caso di conferma, la versione precedente del componente aggiuntivo verrà rimossa e verrà quindi installata la nuova versione.

 Il componente aggiuntivo di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] non è specifico dell'istanza. In un computer è possibile installare una sola istanza del componente aggiuntivo. Non è consentita l'esecuzione side-by-side di versioni differenti con la versione corrente.

##  <a name="rscustomactionexe"></a><a name="bkmk_rscustomaction"></a>RsCustomAction. exe
 Nella tabella seguente vengono riepilogate le opzioni di rscustomaction.exe:

|Opzione|Descrizione|
|------------|-----------------|
|i|Installazione delle azioni personalizzate. Consente di registrare i componenti di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint. W3SVCservice verrà riavviato.|
|r|Repair|
|u|Disinstallazione. Consente di annullare la registrazione dei componenti di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dall'intera farm di SharePoint, senza rimuovere i file dal disco. W3SVCservice verrà riavviato.|
|p|Disinstallazione locale. Consente di annullare la registrazione dei componenti di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] unicamente dal computer locale. I file non verranno rimossi dal disco. W3SVCservice verrà riavviato.|
|t|Solo SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 2005. L'opzione consente di verificare se il server di report dispone di una connessione funzionante al database del server di report.|

## <a name="configuring-reporting-services"></a>Configurazione di Reporting Services
 Una volta installato il componente aggiuntivo in tutti i computer necessari, è necessario configurare il server di report da Amministrazione centrale SharePoint. I passaggi necessari dipendono dall'ordine con il quale sono state installate le diverse tecnologie. Per ulteriori informazioni, vedere [Install Reporting Services modalità SharePoint per sharepoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) e [Reporting Services report server &#40;modalità SharePoint&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)

## <a name="see-also"></a>Vedere anche
 [Installare Reporting Services modalità SharePoint per sharepoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) [Reporting Services Server di report &#40;modalità SharePoint&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)
