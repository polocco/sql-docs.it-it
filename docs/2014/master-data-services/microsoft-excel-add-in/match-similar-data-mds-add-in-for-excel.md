---
title: Cercare la corrispondenza tra dati simili (componente aggiuntivo MDS per Excel) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f6fd6fc1-3569-42a5-b6cb-87a921c88f3b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 135f1a0d02d88a4b984c7a017a1171220c778bd1
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84961001"
---
# <a name="match-similar-data-mds-add-in-for-excel"></a>Cercare la corrispondenza tra dati simili (componente aggiuntivo MDS per Excel)
  Nel [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]usare la funzionalità Data Quality Services (DQS) per trovare analogie nei dati.  
  
 Per eseguire questa procedura, è possibile:  
  
-   Utilizzare la Knowledge Base predefinita di Data Quality Services o  
  
-   Creare una Knowledge Base DQS e criteri di corrispondenza personalizzati. Per altre informazioni, vedere [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
  
-   È necessario disporre di un foglio di lavoro contenente dati gestiti da MDS. Per altre informazioni, vedere [caricare i dati da MDS in Excel](export-data-to-excel-from-master-data-services.md).  
  
-   Facoltativa. È possibile combinare altri dati con i dati gestiti da MDS prima di verificare le analogie. Per altre informazioni, vedere [Combinare i dati &#40;componente aggiuntivo MDS per Excel&#41;](combine-data-mds-add-in-for-excel.md).  
  
### <a name="to-find-similarities-by-using-the-default-knowledge-base"></a>Per trovare analogie utilizzando la Knowledge Base predefinita  
  
1.  Dal foglio di lavoro contenente i dati gestiti da MDS fare clic su **Abbina dati** nel gruppo **Data Quality**.  
  
2.  Nella finestra di dialogo **Abbina dati** selezionare **Dati DQS (predefinito)** nell'elenco **Knowledge Base DQS**.  
  
3.  Per ogni colonna contenente i dati per cui si desidera verificare la corrispondenza, aggiungere una riga nella finestra di dialogo. Per informazioni sui campi di questa finestra di dialogo, vedere [Modalità di impostazione dei parametri relativi alle regole di corrispondenza](../../data-quality-services/create-a-matching-policy.md#MatchingRules).  
  
4.  Quando il totale di tutti i valori di peso è uguale al 100%, fare clic su **OK**.  
  
### <a name="to-find-similarities-by-using-a-custom-knowledge-base"></a>Per trovare analogie utilizzando una Knowledge Base personalizzata  
  
1.  Dal foglio di lavoro contenente i dati gestiti da MDS fare clic su **Abbina dati** nel gruppo **Data Quality**.  
  
2.  Nell'elenco **Knowledge Base DQS** selezionare il nome della Knowledge Base personalizzata.  
  
3.  Per ogni colonna nel foglio di lavoro, selezionare un dominio DQS.  
  
4.  Dopo aver eseguito il mapping di tutti i domini DQS alle colonne nel foglio di lavoro, fare clic su **OK**.  
  
## <a name="next-steps"></a>Passaggi successivi  
  
-   Visualizzare informazioni aggiuntive per determinare quali dati sono simili. Per altre informazioni, vedere [Colonne corrispondenti Data Quality &#40;componente aggiuntivo MDS per Excel&#41;](data-quality-matching-columns-mds-add-in-for-excel.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Corrispondenza Data Quality nel Componente aggiuntivo MDS per Excel](data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Corrispondenza di dati](../../data-quality-services/data-matching.md)  
  
  
