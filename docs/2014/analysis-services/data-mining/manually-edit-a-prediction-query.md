---
title: Modificare manualmente una query di stima | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying prediction queries
- Mining Model Prediction [Analysis Services], modifying prediction queries
- manual prediction query modification [Analysis Services]
ms.assetid: 9f6a9298-49d5-4675-ad49-977a47dff5a6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ce2086e998704e893beaa92aabd2e51129a0450f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66084204"
---
# <a name="manually-edit-a-prediction-query"></a>Modificare manualmente un query di stima
  Dopo avere progettato una query tramite il generatore delle query di stima, è possibile modificarla passando alla visualizzazione Testo query nella scheda **Stima modello di data mining** di Progettazione modelli di data mining. Nella parte inferiore dello schermo viene visualizzato un editor di testo per visualizzare la query creata tramite il generatore delle query.  
  
 Il passaggio alla vista Testo della query è utile per effettuare aggiunte alla query. Ad esempio, è possibile aggiungere una clausola WHERE o ORDER BY.  
  
 Utilizzare la griglia nel generatore delle query di stima per inserire i nomi di oggetti e colonne e impostare la sintassi per le singole funzioni di stima, quindi passare alla modalità di modifica manuale per modificare i valori di parametro.  
  
> [!NOTE]  
>  Se si passa nuovamente alla vista **Progettazione** dalla vista **Testo query** , qualsiasi modifica apportata in **Testo query** andrà persa.  
  
### <a name="modify-a-query"></a>Modificare una query  
  
1.  Nella scheda **Stima modello di data mining** di Progettazione modelli di data mining in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]fare clic su **SQL**.  
  
     La griglia visualizzata nella parte inferiore dello schermo verrà sostituita da un editor di testo che include la query. È possibile digitare le modifiche alla query nell'editor.  
  
2.  Per eseguire la query, scegliere **Risultato** dal menu **Modello di data mining**o fare clic sul pulsante per passare ai risultati della query.  
  
    > [!NOTE]  
    >  Se la query creata non è valida, nella finestra Risultati non verrà segnalato un errore e non verrà visualizzato alcun risultato. Fare clic sul pulsante **Progettazione** oppure scegliere **Progettazione** o **Query** dal menu **Modello di data mining** per correggere il problema ed eseguire nuovamente la query.  
  
## <a name="see-also"></a>Vedi anche  
 [Query di data mining](data-mining-queries.md)   
 [Generatore di query di stima &#40;&#41;di data mining](../prediction-query-builder-data-mining.md)   
 [Lezione 6: Creazione e utilizzo di stime &#40;Esercitazione di base sul data mining&#41;](../../tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
  
