---
title: Funzionalità deprecate in SQL Server Reporting Services SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- deprecated features [Reporting Services]
- HTML OWC rendering extension [Reporting Services]
- Report Server Web service, endpoints
ms.assetid: 3876c01e-f81d-4cce-9104-5106a8c369e6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d5cbef64cbed910018e7d2f8dae1844074aaa3f5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66109347"
---
# <a name="deprecated-features-in-sql-server-reporting-services-in-sql-server-2014"></a>Funzionalità deprecate di SQL Server Reporting Services in SQL Server 2014
  In questo argomento si descrivono le funzionalità di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] deprecate. Le funzionalità sono ancora disponibili nella versione in cui sono deprecate, tuttavia sono pianificate per essere rimosse in una versione successiva di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. È consigliabile non usare le funzionalità deprecate nelle nuove applicazioni.  
  
 In questo argomento  
  
-   [Funzionalità deprecate in SQL Server 2014 Reporting Services](#bkmk_2014)  
  
-   [Funzionalità deprecate di SQL Server 2012 SP1 Reporting Services](#bkmk_2012sp1)  
  
-   [Funzionalità deprecate in SQL Server 2012 Reporting Services](#bkmk_2012)  
  
-   [Funzionalità deprecate di SQL Server 2008 R2 Reporting Services](#bkmk_kj)  
  
##  <a name="sql-server-2014-reporting-services-deprecated-features"></a><a name="bkmk_2014"></a>SQL Server 2014 Reporting Services funzionalità deprecate  
  
### <a name="features-not-supported-in-the-next-version-of-sql-server"></a>Funzionalità non supportate nella prossima versione di SQL Server  
 Le funzionalità riportate di seguito di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] non saranno supportate nella **prossima** versione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Non usare queste funzionalità in un nuovo progetto di sviluppo e modificare non appena possibile le applicazioni in cui sono attualmente implementate.  
  
#### <a name="html-rendering-extension-device-information-settings"></a>Impostazioni relative alle informazioni sul dispositivo per l'estensione per il rendering HTML  
 Le seguenti impostazioni relative alle informazioni sul dispositivo per l'estensione per il rendering HTML sono deprecate.  
  
-   ActionScript  
  
-   ActiveXControls  
  
-   GetImage  
  
-   OnlyVisibleStyles  
  
-   ReplacementRoot  
  
-   ResourceStreamRoot  
  
-   StreamRoot  
  
-   UsePx  
  
-   Zoom  
  
 Per ulteriori informazioni sull'estensione per il rendering HTML, vedere [HTML Device Information Settings](html-device-information-settings.md)  
  
#### <a name="microsoft-word-and-microsoft-excel-1997-2003-rendering"></a>Rendering di Microsoft Word e Microsoft Excel 1997-2003  
 Con le estensioni per il rendering BIFF8 di[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] esegue i report nel formato BIFF (Binary Interchange File Format) di [!INCLUDE[msCoName](../includes/msconame-md.md)] Word e [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003. [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]include le [!INCLUDE[msCoName](../includes/msconame-md.md)] estensioni che eseguono il rendering nel formato Office 2007-2010 Open XML.  
  
#### <a name="report-definition-language-rdl-2005-and-earlier"></a>Linguaggio RDL (Report Definition Language) 2005 e versioni precedenti  
 Il linguaggio RDL (Report Definition Language) 2005 e le versioni precedenti sono deprecati. Per ulteriori informazioni su RDL, vedere [Report Definition Language &#40;SSRS&#41;](reports/report-definition-language-ssrs.md).  
  
 Per ulteriori informazioni sull'aggiornamento dei report, vedere [Upgrade Reports](install-windows/upgrade-reports.md).  
  
#### <a name="sql-server-2005-and-earlier-custom-report-items"></a>Elementi di report personalizzati di SQL Server 2005 e versioni precedenti  
 Gli elementi del report personalizzati compilati [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] per 2005 e versioni precedenti sono deprecati.  
  
#### <a name="reporting-services-snapshots-2005-and-earlier"></a>Snapshot di Reporting Services 2005 e versioni precedenti  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]gli snapshot di cui [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] è stato eseguito il rendering con 2005 e versioni precedenti sono deprecati.  
  
#### <a name="report-models"></a>Modelli di report  
 I modelli di report del linguaggio SMDL (Semantic Modeling Language) sono deprecati. Sebbene sia possibile continuare a utilizzare i modelli di report esistenti come origini dati [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] nei report, è consigliabile aggiornare i report per rimuovere la dipendenza dai modelli di report.  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] non include strumenti per la creazione o l'aggiornamento di modelli di report. Per ulteriori informazioni, vedere [modifiche di rilievo nelle SQL Server Reporting Services SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).  
  
#### <a name="deprecated-methods-in-the-web-service-endpoint"></a>Metodi deprecati nell'endpoint servizio Web  
 Le operazioni seguenti sono deprecate nell'endpoint servizio Web di <xref:ReportService2010.ReportingService2010>:  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
#### <a name="sharepoint-web-parts"></a>Web part di SharePoint  
 Il file CAB di installazione **RSWebParts.cab** e le web part di SharePoint che possono essere estratte dal file CAB, sono deprecati. Le web part deprecate sono Esplora report (**SPExplorer.dwp**) e Visualizzatore report (**SPViewer.dwp**).  
  
 Per ulteriori informazioni sulle web part deprecate, vedere [Visualizzare ed esplorare i report in modalità nativa utilizzando le web part di SharePoint (SSRS)](https://msdn.microsoft.com/library/ms159772.aspx)  
  
### <a name="features-not-supported-in-a-future-version-of-sql-server"></a>Funzionalità non supportate in una futura versione di SQL Server  
 Le funzionalità seguenti del [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] sono supportate nella versione successiva di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], ma in seguito verranno rimosse. La versione specifica di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] non è stata determinata.  
  
 In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] non sono state deprecate funzionalità di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
##  <a name="sql-server-2012-sp1-reporting-services-deprecated-features"></a><a name="bkmk_2012sp1"></a>SQL Server 2012 SP1 Reporting Services funzionalità deprecate  
 In questa sezione si descrivono le funzionalità di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] deprecate in [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)]. Le funzionalità seguenti del [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] sono supportate nella versione successiva di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], ma in seguito verranno rimosse. La versione specifica di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] non è stata determinata.  
  
