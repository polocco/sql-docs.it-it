---
title: Prerequisiti per le esercitazioni (Generatore report) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9b8346a6-f4f4-4ad3-bc98-8f2be342ef2d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 17c8b67d29cb82956a37bc3f83867161486a4f9e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "73637861"
---
# <a name="prerequisites-for-tutorials-report-builder"></a>Prerequisiti per le esercitazioni (Generatore report)
  Nelle esercitazioni di Generatore report si presuppone che l'utente sia in grado di visualizzare e salvare report in un server di report o in un sito di SharePoint integrato in un server di report. Per quanto riguarda i dati, in tutte le esercitazioni vengono utilizzate query letterali che devono essere elaborate da un'istanza di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
 Se non si dispone dell'accesso a un server di report, a un sito o a un'origine dati, sarà possibile apprendere l'utilizzo di Generatore report attraverso la compilazione di un report offline. Vedere [Esercitazione: Creare un report grafico rapido offline &#40;Generatore report&#41;](report-builder/tutorial-create-a-quick-chart-report-offline-report-builder.md).  
  
## <a name="requirements"></a>Requisiti  
 Per completare le esercitazioni di Generatore report, è necessario soddisfare i requisiti seguenti:  
  
-   Accesso a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Generatore report. È possibile eseguire Generatore report utilizzando la versione autonoma di Generatore report o la versione ClickOnce, disponibile da Gestione report o da un sito di SharePoint. Per le versioni ClickOnce, l'unica differenza riguarda il primo passaggio, ovvero l'apertura di Generatore report.  
  
     Per utilizzare Gestione report, aprire Gestione report e fare clic su **Generatore report**. Per impostazione predefinita, l'URL per Gestione report è\<http://*ServerName*>/Reports.  
  
     Per utilizzare un sito di SharePoint, accedere al sito, fare clic sulla scheda Documenti, fare clic su Nuovo documento, quindi su Report di Generatore report nell'elenco a discesa. Ad esempio, http://\<ServerName>/sites/mySite/reports. L'amministratore di SharePoint deve abilitare la caratteristica Report di Generatore report per ogni raccolta documenti.  
  
-   URL di un server di report di [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] o di un sito di SharePoint integrato con un server di report di [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] . È necessario disporre dell'autorizzazione per il salvataggio e la visualizzazione di report, origini dati condivise, set di dati condivisi, parti di report e modelli. Per impostazione predefinita, l'URL per un server di report\<è http://nomeserver>/ReportServer. Per impostazione predefinita, l'URL di un sito di SharePoint\<è http://sitename\<> o http://Server>/site.  
  
-   Nome di un'istanza di [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] e credenziali sufficienti per l'accesso in sola lettura a qualsiasi database. Per le query del set di dati delle esercitazioni vengono utilizzati dati letterali, ma per restituire i metadati necessari per un set di dati del report ogni query deve essere elaborata da un'istanza di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] . Ad esempio, nella stringa di connessione seguente viene specificato solo un server: `data source=<servername>`. È necessario disporre dell'accesso in lettura al database predefinito assegnato all'utente dall'amministratore di sistema che concede l'autorizzazione per l'accesso al server. È inoltre possibile specificare un database, come illustrato nella stringa di connessione seguente: `data source=<servername>;initial catalog=<database>`.  
  
-   Per l'esercitazione in cui è inclusa una mappa, è necessario configurare il server di report affinché supporti le mappe Bing come sfondo. Per ulteriori informazioni, vedere [pianificare il supporto dei report mappa](plan-for-map-report-support.md) nella [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] documentazione [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] di nella documentazione [online](https://go.microsoft.com/fwlink/?LinkId=154888) di in MSDN.Microsoft.com.  
  
-   L'esercitazione, [esercitazione: creazione di report drill-through e report principali &#40;Generatore report&#41;](tutorial-creating-drillthrough-and-main-reports-report-builder.md), usa il set di dati di Contoso Business Intelligence Demo. Questo set di dati è costituito dal data warehouse ContosoDW e dal database dell'elaborazione analitica online (OLAP) di Contoso_Retail. I report che si creeranno in questa esercitazione recuperano i dati di report dal cubo vendite Contoso. Il database OLAP di Contoso_Retail può essere scaricato dall' [Area download Microsoft](https://www.microsoft.com/download/details.aspx?id=18279). Sarà sufficiente scaricare solo il file ContosoBIdemoABF.exe. Il file contiene il database OLAP.  
  
     L'altro file, ContosoBIdemoBAK.exe, è relativo al data warehouse ContosoDW, che non viene utilizzato in questa esercitazione.  
  
     Il sito Web include istruzioni relative all'estrazione e al ripristino del file di backup ContosoRetail.abf nel database OLAP di Contoso_Retail.  
  
     È necessario avere accesso a un'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sulla quale installare il database OLAP.  
  
 L'amministratore del server di report deve concedere le autorizzazioni necessarie per il server di report, configurare i percorsi delle cartelle [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] e configurare le opzioni predefinite di Generatore report. Per ulteriori informazioni, vedere [installazione, disinstallazione e supporto Generatore report](install-uninstall-and-report-builder-support.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Esercitazioni &#40;Generatore report&#41;](report-builder-tutorials.md)  
  
  
