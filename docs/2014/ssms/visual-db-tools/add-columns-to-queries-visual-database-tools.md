---
title: Aggiungere colonne a query (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting columns
- columns [SQL Server], adding
- queries [SQL Server], columns
- adding columns
ms.assetid: 82f3ba72-3d72-4fb1-8179-2a953a782787
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: aef64ed8031664dcbefa7d0e30bf9f63435b292c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "63015702"
---
# <a name="add-columns-to-queries-visual-database-tools"></a>Aggiunta di colonne a query (Visual Database Tools)
  Per utilizzare una colonna in una query, è necessario aggiungerla alla query. È possibile aggiungere una colonna per visualizzarla nell'output della query, per utilizzarla per l'ordinamento oppure per ricercarne o riepilogarne il contenuto. È possibile decidere quali colonne utilizzate nella query devono essere incluse nel riquadro Risultati quando viene eseguita la query. Per altre informazioni, vedere [Rimuovere colonne dai risultati della query &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
> [!NOTE]  
>  Per visualizzare il tipo di dati di una colonna in Progettazione query e Progettazione viste, selezionare la tabella o l'oggetto con valori di tabella nel **riquadro Diagramma** e nella finestra delle proprietà fare clic su Elenco colonne. Fare clic sui **puntini di sospensione (...)** per aprire la finestra di dialogo **Elenco colonne**.  
  
 Ovunque si utilizzi una colonna in una query, è anche possibile utilizzare un'espressione costituita da una qualunque combinazione di colonne, valori letterali, operatori e funzioni.  
  
### <a name="to-add-an-individual-column"></a>Per aggiungere una singola colonna  
  
-   Nel **riquadro Diagramma**selezionare la casella di controllo accanto alla colonna da includere.  
  
     -oppure-  
  
-   Nel **riquadro Criteri**spostarsi sulla prima riga vuota della griglia, fare clic sul campo nella colonna **Colonna** e selezionare un nome di colonna dall'elenco a discesa.  
  
### <a name="to-add-all-columns-for-one-table-or-table-valued-object"></a>Per aggiungere tutte le colonne di una tabella o di un oggetto con valori di tabella  
  
-   Nel **riquadro diagramma**selezionare la casella di controllo accanto a ** \*(tutte le colonne)**.  
  
### <a name="to-add-all-columns-for-all-tables-and-table-structured-objects"></a>Per aggiungere tutte le colonne per tutte le tabelle e gli oggetti con struttura di tabella  
  
1.  Assicurarsi che non sia selezionata alcuna linea di join nel **Riquadro operazioni tabella** .  
  
2.  Fare clic con il pulsante destro del mouse nello spazio vuoto della finestra Progettazione e scegliere **Proprietà** dal menu di scelta rapida.  
  
3.  Nella finestra Proprietà fare clic su **Tutte le colonne** e scegliere **Sì** o **No** dall'elenco a discesa.  
  
## <a name="see-also"></a>Vedere anche  
 [Rimuovere colonne dai risultati della query &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Rimuovere colonne da query &#40;Visual Database Tools&#41;](remove-columns-from-queries-visual-database-tools.md)   
 [Specificare i criteri di ricerca &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)   
 [Riepilogare i risultati delle query &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)   
 [Eseguire operazioni di base con le query &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
