---
title: Configurare il database e il sito Web per Master Data Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
f1_keywords:
- sql12.mds.configmanager.general.f1
ms.assetid: d50863e7-50d9-4ab8-aabb-fd68e2d132a1
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 478dea9095fe22a437aecf138c22374b5a70885b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66054098"
---
# <a name="set-up-the-database-and-website-for-master-data-services"></a>Configurare il database e il sito Web per Master Data Services
  Usare [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] per configurare il database e il sito Web per [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS)  
  
 Per configurare il database e il sito Web, completare le attività seguenti.  
  
1.  Creare un database utilizzando la pagina **Configurazione database** in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].  
  
     Per informazioni, vedere [pagina Configurazione database &#40;Gestione configurazione Master Data Services&#41;](../../2014/master-data-services/database-configuration-page-master-data-services-configuration-manager.md) e [creazione guidata database &#40;Gestione configurazione Master Data Services&#41;](../../2014/master-data-services/create-database-wizard-master-data-services-configuration-manager.md).  
  
2.  Creare un nuovo sito Web, selezionare il sito Web predefinito o selezionare un altro sito Web esistente usando la pagina **configurazione Web** in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]. Associare quindi il database MDS all'applicazione Web selezionata o creata.  
  
     Per informazioni, vedere la [pagina configurazione Web &#40;Gestione configurazione Master Data Services&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) e la finestra di [dialogo crea sito Web &#40;Gestione configurazione Master Data Services ](../../2014/master-data-services/create-website-dialog-box-master-data-services-configuration-manager.md)&#41;.  
  
3.  Opzionale Abilitare l'integrazione con Data Quality Services tramite la pagina **configurazione Web** in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].  
  
     Per ulteriori informazioni, vedere la [pagina configurazione Web &#40;Gestione configurazione Master Data Services&#41;](../../2014/master-data-services/web-configuration-page-master-data-services-configuration-manager.md) e [abilitare l'integrazione di Data Quality Services con Master Data Services](install-windows/enable-data-quality-services-integration-with-master-data-services.md).  
  
 È anche possibile usare [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] per specificare le impostazioni per servizi e applicazioni Web associate al database MDS. Ad esempio, è possibile specificare la frequenza con cui i dati vengono caricati o quella con cui viene inviata la posta elettronica della convalida. Per altre informazioni, vedere [Impostazioni di sistema &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).  
  
## <a name="see-also"></a>Vedi anche  
 [Database Master Data Services](../../2014/master-data-services/master-data-services-database.md)   
 [Applicazione Web Gestione dati master](../../2014/master-data-services/master-data-manager-web-application.md)  
  
  
