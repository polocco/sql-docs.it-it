---
title: Gestione report (modalità nativa SSRS) | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: reporting-services-native
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 04/26/2019
ms.openlocfilehash: 5cefc88469ac3c98f3bb944c0e490f1ce7e88472
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "78172385"
---
# <a name="report-manager--ssrs-native-mode"></a>Gestione report (modalità nativa SSRS)
  Gestione report è uno strumento di gestione e accesso ai report basato sul Web che consente di amministrare una singola istanza del server di report da una postazione remota su una connessione HTTP. e offre funzionalità di visualizzatore di report e di navigazione. In questo argomento

-   [Definizione di Gestione report](#bkmk_whatis_report_manager)

-   [Avviare e utilizzare Gestione report](#bkmk_start_report_manager)

-   [Descrizioni delle icone](#bkmk_icon_descriptions)

##  <a name="what-is-report-manager"></a><a name="bkmk_whatis_report_manager"></a>Che cos'è Gestione report?
 È possibile utilizzare Gestione report per eseguire le attività seguenti:

-   Visualizzare, ricercare, stampare e sottoscrivere report.

-   Creare, proteggere e gestire la gerarchia di cartelle per organizzare gli elementi presenti nel server.

-   Configurare la sicurezza basata sui ruoli dalla quale dipende l'accesso a elementi e operazioni.

-   Configurare le proprietà di esecuzione del report, la cronologia del report e i parametri del report.

-   Creazione di modelli di report che si connettono e [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] recuperano dati da un' [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] origine dati o da un'origine dati relazionale.

-   Impostare la sicurezza degli elementi di un modello per consentire l'accesso a entità specifiche del modello o per eseguire il mapping delle entità a report click-through predefiniti creati in precedenza.

-   Creare pianificazioni condivise e origini dei dati condivise per migliorare la gestione delle pianificazioni e delle connessioni alle origini dei dati.

-   Creare sottoscrizioni guidate dai dati che consentono di implementare i report in un elenco di destinatari di grandi dimensioni.

-   Creare report collegati per riutilizzare e ridefinire gli scopi di un report esistente in modi diversi.

-   Avviare Generatore report per creare report da salvare ed eseguire nel server di report.

 È possibile utilizzare Gestione report per esplorare le cartelle del server di report o cercare report specifici. È possibile visualizzare un report, le sue proprietà generali e vecchie copie del report acquisite nella cronologia del report. A seconda delle autorizzazioni di cui si dispone, potrebbe inoltre essere possibile sottoscrivere report per il recapito in una casella di posta elettronica o in una cartella condivisa nel file system.

> [!NOTE]
>  Per informazioni sulle versioni e i browser supportati, vedere [Planning for Reporting Services e Power View Browser Support &#40;Reporting Services 2014&#41;](../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md).

 Gestione report viene utilizzato solo per un server di report in esecuzione in modalità nativa. Non è supportato per un server di report configurato per la modalità integrata SharePoint.

 Alcune funzionalità di Gestione report sono disponibili solo in determinate edizioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Per ulteriori informazioni, vedere [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).

 In una nuova installazione solo gli amministratori locali dispongono di autorizzazioni sufficienti per utilizzare il contenuto e le impostazioni. Per concedere le autorizzazioni agli altri utenti, un amministratore locale deve creare le assegnazioni di ruolo appropriate per gestire l'accesso al server di report. Le pagine dell'applicazione e le operazioni che saranno in seguito disponibili per un utente dipendono dalle assegnazioni di ruolo di tale utente. Per ulteriori informazioni, vedere [concedere l'accesso utente a un server di Report &#40;Gestione report&#41;](security/grant-user-access-to-a-report-server.md).

 Se si utilizza [!INCLUDE[wiprlhlong](../includes/wiprlhlong-md.md)] o Windows Server 2008, è necessario configurare Gestione report per l'amministrazione locale. Per altre informazioni, vedere [Configurare un server di report in modalità nativa per gli amministratori locali &#40;SSRS&#41;](report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).

##  <a name="start-and-use-report-manager"></a><a name="bkmk_start_report_manager"></a>Avviare e utilizzare Gestione report
 Gestione report è un'applicazione Web che si apre digitando l'apposito URL nella barra degli indirizzi di una finestra del browser. Quando si avvia Gestione report, le pagine, le opzioni e i collegamenti visualizzati variano in base alle autorizzazioni di cui si dispone sul server di report. Per eseguire un'attività, è necessario essere assegnato a un ruolo che include l'attività. Gli utenti assegnati a un ruolo con autorizzazioni complete hanno accesso a tutti i menu e le pagine disponibili per la gestione di un server di report. Un utente assegnato a un ruolo autorizzato a visualizzare ed eseguire i report, invece, potrà visualizzare solo le pagine e i menu correlati a queste attività specifiche. Per ogni utente è possibile impostare assegnazioni di ruolo diverse per server di report diversi o anche per le varie cartelle e i vari report archiviati in un singolo server di report.

 Per altre informazioni sui ruoli, vedere [Concessione di autorizzazioni in un server di report in modalità nativa](security/granting-permissions-on-a-native-mode-report-server.md).

> [!NOTE]
>  Se si utilizza Windows Vista o Windows Server 2008, sarà necessario configurare il server di report per l'amministrazione locale prima di poter utilizzare Gestione report per gestire un'istanza del server di report locale. Per istruzioni su come configurare il server, vedere [configurare un server di report in modalità nativa per l'amministrazione locale &#40;&#41;SSRS ](report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).

## <a name="start-report-manager"></a>Avviare Gestione report

#### <a name="to-start-report-manager-from-a-browser"></a>Per avviare Gestione report da un browser

1.  Aprire [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer 7.0 o versione successiva.

2.  Nella barra degli indirizzi del browser digitare l'URL di Gestione report.

    -   L'URL predefinito è `http://[ComputerName]/reports`.

    -   Il server di report potrebbe essere configurato per l'utilizzo di una porta specifica. Ad esempio, `http:// [ComputerName]:80/reports` o `http:// [ComputerName]:8080/reports`.

## <a name="configuring-report-manager"></a>Configurazione di Gestione report
 La configurazione di Gestione report consiste nel definire un URL per l'applicazione. Se la distribuzione include l'esecuzione di Gestione report in un server distinto, è necessaria una configurazione aggiuntiva.

 Non esistono molti modi per personalizzare Gestione report. Ad esempio, è possibile modificare il titolo dell'applicazione nella pagina Impostazioni sito. Gli sviluppatori Web possono modificare i fogli di stile che contengono le informazioni sullo stile utilizzate da Gestione report. Poiché Gestione report non è progettato specificamente per supportare la personalizzazione, è necessario testare accuratamente tutte le modifiche apportate. Se Gestione report non soddisfa le proprie esigenze, è possibile sviluppare un visualizzatore di report personalizzato oppure configurare web part di SharePoint per individuare e visualizzare i report in un sito di SharePoint. Per altre informazioni, vedere [Configurare Gestione report &#40;modalità nativa&#41;](report-server/configure-web-portal.md).

##  <a name="icon-descriptions"></a><a name="bkmk_icon_descriptions"></a>Descrizioni delle icone
 Nella tabella seguente vengono descritte le icone utilizzate in Gestione report. Per ulteriori informazioni sulle icone visualizzate nella barra degli strumenti dei report, vedere [Visualizzatore HTML e barra degli strumenti dei report](html-viewer-and-the-report-toolbar.md).

|Icona|Descrizione|Azione|
|----------|-----------------|------------|
|![Icona di report](media/hlp-16doc.gif "Icona di report")|Report|Fare clic sul nome o sull'icona del report per aprire il report. Il report viene aperto in una finestra separata.|
|![Icona modello](media/model-icon.gif "Icona di modello")|Modello di report|Fare clic sull'icona del modello di report per aprire la pagina delle proprietà del modello.|
|![Icona di report collegato](media/hlp-16linked.gif "Icona di report collegato")|Report collegato|Fare clic sull'icona o sul nome del report collegato per aprirlo. Il report viene aperto in una finestra separata.|
|![Icona Cartella](media/hlp-16folder.gif "Icona Cartella")|Cartella|Fare clic sull'icona o sul nome della cartella per aprirla.|
|![Icona di sottoscrizione](media/hlp-16subscription.gif "Icona di sottoscrizione")|Subscription|Fare clic sull'icona o sulla descrizione della sottoscrizione per modificarla.|
|![Icona della sottoscrizione guidata dai dati](media/hlp-16subscriptiondd.gif "Icona della sottoscrizione guidata dai dati")|Sottoscrizione guidata dai dati|Fare clic sull'icona o sulla descrizione della sottoscrizione guidata dai dati per modificarla.|
|![Icona di risorsa generica](media/hlp-16file.gif "Icona di risorsa generica")|Risorsa|Fare clic sull'icona o sul nome della risorsa per aprirla. La risorsa viene aperta in una finestra separata.|
|![Icona Origine dati condivisa](media/hlp-16datasource.png "Icona Origine dati condivisa")|Origine dei dati condivisa|Fare clic sull'icona di un'origine dei dati condivisa per aprire le pagine delle proprietà, l'elenco dei report e l'elenco delle sottoscrizioni per l'origine dei dati.|
|![Icona della pagina delle proprietà](media/hlp-16prop.gif "Icona della pagina delle proprietà")|Pagina delle proprietà|Fare clic sull'icona della pagina delle proprietà per accedere a pagine aggiuntive per l'impostazione di proprietà e opzioni di sicurezza.|

## <a name="see-also"></a>Vedere anche

- [Configurare un URL &#40;Gestione configurazione SSRS&#41;](install-windows/configure-a-url-ssrs-configuration-manager.md)
- [Pianificazione del supporto per Reporting Services e Power View browser &#40;Reporting Services 2014&#41;](../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md)
- [Generatore report &#40;SSRS&#41;](tools/report-builder-authoring-environment-ssrs.md)
- - [Strumenti di Reporting Services](tools/reporting-services-tools.md)
- [Gestione dei contenuti del server di report &#40;la modalità nativa di SSRS&#41;](report-server/report-server-content-management-ssrs-native-mode.md) 
 [Gestione report Guida sensibile](../../2014/reporting-services/report-manager-f1-help.md) al contesto