---
title: File di log e origini di Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting [Reporting Services], log files
- logs [Reporting Services]
- logs [Reporting Services], about log files
- report servers [Reporting Services], log files
- report server log files
- files [Reporting Services], logs
ms.assetid: 80ef0acc-cbef-49d0-87e7-844e3ce19604
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3908c39fc6deba57bf8f0e277918e5b8167f4a77
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "78177187"
---
# <a name="reporting-services-log-files-and-sources"></a>File di log e origini di Reporting Services
  Nel server di report [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] e nell'ambiente server di report viene usata una varietà di destinazioni di log per registrare le informazioni sullo stato e sulle operazioni del server. Sono disponibili due categorie di base di registrazione: registrazione dell'esecuzione e registrazione della traccia. La registrazione dell'esecuzione include le informazioni sulle statistiche, sul controllo, sulla diagnosi delle prestazioni e sull'ottimizzazione dell'esecuzione del report. La registrazione della traccia è costituita da informazioni su messaggi di errore e diagnostica generale.

 **[!INCLUDE[applies](../../includes/applies-md.md)]**  Modalità SharePoint di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] | Modalità nativa di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]

 Nella tabella seguente sono forniti i collegamenti ad altre informazioni su ogni log, compresi il percorso del log e le indicazioni per visualizzarne il contenuto.

|File di log|Descrizione|
|---------|-----------------|
|[Log di esecuzione del server di report e la vista ExecutionLog3](report-server-executionlog-and-the-executionlog3-view.md)|Il log di esecuzione è una vista di SQL Server archiviata nel database del server di report.<br /><br /> Il log di esecuzione del server di report contiene informazioni sui report specifici, inclusi l'ora di esecuzione del report, l'utente che ha eseguito il report, il destinatario a cui il report è stato recapitato e il formato di rendering utilizzato.|
|Log di traccia di SharePoint|Per i server di report in esecuzione in SharePoint, i log di traccia di SharePoint contengono informazioni su [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] . È anche possibile configurare informazioni specifiche su [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] per il servizio di registrazione unificato di SharePoint. Per altre informazioni, vedere [Abilitare gli eventi di Reporting Services per il log di traccia di SharePoint &#40;ULS&#41;](turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md)|
|[Log di traccia del servizio del server di report](report-server-service-trace-log.md)|I log di traccia del servizio Services contengono informazioni molto dettagliate, utili per eseguire il debug di un'applicazione o per raccogliere informazioni su un problema o su un evento.<br /><br /> `C:\Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\LogFiles`|
|[Log HTTP del server di report](report-server-http-log.md)|Il file di log di HTTP contiene un record di tutte le richieste HTTP e le risposte gestite dal servizio Web ReportServer e da Gestione report.|
|[Registro applicazioni di Windows](windows-application-log.md)|Il registro applicazioni di Microsoft Windows contiene informazioni sugli eventi del server di report.|
|Log delle prestazioni di Windows|I log delle prestazioni di Windows contengono dati sulle prestazioni del server di report. L'utente può creare registri di prestazioni e scegliere i contatori in base ai dati che desidera raccogliere. Per altre informazioni, vedere [Monitoraggio delle prestazioni del server di report](monitoring-report-server-performance.md).|
|File di log del programma di installazione|File di log vengono inoltre creati durante l'installazione. Se il programma di installazione non viene completato oppure se viene completato ma vengono visualizzati avvisi o altri messaggi, è possibile esaminare i file di log per risolvere il problema. Per altre informazioni, vedere [Visualizzare e leggere i file di log del programma di installazione di SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).|
|Log IIS|File di log creati da Microsoft Internet Information Services (IIS). Per ulteriori informazioni, vedere [come abilitare la registrazione in Internet Information Services (IIS)](https://support.microsoft.com/kb/313437).|
|Video|Visualizzare un breve video che illustra l'uso di Microsoft Power Query per visualizzare i file di log di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] .<br /><br /> ![visualizzare un video sui log di Power Query e SSRS](../media/generic-video-thumbnail.png "visualizzare un video sui log di Power Query e SSRS")|

## <a name="see-also"></a>Vedere anche
 [Reporting Services &#40;del server di report in modalità nativa&#41;](reporting-services-report-server-native-mode.md) [riferimento a errori ed eventi &#40;Reporting Services](../troubleshooting/errors-and-events-reference-reporting-services.md)&#41;


