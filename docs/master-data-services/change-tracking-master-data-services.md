---
title: Rilevamento modifiche
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- change tracking [SQL Server]
ms.assetid: 5e879c65-0d38-454f-9a20-62a6e72c89f7
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6519ea515b6552805aa5b97e38579082ddcfe15c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "73729660"
---
# <a name="change-tracking-master-data-services"></a>Rilevamento modifiche (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]è possibile utilizzare gruppi rilevamento delle modifiche per eseguire un'azione quando cambia un valore di attributo. Usare il rilevamento modifiche quando non si conosce il nuovo valore, ma si desidera sapere se sono state apportate modifiche.  
  
## <a name="configuring-change-tracking"></a>Configurazione del rilevamento modifiche  
 Per configurare il rilevamento modifiche, aggiungere un attributo a un gruppo rilevamento modifiche. Il gruppo può contenere uno o molti attributi. Creare quindi una regola business per definire l'azione da eseguire quando uno degli attributi del gruppo vengono modificati.  
  
> [!NOTE]  
>  Le regole business del rilevamento modifiche considerano i dati in gestione temporanea (importati) come modificati.  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Aggiungere attributi a un gruppo rilevamento modifiche.|[Aggiungere attributi ad un gruppo rilevamento modifiche &#40;Master Data Services&#41;](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|Creare una regola business per avviare azioni in base alle modifiche apportate agli attributi.|[Inizializzare azioni basate su modifiche dei valori di attributo &#40;Master Data Services&#41;](../master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
  
## <a name="related-content"></a>Contenuto correlato  
  
-   [Convalida &#40;Master Data Services&#41;](../master-data-services/validation-master-data-services.md)  
  
-   [Regole di business &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
-   [Attributi &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)  
  
  
