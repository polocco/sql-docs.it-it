---
description: Gruppi di attributi (Master Data Services)
title: Gruppi di attributi
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services]
- attribute groups [Master Data Services], about attribute groups
ms.assetid: 648b3d0b-e15a-45f9-8292-3a54a072e62c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e6ef092efb1133d5067f9f3959765017f695acc5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88413437"
---
# <a name="attribute-groups-master-data-services"></a>Gruppi di attributi (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]i gruppi di attributi consentono di organizzare gli attributi in un'entità. Quando un'entità dispone di molti attributi, i gruppi di attributi migliorano la modalità di visualizzazione di un'entità nell'applicazione Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] .  
  
## <a name="how-attribute-groups-change-the-display"></a>Modalità di modifica della visualizzazione dei gruppi di attributi  
 I gruppi di attributi vengono visualizzati come schede al di sopra della griglia nell'area funzionale **Visualizzatore** di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
 Quando un'entità dispone di un numero elevato di attributi e l'entità + visualizzata in una griglia nel **Visualizzatore**, è necessario scorrere verso destra per visualizzare tutti gli attributi. Per evitare di dover scorrere verso destra, è possibile creare gruppi di attributi.  
  
-   Gli attributi Name e Code sono sempre inclusi automaticamente nei gruppi di attributi.  
  
-   Ciascun attributo di un'entità può appartenere a uno o più gruppi di attributi.  
  
-   Tutti gli attributi sono inclusi automaticamente nella scheda **Tutti gli attributi** nel **Visualizzatore**.  
  
-   Non è possibile nascondere la scheda **Tutti gli attributi** .  
  
 I gruppi di attributi vengono amministrati nell'area funzionale **Amministrazione sistema** di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
## <a name="show-or-hide-attribute-groups"></a>Mostrare o nascondere i gruppi di attributi  
 Quando si crea un gruppo di attributi, questo viene automaticamente nascosto a tutti gli utenti ad eccezione di quello che lo creato. Per altre informazioni su come rendere visibile un gruppo, vedere [Rendere visibile un gruppo di attributi per gli utenti &#40;Master Data Services&#41;](../master-data-services/make-an-attribute-group-visible-to-users-master-data-services.md).  
  
 Per nascondere un attributo specifico all'interno di un gruppo, è possibile assegnare l'autorizzazione **Nega** all'attributo. Per altre informazioni, vedere [Autorizzazioni per elementi foglia &#40;Master Data Services&#41;](../master-data-services/leaf-permissions-master-data-services.md).  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Creare un nuovo gruppo di attributi e aggiungergli attributi.|[Creare un gruppo di attributi &#40;Master Data Services&#41;](../master-data-services/create-an-attribute-group-master-data-services.md)|  
|Rendere visibile un gruppo di attributi agli utenti.|[Rendere visibile un gruppo di attributi per gli utenti &#40;Master Data Services&#41;](../master-data-services/make-an-attribute-group-visible-to-users-master-data-services.md)|  
|Modificare il nome di un gruppo di attributi esistente.|[Modificare il nome di un gruppo di attributi &#40;Master Data Services&#41;](../master-data-services/change-an-attribute-group-name-master-data-services.md)|  
|Eliminare un gruppo di attributi esistente.|[Eliminare un gruppo di attributi &#40;Master Data Services&#41;](../master-data-services/delete-an-attribute-group-master-data-services.md)|  
  
## <a name="related-content"></a>Contenuto correlato  
  
-   [Attributi &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)  
  
  
