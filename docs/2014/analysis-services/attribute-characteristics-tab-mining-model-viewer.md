---
title: Scheda Caratteristiche attributo (Visualizzatore modello di data mining) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.characteristics.f1
ms.assetid: f0c3350d-84c0-4ab8-9fb8-1527c2647299
author: minewiskan
ms.author: owend
ms.openlocfilehash: e62e42dc1cc405f5515e40b0b050036b673a7b89
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2020
ms.locfileid: "84527939"
---
# <a name="attribute-characteristics-tab-mining-model-viewer"></a>Scheda Caratteristiche attributo (Visualizzatore modello di data mining)
  Usare il riquadro **Caratteristiche attributo** per esplorare le relazioni tra i risultati e gli attributi di input in un modello Naive Bayes. È possibile scegliere il valore dell'attributo di destinazione, quindi visualizzare un elenco degli attributi di input che influiscono maggiormente sui risultati.  
  
 **Per altre informazioni:** [Algoritmo Microsoft Naive Bayes](data-mining/microsoft-naive-bayes-algorithm.md)e [Visualizzare un modello utilizzando il Visualizzatore Microsoft Naive Bayes](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
  
## <a name="options"></a>Opzioni  
 **Aggiorna contenuto visualizzatore**  
 Consente di ricaricare il modello di data mining nel visualizzatore.  
  
 **Modello di data mining**  
 Consente di scegliere un modello di data mining da visualizzare tra i modelli presenti nella struttura di data mining corrente. Il modello di data mining verrà aperto automaticamente nel visualizzatore personalizzato migliore per il particolare tipo di modello scelto.  
  
 **Visualizzatore**  
 Consente di scegliere un visualizzatore da utilizzare per l'esplorazione del modello di data mining selezionato. Per ogni modello è possibile scegliere tra un visualizzatore personalizzato o Visualizzatore contenuto di data mining [!INCLUDE[msCoName](../includes/msconame-md.md)] . Se disponibili, nell'elenco vengono visualizzati anche i visualizzatori plug-in.  
  
 **Attributo**  
 Consente di scegliere l'attributo stimabile che si desidera analizzare.  
  
 **Valore**  
 Consente di scegliere uno stato per l'attributo stimabile impostato in **Attributo**. Poiché i modelli Naive Bayes non supportano le variabili continue, tutti gli attributi di destinazione dispongono di risultati discreti o discretizzati. L'attributo Missing viene sempre aggiunto automaticamente all'elenco.  
  
 **Caratteristiche per\<predictable state>**  
 Nel grafico sono contenute le colonne seguenti in cui viene descritta la modalità di correlazione tra gli stati dell'attributo di input e lo stato dell'attributo stimabile selezionato.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|**Variabile**|Vengono elencati gli attributi di input nel modello di data mining.|  
|**Valori**|Viene elencato ogni stato dell'attributo di input in **Variabile**.|  
|**Probabilità**|La barra rappresenta la probabilità che l'attributo e il valore in tale riga siano associati allo stato selezionato dell'attributo stimabile. Posizionare il mouse sulla barra per visualizzare la probabilità in percentuale.|  
  
## <a name="see-also"></a>Vedere anche  
 [Algoritmi di data mining &#40;Analysis Services-&#41;di data mining](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visualizzatori modello di data mining &#40;Progettazione modelli di data mining&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visualizzatori modello di data mining](data-mining/data-mining-model-viewers.md)  
  
  
