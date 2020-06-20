---
title: Comprimere i gruppi di righe (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- group collapsing [SQL Server]
- collapsing rows
- row collapsing [SQL Server]
ms.assetid: 7338dad0-965d-44ba-8c1a-b993acb7156d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0534d416d6d821e2d1870e98a42e8281648c6af1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85066193"
---
# <a name="collapse-groups-of-rows-visual-database-tools"></a>Compressione di gruppi di righe (Visual Database Tools)
  È possibile creare un risultato di query in cui ogni riga di risultati corrisponda a un intero gruppo di righe dei dati originali. Quando si comprimono le righe, è necessario tenere presenti alcune considerazioni:  
  
-   **È possibile eliminare le righe duplicate** Alcune query possono creare set di risultati in cui sono presenti più righe identiche. È possibile, ad esempio, creare un set di risultati in cui ogni riga contiene la città in cui risiede un autore e il nome dello stato in cui tale città si trova. Se però in una città risiedono più autori, saranno presenti numerose righe identiche. Il codice SQL risultante potrebbe essere simile al seguente:  
  
    ```  
    SELECT city, state  
    FROM authors  
    ```  
  
     Il set di risultati generato dalla query precedente non è molto utile. Se in una città risiedono quattro autori, il set di risultati includerà quattro righe identiche. Poiché il set di risultati non contiene altre colonne oltre a quelle della città e dello stato, non è possibile distinguere le righe identiche l'una dall'altra. Un modo per evitare le righe duplicate consiste nell'includere ulteriori colonne che possano rendere diverse le righe. Se ad esempio si include il nome dell'autore, ogni riga sarà diversa, a condizione che in una qualsiasi città non vivano due autori con lo stesso nome. Il codice SQL risultante potrebbe essere simile al seguente:  
  
    ```  
    SELECT city, state, fname, minit, lname  
    FROM authors  
  
    ```  
  
     La query precedente elimina il sintomo, ma non risolve realmente il problema. In altre parole, il set di risultati non contiene duplicati, ma non riguarda più in modo specifico le città. Per eliminare i duplicati nel set di risultati originale e fare in modo che ogni riga descriva una città, è possibile creare una query che restituisca soltanto righe distinte. Il codice SQL risultante potrebbe essere simile al seguente:  
  
    ```  
    SELECT DISTINCT city, state  
    FROM authors  
  
    ```  
  
     Per altre informazioni sull'eliminazione dei duplicati, vedere [Escludere righe duplicate &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
-   **È possibile eseguire calcoli su gruppi di righe** È possibile riepilogare le informazioni presenti in gruppi di righe. È possibile, ad esempio, creare un set di risultati in cui ogni riga contiene la città in cui risiede un autore e il nome dello stato a cui tale città appartiene più un conteggio del numero di autori residenti nella città. Il codice SQL risultante potrebbe essere simile al seguente:  
  
    ```  
    SELECT city, state, COUNT(*)  
    FROM authors  
    GROUP BY city, state  
  
    ```  
  
     Per informazioni dettagliate sull'esecuzione di calcoli su gruppi di righe, vedere [Creare un riepilogo dei risultati di query &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md) e [Ordinare e raggruppare i risultati delle query &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md).  
  
-   **È possibile usare criteri di selezione per includere gruppi di righe** È possibile, ad esempio, creare un set di risultati in cui ogni riga include la città di residenza di più autori e il nome dello stato a cui tale città appartiene, oltre a un conteggio del numero di autori residenti in tale città. Il codice SQL risultante potrebbe essere simile al seguente:  
  
    ```  
    SELECT city, state, COUNT(*)  
    FROM authors  
    GROUP BY city, state  
    HAVING COUNT(*) > 1  
  
    ```  
  
     Per informazioni dettagliate sull'applicazione di criteri di selezione su gruppi di righe, vedere [Definizione di condizioni per i gruppi &#40;Visual Database Tools&#41;](specify-conditions-for-groups-visual-database-tools.md) e [Utilizzo delle clausole HAVING e WHERE nella stessa query &#40;Visual Database Tools&#41;](use-having-and-where-clauses-in-the-same-query-visual-database-tools.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Specificare i criteri di ricerca &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)   
 [Procedure per la progettazione di query e viste &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
