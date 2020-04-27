---
title: Visualizzare gli errori che si verificano durante il processo di gestione temporanea (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- staging process [Master Data Services], viewing errors
ms.assetid: 6d2bff84-624b-47fc-a4a5-d9ea01d13412
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 75b7fb5a1b98f599a07e47101f93268779ca39b9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "65478573"
---
# <a name="view-errors-that-occur-during-the-staging-process-master-data-services"></a>Visualizzare errori che si verificano durante il processo di gestione temporanea (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], è possibile visualizzare errori che si verificano durante il processo di gestione temporanea. Nel database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , sono disponibili due viste che mostrano errori:  
  
-   stg.viw_name_MemberErrorDetails per foglia o aggiornamenti dei membri consolidati.  
  
-   stg.viw_name_RelationshipErrorDetails per aggiornamenti delle relazioni di gerarchia.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   Nel database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , è necessario disporre delle autorizzazioni SELECT per la vista stg.viw_name_MemberErrorDetails o stg.viw_name_RelationshipErrorDetails.  
  
-   È necessario essere un amministratore del modello. Per ulteriori informazioni, vedere [amministratori &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-view-staging-errors"></a>Per visualizzare gli errori di gestione temporanea  
  
1.  Aprire [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] e connettersi all'istanza [!INCLUDE[ssDE](../includes/ssde-md.md)] per il database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  Aprire una nuova query.  
  
3.  Digitare il testo seguente, sostituendo il nome con quello della tabella di staging, ad esempio, viw_Product_MemberErrorDetails.  
  
     `SELECT * FROM stg.viw_name_MemberErrorDetails`  
  
4.  Eseguire la query. I dettagli dell'errore vengono visualizzati nel campo **ErrorDescription** .  
  
## <a name="next-steps"></a>Passaggi successivi  
 Per informazioni dettagliate sui messaggi di errore, vedere [Errori del processo di gestione temporanea &#40;Master Data Services&#41;](../../2014/master-data-services/staging-process-errors-master-data-services.md).  
  
## <a name="see-also"></a>Vedi anche  
 [Importazione dati &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)   
 [Risoluzione dei problemi relativi al processo di gestione temporanea (Master Data Services)](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-the-staging-process-master-data-services.aspx)  
  
  