### <a name="sharepoint-web-parts"></a>Web part di SharePoint  
 Il file CAB di installazione **RSWebParts.cab** e le web part di SharePoint che possono essere estratte dal file CAB, sono deprecati. Le web part deprecate sono Esplora report (**SPExplorer.dwp**) e Visualizzatore report (**SPViewer.dwp**).  
  
 Per ulteriori informazioni sulle web part deprecate, vedere [Visualizzare ed esplorare i report in modalità nativa utilizzando le web part di SharePoint (SSRS)](https://msdn.microsoft.com/library/ms159772.aspx)  
  
##  <a name="sql-server-2012-reporting-services-deprecated-features"></a><a name="bkmk_2012"></a>SQL Server 2012 Reporting Services funzionalità deprecate  
 In questa sezione si descrivono le funzionalità di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] deprecate in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].  
  
### <a name="html-rendering-extension-device-information-settings"></a>Impostazioni relative alle informazioni sul dispositivo per l'estensione per il rendering HTML  
 Le seguenti impostazioni relative alle informazioni sul dispositivo per l'estensione per il rendering HTML sono deprecate.  
  
-   ActionScript  
  
-   ActiveXControls  
  
-   GetImage  
  
-   OnlyVisibleStyles  
  
-   ReplacementRoot  
  
-   ResourceStreamRoot  
  
-   StreamRoot  
  
-   UsePx  
  
-   Zoom  
  
 Per ulteriori informazioni sull'estensione per il rendering HTML, vedere [HTML Device Information Settings](html-device-information-settings.md)  
  
