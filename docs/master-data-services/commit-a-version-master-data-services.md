---
description: Eseguire il commit di una versione (Master Data Services)
title: Eseguire il commit di una versione
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- committing versions [Master Data Services]
- versions [Master Data Services], committing
ms.assetid: 6b967a39-b333-4b84-9e5f-4fb07e156826
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 27564141f1f0f4c90a08449cbd9cffd7cea9dae0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88430073"
---
# <a name="commit-a-version-master-data-services"></a>Eseguire il commit di una versione (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]eseguire il commit di una versione di un modello per evitare modifiche ai membri del modello e ai relativi attributi. È impossibile sbloccare le versioni di cui è stato eseguito il commit.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario avere l'autorizzazione per accedere all'area funzionale **Gestione versioni** .  
  
-   È necessario essere un amministratore del modello. Per ulteriori informazioni, vedere [amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Lo stato della versione deve essere **Bloccato**. Per altre informazioni, vedere [Bloccare una versione &#40;Master Data Services&#41;](../master-data-services/lock-a-version-master-data-services.md).  
  
-   È necessario che la convalida di tutti i membri abbia avuto esito positivo.  
  
-   È necessario avere l'autorizzazione per accedere all'area funzionale Gestione versioni. Per altre informazioni, vedere [Autorizzazioni per aree funzionali &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
### <a name="to-commit-a-version"></a>Per eseguire il commit di una versione  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Gestione versioni**.  
  
2.  Nella pagina **Gestisci versioni** scegliere **Convalida versione**nella barra dei menu.  
  
3.  Nella pagina **Convalida versione** selezionare il modello e la versione di cui si vuole eseguire il commit.  
  
4.  Fare clic su **Esegui commit**.  
  
5.  Nella finestra di dialogo di conferma fare clic su **OK**.  
  
## <a name="next-steps"></a>Passaggi successivi  
  
-   [Creare un flag di versione &#40;Master Data Services&#41;](../master-data-services/create-a-version-flag-master-data-services.md)  
  
-   [Assegnare un flag a una versione &#40;Master Data Services&#41;](../master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
-   [Copiare una versione &#40;Master Data Services&#41;](../master-data-services/copy-a-version-master-data-services.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Versioni &#40;Master Data Services&#41;](../master-data-services/versions-master-data-services.md)  
  
  
