---
title: Finestra di dialogo filtro (grafico accuratezza modello di data mining) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 71e884a9-7ec4-4459-a4c4-87f6c796d478
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6102fe9c623e785c0ca207660697bffebce82bb5
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544485"
---
# <a name="filter-dialog-box-mining-accuracy-chart"></a>Finestra di dialogo Filtro (Grafico accuratezza modello di data mining)
  La finestra di dialogo **Filtro** consente di compilare condizioni che è possibile applicare a un set di dati. Il set di dati può essere rappresentato da un set di dati esterno utilizzato per eseguire il test oppure da dati del case utilizzati per eseguire il training di un modello di data mining. Questa finestra di dialogo consente di compilare criteri che è possibile salvare come parte di criteri di filtro più complessi nella finestra di dialogo **Filtro dei set di dati** o in **Filtro modello** .  
  
-   La finestra di dialogo **Filtro dei set di dati** è disponibile dalla scheda **Selezione input** della finestra di progettazione **Grafico accuratezza modello di data mining** .  
  
-   La finestra di dialogo **Filtro modello** è disponibile dalla scheda **Modelli di data mining** della finestra di progettazione Data Mining.  
  
 Se si applica un filtro a un modello di data mining, usare prima la finestra di dialogo **Filtro modello** per scegliere una tabella. È quindi possibile usare la finestra di dialogo **Filtro** per compilare le condizioni che si applicano solo a questa tabella.  
  
 Se si crea un filtro da applicare a un set di dati di test esterno, usare prima la finestra di dialogo **Filtro dei set di dati** per scegliere una tabella dall'elenco di tabelle in una vista origine dati. È quindi possibile usare la finestra di dialogo **Filtro** per compilare le condizioni che si applicano solo a questa tabella.  
  
 Dopo avere creato un set di condizioni da applicare a una singola tabella, [!INCLUDE[clickOK](../includes/clickok-md.md)]. Le modifiche apportate alla finestra di dialogo **Filtro** vengono aggiunte automaticamente all'espressione di filtro nella finestra di dialogo padre, **Filtro dei set di dati** o **Filtro modello**.  
  
 Se si applica il filtro al nuovo set di dati, il modello di data mining esistente viene utilizzato per valutare solo i case del set di dati che soddisfano le condizioni. Tuttavia, se si applica il filtro al modello di data mining, l'accuratezza del modello viene valutata solo per i case all'interno del modello di data mining che soddisfano i criteri.  
  
 **Per altre informazioni:** [Test e convalida &#40;Data mining&#41;](data-mining/testing-and-validation-data-mining.md)  
  
## <a name="options"></a>Opzioni  
 **Condizioni**  
 Griglia contenente le colonne in cui si specificano le condizioni nelle colonne dalla tabella selezionata nella finestra di dialogo **Filtro dei set di dati** .  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|**E/o**|Fare clic per specificare se applicare l'operatore AND o l'operatore OR alla condizione nella riga. Questi valori sono disponibili solo dopo aver selezionato una colonna dall'elenco **Colonna struttura di data mining** .|  
|**Colonne struttura di data mining**|Fare clic per selezionare una colonna dall'elenco delle colonne contenute nella tabella selezionata dall'origine dati nella finestra di dialogo **Filtro dei set di dati** .|  
|**Operatore**|Selezionare un operatore dall'elenco. Gli operatori disponibili dipendono dal tipo di dati della colonna.<br /><br /> Se la colonna contiene valori discreti, sono disponibili solo gli operatori seguenti:<br /><br /> = (uguale a), <> (diverso da), IS NOT NULL, IS NULL.<br /><br /> Se la colonna contiene valori continui, sono supportati anche gli operatori per le operazioni maggiore di e minore di.|  
|**Valore**|Digitare un valore da utilizzare come condizione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Attività e procedure di test e convalida &#40;di data mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)   
 [Progettazione Grafico accuratezza modello di data mining &#40;&#41;di data mining](mining-accuracy-chart-designer-data-mining.md)  
  
  