### <a name="microsoft-word-and-microsoft-excel-1997-2003-rendering"></a>Rendering di Microsoft Word e Microsoft Excel 1997-2003  
 Con le estensioni per il rendering BIFF8 di[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] esegue i report nel formato BIFF (Binary Interchange File Format) di [!INCLUDE[msCoName](../includes/msconame-md.md)] Word e [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel 1997-2003. [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]include le [!INCLUDE[msCoName](../includes/msconame-md.md)] estensioni che eseguono il rendering nel formato Office 2007-2010 Open XML.  
  
### <a name="report-definition-language-rdl-2005-and-earlier"></a>Linguaggio RDL (Report Definition Language) 2005 e versioni precedenti  
 Il linguaggio RDL (Report Definition Language) 2005 e le versioni precedenti sono deprecati. Per ulteriori informazioni su RDL, vedere [Report Definition Language &#40;SSRS&#41;](reports/report-definition-language-ssrs.md).  
  
 Per ulteriori informazioni sull'aggiornamento dei report, vedere [Upgrade Reports](install-windows/upgrade-reports.md).  
  
### <a name="sql-server-2005-and-earlier-custom-report-items"></a>Elementi di report personalizzati di SQL Server 2005 e versioni precedenti  
 Gli elementi del report personalizzati compilati [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] per 2005 e versioni precedenti sono deprecati.  
  
### <a name="reporting-services-snapshots-2005-and-earlier"></a>Snapshot di Reporting Services 2005 e versioni precedenti  
 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]gli snapshot di cui [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] è stato eseguito il rendering con 2005 e versioni precedenti sono deprecati.  
  
### <a name="report-models"></a>Modelli di report  
 I modelli di report del linguaggio SMDL (Semantic Modeling Language) sono deprecati. Sebbene sia possibile continuare a utilizzare i modelli di report esistenti come origini dati [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] nei report, è consigliabile aggiornare i report per rimuovere la dipendenza dai modelli di report.  
  
 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] non include strumenti per la creazione o l'aggiornamento di modelli di report. Per ulteriori informazioni, vedere [modifiche di rilievo nelle SQL Server Reporting Services SQL Server 2014](breaking-changes-in-sql-server-reporting-services-in-sql-server-2016.md).  
  
### <a name="deprecated-methods-in-the-web-service-endpoint"></a>Metodi deprecati nell'endpoint servizio Web  
 Le operazioni seguenti sono deprecate nell'endpoint servizio Web di <xref:ReportService2010.ReportingService2010>:  
  
-   <xref:ReportService2010.ReportingService2010.GetProperties%2A>  
  
-   <xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>  
  
##  <a name="sql-server-2008-r2-reporting-services-deprecated-features"></a><a name="bkmk_kj"></a>SQL Server 2008 R2 Reporting Services funzionalità deprecate  
  
> [!NOTE]  
>  Poiché SQL Server 2008 R2 è un aggiornamento secondario della versione di SQL Server 2008, è consigliabile rivedere anche il contenuto nella sezione relativa a SQL Server 2008.  
  
### <a name="report-server-web-service-endpoints"></a>Endpoint del servizio Web ReportServer  
 I servizi Web <xref:ReportService2005.ReportingService2005> e <xref:ReportService2006.ReportingService2006> sono deprecati in questa versione. Questi endpoint sono stati sostituiti da un nuovo endpoint: <xref:ReportService2010.ReportingService2010>.  
  
 Nel nuovo endpoint sono incluse tutte le funzionalità disponibili negli endpoint deprecati e le nuove funzionalità introdotte in SQL Server 2008 R2.  
  
## <a name="see-also"></a>Vedi anche  
 [Novità &#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [Compatibilità con le versioni precedenti](../getting-started/backward-compatibility.md)   
 [Modifiche del comportamento a SQL Server Reporting Services in SQL Server 2014](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
 [Funzionalità non più disponibili di SQL Server Reporting Services in SQL Server 2014](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  
  
  
