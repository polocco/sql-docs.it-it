---
title: Eliminare un membro o una raccolta (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], deleting
- leaf members [Master Data Services], deleting
- deleting members [Master Data Services]
- members [Master Data Services], deleting
- consolidated members [Master Data Services], deleting
ms.assetid: 519130a7-4226-4d71-9124-d2ee0ce7e5bd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c37f57da9651cad37a3ac4bb267efb3da05d7616
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971608"
---
# <a name="delete-a-member-or-collection-master-data-services"></a>Eliminare un membro o una raccolta (Master Data Services)
  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]eliminare un membro o una raccolta quando non è più necessaria. Se si desidera eliminare i membri in bulk, utilizzare invece il processo di gestione temporanea. Per ulteriori informazioni, vedere [disattivare o eliminare membri utilizzando il processo di gestione temporanea &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md).  
  
> [!NOTE]  
>  Non è possibile eliminare un membro se viene utilizzato come valore dell'attributo basato su dominio per un altro membro.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre dell'autorizzazione per accedere all'area funzionale **Esplora** .  
  
-   Per i membri, è necessario disporre almeno dell'autorizzazione **aggiornamento** per l'oggetto modello foglia da cui si desidera eliminare un membro.  
  
-   Per le raccolte, è necessario disporre almeno dell'autorizzazione **Aggiornamento** per l'oggetto raccolta foglia in fase di eliminazione.  
  
### <a name="to-delete-a-member-or-collection"></a>Per eliminare un membro o una raccolta  
  
1.  Nella home page di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] selezionare un modello nell'elenco **Modello** .  
  
2.  Selezionare una versione dall'elenco **Versione** .  
  
3.  Fare clic su **Esplora**.  
  
4.  Per eliminare:  
  
    -   Un membro foglia, scegliere **Entità** dalla barra dei menu, quindi fare clic sul nome dell'entità che contiene il membro.  
  
    -   Un membro consolidato, scegliere **Gerarchie** dalla barra dei menu, quindi fare clic sul nome della gerarchia che contiene il membro. Quindi fare clic sul nodo nella gerarchia che contiene il membro.  
  
    -   Una raccolta, scegliere **Raccolte** dalla barra dei menu, quindi fare clic sul nome dell'entità che contiene la raccolta.  
  
5.  Nella griglia fare clic sulla riga del membro o della raccolta che si desidera eliminare.  
  
6.  Fare clic su **Elimina membro**, **Elimina**o **Elimina raccolta**.  
  
7.  Nella finestra di dialogo di conferma fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Riattivare un membro o una raccolta &#40;Master Data Services&#41;](../../2014/master-data-services/reactivate-a-member-or-collection-master-data-services.md)   
 [Membri &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md)   
 [Raccolte &#40;Master Data Services&#41;](../../2014/master-data-services/collections-master-data-services.md)  
  
  
