---
title: Creare e gestire partizioni nel database dell'area di lavoro (SSAS tabulare) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.partitionmgr.f1
ms.assetid: 0b3027d6-652b-4eb3-a197-58b25df65218
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 37f1b8c1f97601ab9997fdb6706587f42e1b4e6f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/25/2020
ms.locfileid: "66067455"
---
# <a name="create-and-manage-partitions-in-the-workspace-database-ssas-tabular"></a>Creare e gestire partizioni nel database dell'area di lavoro (SSAS tabulare)
  Le partizioni consentono di dividere una tabella in parti logiche. Ogni partizione può quindi essere elaborata (aggiornata) indipendentemente o in parallelo ad altre. Le partizioni possono consentire di migliorare la scalabilità e la facilità di gestione di database grandi. Per impostazione predefinita, ogni tabella dispone di una partizione in cui sono incluse tutte le colonne. Nelle attività di questo argomento viene descritto come creare e gestire partizioni nel database dell'area di lavoro modello tramite la finestra di dialogo **Gestione partizioni** in[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]  
  
 Dopo aver distribuito un modello in un'altra istanza di Analysis Services, gli amministratori di database possono creare e gestire partizioni nel modello (distribuito) utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Per altre informazioni, vedere [Creare e gestire partizioni di modelli tabulari &#40;SSAS tabulare&#41;](partitions-ssas-tabular.md).  
  
 In questo argomento sono incluse le attività seguenti:  
  
-   [Per creare una nuova partizione](#bkmk_create_new)  
  
-   [Per copiare una partizione](#bkmk_copy)  
  
-   [Per eliminare una partizione](#bkmk_delete)  
  
> [!NOTE]  
>  Non è possibile unire partizioni nel database dell'area di lavoro modello tramite la finestra di dialogo Gestione partizioni. Le partizioni possono essere unite in un modello distribuito solo utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="tasks"></a>Attività  
 Per creare e gestire partizioni, usare la finestra di dialogo **Gestione partizioni** . Per visualizzare la finestra di dialogo **Gestione partizioni** , in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]fare clic sul menu **Tabella** e quindi scegliere **Partizioni**.  
  
###  <a name="to-create-a-new-partition"></a><a name="bkmk_create_new"></a>Per creare una nuova partizione  
  
1.  In Progettazione modelli selezionare la tabella per cui si desidera definire una partizione.  
  
2.  Fare clic sul menu **Tabella** , quindi scegliere **Partizioni**.  
  
3.  Nella casella di riepilogo **Tabella**di **Gestione partizioni** verificare o selezionare la tabella che si vuole partizionare e quindi fare clic su **Nuova**.  
  
4.  In **Nome partizione**digitare un nome per la partizione. Per impostazione predefinita, il nome della partizione predefinita sarà numerato in modo incrementale per ogni nuova partizione.  
  
5.  È possibile selezionare le righe e le colonne da includere nella partizione utilizzando la modalità Anteprima tabella o una query SQL creata tramite la modalità Editor query.  
  
     Per usare la modalità Anteprima tabella (impostazione predefinita), fare clic sul pulsante **Anteprima tabella** in prossimità dell'angolo superiore destro della finestra di anteprima. Scegliere le colonne che si desidera includere nella partizione selezionando la casella di controllo accanto al nome della colonna. Per filtrare le righe, fare clic con il pulsante destro del mouse su un valore della cella e scegliere **Filtro in base al valore della cella selezionata**.  
  
     Per usare un'istruzione SQL, fare clic sul pulsante **Editor query** in prossimità dell'angolo superiore destro della finestra di anteprima e quindi digitare o incollare un'istruzione della query SQL nella finestra Query. Per convalidare l'istruzione, fare clic su **Convalida**. Per usare Progettazione query, fare clic su **Progettazione**.  
  
###  <a name="to-copy-a-partition"></a><a name="bkmk_copy"></a>Per copiare una partizione  
  
1.  Nella casella di riepilogo **Tabella**di **Gestione partizioni** verificare o selezionare la tabella contenente la partizione che si vuole copiare.  
  
2.  Dall'elenco **Partizioni** selezionare la partizione che si vuole copiare e quindi fare clic su **Copia**.  
  
3.  In **Nome partizione**digitare un nuovo nome per la partizione.  
  
###  <a name="to-delete-a-partition"></a><a name="bkmk_delete"></a> Per eliminare una partizione  
  
1.  Nella casella di riepilogo **Tabella**di **Gestione partizioni** verificare o selezionare la tabella contenente la partizione che si vuole eliminare.  
  
2.  Nell'elenco **Partizioni** selezionare la partizione che si vuole eliminare e quindi fare clic su **Elimina**.  
  
## <a name="see-also"></a>Vedi anche  
 [Partizioni &#40;SSAS tabulare&#41;](partitions-ssas-tabular.md)   
 [Elaborare partizioni nel database dell'area di lavoro &#40;SSAS tabulare&#41;](process-partitions-in-the-workspace-database-ssas-tabular.md)  
  
  
