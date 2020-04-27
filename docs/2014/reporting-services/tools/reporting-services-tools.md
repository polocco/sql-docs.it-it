---
title: Strumenti di Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SSRS, tools
- Reporting Services, tools
- components [Reporting Services]
- components [Reporting Services], about components
- Reporting Services, components
- SSRS, components
- reports [Reporting Services], tools
- SQL Server Reporting Services, components
- SQL Server Reporting Services, tools
- architecture [Reporting Services]
ms.assetid: 23d616e3-eb90-43fb-9b7a-869bd7e22e7b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 21c56f28a6f65b22d8fe334a1046f44f868c4453
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66099906"
---
# <a name="reporting-services-tools"></a>Strumenti di Reporting Services
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] contiene un set di strumenti grafici e di scripting che supportano lo sviluppo e l'uso di report completi in un ambiente gestito. Il set include strumenti di sviluppo, strumenti di configurazione e amministrazione e strumenti per la visualizzazione di report. In questo argomento viene fornita una breve panoramica di ogni strumento di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e di come è possibile accedervi.  
  
 Per trovare rapidamente uno strumento, vedere [Esercitazione: Individuazione e avvio degli strumenti di Reporting Services &#40;SSRS&#41;](tutorial-how-to-locate-and-start-reporting-services-tools-ssrs.md).  
  
## <a name="tools-for-report-authoring"></a>Strumenti per la creazione di report  
 La tabella seguente elenca gli strumenti disponibili per la creazione di report in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
|Strumento|Descrizione|Modalità di accesso|  
|----------|-----------------|-------------------|  
|[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]|Un'esperienza interattiva di esplorazione e presentazione visiva dei dati progettata per consentire la creazione e l'interazione con i report basati sui modelli tabulari di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .<br /><br /> Nota: richiede [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in modalità SharePoint.|Browser con Silverlight.|  
|Progettazione report|Utilizzare questo strumento per progettare report e per distribuirli in un server di report in modalità nativa o in modalità SharePoint.<br /><br /> Ospitato in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<br /><br /> Riquadro dei dati del report per organizzare i dati utilizzati nel report<br /><br /> Visualizzazioni a schede per la progettazione e l'anteprima per una progettazione dei report interattiva<br /><br /> Finestre di progettazione query che consentono di specificare i dati da recuperare dalle origini dati associati ai tipi di origini dati nel [file di configurazione RSReportDesigner](../report-server/rsreportdesigner-configuration-file.md)<br /><br /> Editor espressioni con supporto IntelliSense per compilare le espressioni di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] che consentono di personalizzare il contenuto e l'aspetto del report.<br /><br /> Supporta gli elementi del report personalizzati e le finestre Progettazione query personalizzate<br /><br /> <br /><br /> Per altre informazioni, vedere [Reporting Services in SQL Server Data Tools &#40;SSDT&#41;](reporting-services-in-sql-server-data-tools-ssdt.md).|[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]|  
|Generatore report|Utilizzare questo strumento per progettare report e per distribuirli in un server di report in modalità nativa o in modalità SharePoint.<br /><br /> [!INCLUDE[msCoName](../../includes/msconame-md.md)] Ambiente di creazione simile a Office<br /><br /> Possibilità di salvare elementi del report come parti di report<br /><br /> Una procedura guidata per la creazione di mappe<br /><br /> Aggregazioni di aggregazioni<br /><br /> Supporto migliorato per le espressioni<br /><br /> Finestre Progettazione query che consentono di specificare i dati da recuperare da una selezione di tipi di origini dati predefiniti<br /><br /> <br /><br /> Per ulteriori informazioni, vedere [Generatore report &#40;&#41;SSRS ](report-builder-authoring-environment-ssrs.md).|Scaricare il file MSI o aprirlo da Gestione report/SharePoint|  
  
## <a name="tools-for-report-server-administration"></a>Strumenti per l'amministrazione del server di report  
 È disponibile un set di strumenti grafici e di scripting per l'amministrazione del server di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]report in. Gli strumenti utilizzati dipendono dalla modalità di distribuzione del server di report.  
  
### <a name="native-mode"></a>Modalità nativa  
 Nella tabella seguente vengono elencati gli strumenti disponibili per l'amministrazione del server di report distribuito in modalità nativa.  
  
|Strumento|Descrizione|Modalità di accesso|  
|----------|-----------------|-------------------|  
|Gestione configurazione Reporting Services|Utilizzare questo strumento per configurare un'installazione di Reporting Services. Si noti che il Configuration Manager Reporting Services non consente di gestire il contenuto del server di report, abilitare funzionalità aggiuntive o concedere l'accesso al server. Le attività disponibili includono:<br /><br /> Configurazione sia delle istanze locali che remote del server di report.<br /><br /> Configurazione dell'account del servizio del server di report.<br /><br /> Creazione e configurazione di uno o più URL del servizio Web.<br /><br /> Configurazione dell'URL di Gestione report.<br /><br /> Creazione e configurazione del database del server di report.<br /><br /> Configurazione di una distribuzione con scalabilità orizzontale.<br /><br /> Backup, ripristino o sostituzione della chiave simmetrica utilizzata per crittografare stringhe di connessione e credenziali archiviate.<br /><br /> Configurazione dell'account di esecuzione automatica.<br /><br /> Configurazione di un server SMTP per il recapito tramite posta elettronica.<br /><br /> <br /><br /> Per altre informazioni, vedere [Gestione configurazione Reporting Services &#40;modalità nativa&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).|Menu Start|  
|SQL Server Management Studio|Utilizzare questo strumento per gestire una o più istanze del server di report in un unico ambiente, incluse le seguenti attività:.<br /><br /> Gestione sia delle istanze locali che remote del server di report<br /><br /> Impostazione delle proprietà del server di report<br /><br /> Modifica di definizioni di ruolo<br /><br /> Disabilitazione delle caratteristiche del server di report non utilizzate<br /><br /> Gestione di processi<br /><br /> Gestione di pianificazioni condivise|Menu Start|  
|Gestione configurazione SQL Server|Utilizzare questo strumento per eseguire le operazioni seguenti:<br /><br /> Avviare e arrestare i servizi Windows per Reporting Services<br /><br /> Configurare Segnalazione commenti e suggerimenti utenti, il percorso della directory dei dump e la segnalazione errori.<br /><br /> <br /><br /> ** \* Avviso di \* \* ** Non utilizzare questo strumento per configurare l'account del servizio. Utilizzare invece lo strumento di configurazione di Reporting Services.<br /><br /> Per altre informazioni, vedere [Gestione configurazione SQL Server](../../relational-databases/sql-server-configuration-manager.md).|Menu Start|  
|Utilità rsconfig|Utilizzare questo strumento per configurare e gestire una connessione del server di report al database del server di report. È inoltre possibile utilizzarla per specificare un account utente per l'elaborazione automatica dei report.<br /><br /> Per altre informazioni, vedere [Utilità della riga di comando del server di report &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md).|Prompt dei comandi|  
|Utilità rskeymgmt|Utilizzare questo strumento per eseguire le operazioni seguenti:<br /><br /> Estrarre, ripristinare, creare ed eliminare la chiave simmetrica utilizzata per crittografare i dati del server di report.<br /><br /> Creare un join delle istanze del server di report in una distribuzione con scalabilità orizzontale.<br /><br /> <br /><br /> Per altre informazioni, vedere [Utilità della riga di comando del server di report &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md).|Prompt dei comandi|  
|Classi di Strumentazione gestione Windows (WMI)|Utilizzare queste classi per automatizzare le attività di configurazione in Gestione configurazione Reporting Services senza che sia necessario utilizzare l'interfaccia utente grafica.<br /><br /> Per altre informazioni, vedere [Accesso al provider WMI a livello di programmazione](../accessing-the-wmi-provider-programmatically.md).|Visual Basic Script|  
  
### <a name="sharepoint-integrated-mode"></a>Modalità integrata SharePoint  
 In modalità SharePoint, Reporting Services è un'applicazione di servizio nell'architettura di SharePoint e viene amministrata direttamente tramite SharePoint  
  
|Strumento|Descrizione|Modalità di accesso|  
|----------|-----------------|-------------------|  
|Amministrazione centrale SharePoint|Usare Amministrazione centrale SharePoint per creare, eseguire una query e gestire le applicazioni di servizio condivise per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].<br /><br /> Per altre informazioni, vedere [Configurazione e amministrazione di un server di report &#40;modalità SharePoint di Reporting Services&#41;](../configure-administer-report-server-reporting-services-sharepoint-mode.md).|Browser per l'URL di Amministrazione centrale del sito di SharePoint|  
|Cmdlet di PowerShell|Utilizzare i cmdlet di PowerShell per creare, eseguire una query e gestire le applicazioni di servizio condivise per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].<br /><br /> Per altre informazioni, vedere [PowerShell cmdlets for Reporting Services SharePoint Mode](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md)(Cmdlet di PowerShell per la modalità SharePoint di Reporting Services).|Shell di gestione SharePoint 2010|  
  
## <a name="tools-for-report-content-management"></a>Strumenti per la gestione del contenuto dei report  
 È disponibile un set di strumenti grafici e di scripting per la gestione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]del contenuto in. Gli strumenti utilizzati dipendono dalla modalità di distribuzione del server di report.  
  
|Strumento|Descrizione|Modalità di accesso|  
|----------|-----------------|-------------------|  
|URL del servizio Web ReportServer|Utilizzare questo strumento per cercare il contenuto nel catalogo del report in una pagina di navigazione degli elementi generica.<br /><br /> Per ulteriori informazioni, vedere [Report Server Web Service](../report-server-web-service/report-server-web-service.md).|Browser|  
|Gestione report|**(Solo in modalità nativa)** Usare questo strumento per amministrare una sola istanza del server di report da un percorso remoto su una connessione HTTP. È possibile eseguire le operazioni seguenti:<br /><br /> Visualizzare, ricercare, stampare e sottoscrivere report.<br /><br /> Creare, proteggere e gestire la gerarchia di cartelle per organizzare gli elementi presenti nel server.<br /><br /> Configurare la sicurezza basata sui ruoli dalla quale dipende l'accesso a elementi e operazioni.<br /><br /> Configurare le proprietà di esecuzione del report, la cronologia del report e i parametri del report.<br /><br /> Creare modelli di report che si connettono e recuperano dati da un'origine dati di Microsoft SQL Server Analysis Services o da un'origine dati relazionale di SQL Server.<br /><br /> Impostare la sicurezza degli elementi di un modello per consentire l'accesso a entità specifiche del modello o per eseguire il mapping delle entità a report click-through predefiniti creati in precedenza.<br /><br /> Creare pianificazioni condivise e origini dei dati condivise per migliorare la gestione delle pianificazioni e delle connessioni alle origini dei dati.<br /><br /> Creare sottoscrizioni guidate dai dati che consentono di implementare i report in un elenco di destinatari di grandi dimensioni.<br /><br /> Creare report collegati per riutilizzare e ridefinire gli scopi di un report esistente in modi diversi.<br /><br /> Avviare Generatore report per creare report da salvare ed eseguire nel server di report.<br /><br /> <br /><br /> Per altre informazioni, vedere [Gestione report &#40;modalità nativa SSRS&#41;](../report-manager-ssrs-native-mode.md).||  
|Utilità rs|Questo strumento è un host di script che è possibile utilizzare per l'esecuzione di operazioni inserite nello script. Questo strumento consente di eseguire script di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] per la copia di dati tra database del server di report, la pubblicazione di report, la creazione di elementi in un database del server di report e altro ancora.<br /><br /> Per altre informazioni, vedere [Utilità della riga di comando del server di report &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md).|Prompt dei comandi|  
  
## <a name="see-also"></a>Vedi anche  
 [Reporting Services server di report](../reporting-services-report-server.md)   
 [Reporting Services concetti &#40;SSRS&#41;](../reporting-services-concepts-ssrs.md)   
 [Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
  
