---
title: Esplorazione della flessibilità di un'area dati Tablix (Generatore report) | Microsoft Docs
description: Scoprire la flessibilità dei report impaginati in Generatore report quando si aggiunge una tabella, una matrice o un'area dati elenco.
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: fef19359-a618-4d21-a7e4-e391cdefd4eb
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 1f87c4ddc6b678675d5bcad06d06a3c466ecd929
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "84999552"
---
# <a name="exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs"></a>Esplorazione della flessibilità di un'area dati Tablix (Generatore report e SSRS)
In un report impaginato di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , quando si aggiunge una tabella, una matrice o un'area dati elenco dalla scheda Inserisci sulla barra multifunzione, si può partire con un modello iniziale per un'area dati Tablix. La scelta iniziale del modello, tuttavia, non è vincolante. Per continuare a sviluppare la modalità di visualizzazione dei dati è possibile aggiungere o rimuovere caratteristiche dell'area dati Tablix quali gruppi, righe e colonne.  
  
 Quando si elimina un gruppo di righe o colonne, è possibile scegliere di eliminare le righe e le colonne utilizzate per visualizzare i valori del gruppo. È inoltre possibile aggiungere o rimuovere righe e colonne manualmente. Per informazioni sull'uso di righe e colonne per la visualizzazione di dati dettaglio e dei gruppi, vedere [Area dati Tablix &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md).  
  
 Dopo avere modificato la struttura dell'area dati Tablix, è possibile impostare le proprietà per controllare la modalità di rendering dell'area dati nel report. È ad esempio è possibile ripetere intestazioni di colonna all'inizio di ogni pagina o mantenere un'intestazione di gruppo con il gruppo. Per altre informazioni, vedere [Controllo della visualizzazione dell'area dati Tablix in una pagina del report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/controlling-the-tablix-data-region-display-on-a-report-page.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="changing-a-table-to-a-matrix"></a>Sostituzione di una tabella con una matrice  
 Per impostazione predefinita, una tabella contiene righe di dettaglio che visualizzano i valori del set di dati del report. In genere, una tabella include gruppi di righe in cui i dati dettaglio sono organizzati per gruppo, quindi include i valori aggregati basati su ogni gruppo. Per sostituire la tabella con una matrice, aggiungere gruppi di colonne. In genere, il gruppo dettagli viene rimosso quando l'area dati contiene sia gruppi di righe sia di colonne in modo che sia possibile visualizzare solo i valori riepilogativi dei gruppi. Per altre informazioni, vedere [Aggiunta o eliminazione di un gruppo in un'area dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md).  
  
 Per definizione, la creazione di una matrice implica l'aggiunta di una cella d'angolo della Tablix. È possibile unire le celle di quest'area e aggiungere un'etichetta. Per altre informazioni, vedere [Unire le celle in un'area dati &#40;Generatore report e SSRS& #41;](../../reporting-services/report-design/merge-cells-in-a-data-region-report-builder-and-ssrs.md).  
  
## <a name="changing-a-matrix-to-a-table"></a>Sostituzione di una matrice con una tabella  
 Per impostazione predefinita, una matrice contiene gruppi di righe e di colonne, ma non gruppi dettagli. Per sostituire una matrice con una tabella, rimuovere i gruppi di colonne e aggiungere un gruppo dettagli da visualizzare nella riga di dettaglio. Per altre informazioni, vedere [Aggiunta o eliminazione di un gruppo in un'area dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) e [Aggiungere un gruppo dettagli &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-a-details-group-report-builder-and-ssrs.md).  
  
## <a name="changing-a-default-list-to-a-grouped-list"></a>Sostituzione di un elenco predefinito con un elenco con gruppi  
 Per impostazione predefinita, un elenco contiene righe di dettagli, ma non gruppi. Per modificare l'elenco in modo da utilizzare una riga di gruppo, rinominare il gruppo dettagli e specificare un'espressione di raggruppamento. Per altre informazioni, vedere [Aggiunta o eliminazione di un gruppo in un'area dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)  
  
## <a name="creating-stepped-displays"></a>Creazione di visualizzazioni con rientri  
 Per impostazione predefinita, quando si aggiungono gruppi a un'area dati Tablix, le celle presenti nell'area dell'intestazione del gruppo di righe visualizzano valori in colonne. In presenza di gruppi nidificati, ogni gruppo viene visualizzato in una colonna separata. Per creare una visualizzazione con rientri, rimuovere tutte le colonne di gruppo, ad eccezione di una, e formattare la colonna restante per visualizzare la gerarchia di gruppi come visualizzazione di testo rientrata. Per altre informazioni, vedere [Creazione di un report con rientri &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/create-a-stepped-report-report-builder-and-ssrs.md).  
  
## <a name="adding-an-adjacent-details-group"></a>Aggiunta di un gruppo dettagli adiacente  
 Per impostazione predefinita, il gruppo dettagli è il gruppo figlio più interno in una gerarchia di gruppi. Non è possibile nidificare un gruppo al di sotto del gruppo dettagli. È ad esempio possibile creare ulteriori gruppi dettagli adiacenti per visualizzare i primi cinque prodotti e gli ultimi cinque 5 prodotti per vendita. Grazie alla possibilità di aggiungere espressioni di filtro e ordinamento su ogni gruppo, possono essere mostrate due viste di dati dettaglio dello stesso set di dati in un'unica area dati Tablix. Per altre informazioni, vedere [Informazioni sui gruppi &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/understanding-groups-report-builder-and-ssrs.md), [Aggiunta o eliminazione di un gruppo in un'area dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) e [Aggiungere un filtro a un set di dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Area dati Tablix &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)   
 [Tabelle, matrici ed elenchi &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Tabelle &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)   
 [Matrici &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md)   
 [Elenchi &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
  
  
