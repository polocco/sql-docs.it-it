---
title: Eliminare una gerarchia esplicita (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- explicit hierarchies, deleting
- deleting explicit hierarchies [Master Data Services]
ms.assetid: 4ce177b0-9884-47a2-9cea-212e845dd762
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: db4a6a51164fbcdfd62a542cba9e48a58438d0ed
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84950721"
---
# <a name="delete-an-explicit-hierarchy-master-data-services"></a>Eliminare una gerarchia esplicita (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]eliminare una gerarchia esplicita quando non è più necessaria.  
  
> [!WARNING]  
>  Quando si elimina una gerarchia esplicita, vengono eliminati anche tutti i membri consolidati in essa contenuti. Se si eliminano tutte le gerarchie esplicite per un'entità, vengono eliminate anche tutte le raccolte dell'entità e quest'ultima non è più abilitata per le raccolte e le gerarchie esplicite.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Amministrazione sistema** .  
  
-   È necessario essere un amministratore del modello. Per ulteriori informazioni, vedere [amministratori &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-delete-an-explicit-hierarchy"></a>Per eliminare una gerarchia esplicita  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Amministrazione sistema**.  
  
2.  Nella pagina **Vista modelli** scegliere **Gestisci** dalla barra dei menu, quindi fare clic su **Entità**.  
  
3.  Nella pagina **Gestione entità** selezionare un modello dall'elenco **Modello** .  
  
4.  Selezionare la riga relativa all'entità contenente la gerarchia esplicita da eliminare.  
  
5.  Fare clic su **Modifica entità selezionata**.  
  
6.  Nel riquadro **gerarchie esplicite** della pagina **Modifica entità** fare clic sulla gerarchia esplicita che si desidera eliminare.  
  
7.  Fare clic su **Elimina gerarchia selezionata**.  
  
8.  Nella finestra di dialogo di conferma fare clic su **OK**.  
  
9. Nell'ulteriore finestra di dialogo di conferma fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare una gerarchia esplicita &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)   
 [Gerarchie esplicite &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
