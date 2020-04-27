---
title: Pubblicare un report in una raccolta di SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- deploying [Reporting Services], reports in SharePoint integrated mode
- SharePoint integration [Reporting Services], publishing to a library
- publishing reports [Reporting Services], to a SharePoint library
ms.assetid: 3f6dfc28-50d8-4231-bd25-871b5f77cce6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1cc957af5596acbf2478d55645b1386283970e33
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66102532"
---
# <a name="publish-a-report-to-a-sharepoint-library"></a>Pubblicare un report in una raccolta di SharePoint
  Per pubblicare un report in un sito di SharePoint configurato per l'integrazione con SharePoint, è necessario impostare le proprietà del progetto in Progettazione report. Nelle proprietà del progetto tutti i riferimenti a server, report e origini dati condivise devono essere URL completi. Nella definizione di un report tutti i riferimenti a sottoreport, report drill-through e risorse quali immagini basate su Web devono essere rappresentati da URL completi.  
  
 Per impostare le proprietà del progetto, è necessario disporre dell'autorizzazione **Membro** o **Proprietario** per il sito di SharePoint. Per altre informazioni, vedere [Esempi di URL per elementi di report pubblicati in un server di report in modalità SharePoint &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md).  
  
### <a name="to-publish-a-report-to-a-sharepoint-site"></a>Per pubblicare un report in un sito di SharePoint  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire un progetto del server di report esistente o nuovo.  
  
2.  Scegliere **Proprietà** dal menu **Progetto**. Verrà visualizzata la finestra di dialogo **pagine delle proprietà** di _ \<Project>_.  
  
3.  Nell'elenco **Configurazione** selezionare il nome di una configurazione della build della soluzione da usare per compilare e pubblicare il report. La configurazione corrente è elencata come **attiva**(*\<Configuration>*).  
  
4.  Se si desidera pubblicare le origini dati condivise nel progetto e sovrascrivere origini dati condivise pubblicate in precedenza, impostare **OverwriteDataSources** su **True**.  
  
5.  Opzionale Per **TargetDataSourceFolder**, digitare l'URL di una raccolta di SharePoint o di una cartella della raccolta *http://TestServer/TestSite/Documents/DataSources)*, ad esempio.  
  
     Se non si specifica alcun valore, verrà utilizzato il valore **TargetReportFolder** .  
  
6.  Per **TargetReportFolder**, digitare l'URL di una raccolta o di una cartella della raccolta, *http://TestServer/TestSite/Documents/Reports)* ad esempio.  
  
7.  Per **TargetServerURL**, digitare l'URL di un sito principale o secondario di SharePoint. Se non si specifica un sito, viene utilizzato il sito principale predefinito, ad esempio *http://servername* *http://servername/site*,, o. *http://servername/site/subsite*  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. In Esplora soluzioni fare clic con il pulsante destro del mouse sul report da pubblicare, quindi scegliere **Distribuisci**. Il report verrà pubblicato nel percorso specificato in **TargetReportFolder**. Gli eventuali errori di distribuzioni verranno visualizzati nella finestra di output.  
  
## <a name="see-also"></a>Vedi anche  
 [Finestra di dialogo Pagine delle proprietà del progetto](../tools/project-property-pages-dialog-box.md)   
 [Impostare le proprietà di distribuzione &#40;Reporting Services&#41;](../tools/set-deployment-properties-reporting-services.md)   
 [Pubblicazione di report in un server di report](publishing-reports-to-a-report-server.md)   
 [Esempi di URL per elementi di report pubblicati in un server di report in modalità SharePoint &#40;SSRS&#41;](../tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)   
 [Usare una connessione Office Data Connection &#40;.odc&#41; ai report &#40;Reporting Services in modalità integrata SharePoint&#41;](../report-data/use-an-office-data-connection-odc-with-reports.md)  
  
  
