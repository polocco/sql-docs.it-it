---
title: Aggiornamento di report mediante le classi generate dallo schema RDL (esercitazione su SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RDL [Reporting Services], generating
- RDL [Reporting Services], tutorials
- RDL [Reporting Services], serializing
ms.assetid: 8f81d48f-7ab9-4ef8-bce0-7d16d9a47fbd
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 313a5268b754089d4ca8964328d53cb23ec6edd1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62746115"
---
# <a name="updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial"></a>Aggiornamento dei report mediante le classi generate dallo schema RDL (esercitazione SSRS)
  In questa esercitazione viene illustrato come utilizzare lo strumento XML Schema Definition (XSD. exe) per generare classi che consentono di serializzare e deserializzare i file di definizione dei report (con estensione rdl e rdlc [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.Xml.Serialization.XmlSerializer> ) con la classe.  
  
## <a name="what-you-will-learn"></a>Lezioni dell'esercitazione  
 Durante questa esercitazione verranno eseguite le attività seguenti:  
  
-   Creare un'applicazione usando il [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modello di progetto applicazione console.  
  
-   Generare classi dallo schema Report Definition Language (RDL) utilizzando lo strumento **xsd** .  
  
-   Connessione a un server di report e recupero di una definizione del report.  
  
-   Scrittura di codice per l'aggiornamento del file di definizione del report.  
  
-   Salvataggio della definizione aggiornata del report nel server di report.  
  
-   Eseguire l'applicazione dello schema RDL (VB/C#).  
  
> [!NOTE]  
>  Gli esempi di codice forniti in questa esercitazione potrebbero non funzionare per i report in cui non è disponibile alcuna descrizione. L'errore si verifica perché la proprietà di descrizione non è disponibile per i report privi di descrizione specificata.  
  
## <a name="requirements"></a>Requisiti  
 Per eseguire l'esercitazione, occorre:  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].  
  
-   Autorizzazioni sufficienti per l'accesso al servizio Web ReportServer e la pubblicazione di report sul servizio nel computer in cui è installato il server di report.  
  
-   Il database di esempio [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] installato in un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Un report installato nel server di report. In questa esercitazione viene utilizzato il report di esempio Company Sales 2012. Per ulteriori informazioni sui report di esempio, vedere [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
> [!NOTE]  
>  Gli esempi non vengono installati automaticamente durante l'installazione, ma possono essere installati in qualsiasi momento. Per informazioni sugli esempi, vedere [SQL Server Product Samples](https://go.microsoft.com/fwlink/?LinkId=182887).  
  
 **Tempo stimato per il completamento dell'esercitazione:** 30 minuti  
  
## <a name="tasks"></a>Attività  
 [Lezione 1: Creare il progetto di Visual Studio per lo schema RDL](../../2014/tutorials/lesson-1-create-the-rdl-schema-visual-studio-project.md)  
  
 [Lezione 2: Generare classi dallo schema RDL con lo strumento xsd](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md)  
  
 [Lezione 3: Caricare la definizione di un report dal server di report](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md)  
  
 [Lezione 4: Aggiornare la definizione del report a livello di programmazione](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md)  
  
 [Lezione 5: Pubblicare la definizione del report nel server di report](../../2014/tutorials/lesson-5-publish-the-report-definition-to-the-report-server.md)  
  
 [Lezione 6: eseguire l'applicazione dello schema RDL &#40;VB-C&#35;&#41;](../../2014/tutorials/lesson-6-run-the-rdl-schema-application-vb-csharp.md)  
  
## <a name="see-also"></a>Vedi anche  
 [Report Definition Language &#40;SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
