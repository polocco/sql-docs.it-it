---
description: Riepilogo dei risultati di query (Visual Database Tools)
title: Riepilogare i risultati di query
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- summarizing query results
- queries [SQL Server], results
- aggregate queries [SQL Server]
ms.assetid: c9e15350-ed57-4d95-814d-815fbebfd86b
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 5bd8a8f85fd0d26f206f8c6c3b352eb883d3aa61
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88312277"
---
# <a name="summarize-query-results-visual-database-tools"></a>Riepilogo dei risultati di query (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Quando si creano query di aggregazione, è necessario rispettare alcuni principi logici. Non è, ad esempio, possibile visualizzare il contenuto di singole righe in una query di riepilogo. Progettazione query e Progettazione viste agevola il rispetto di tali principi mediante le particolari modalità di funzionamento del [riquadro Diagramma](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md) e del [riquadro Criteri](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md) .  
  
La conoscenza dei principi alla base delle query di aggregazione e del funzionamento di Progettazione query e Progettazione viste consente di creare query di aggregazione corrette da un punto di vista logico. Il principio fondamentale è che le query di aggregazione possono dare come risultato soltanto informazioni di riepilogo. Di conseguenza, la maggior parte dei principi che seguono descrive le modalità in base a cui è possibile fare riferimento a singole colonne di dati all'interno di una query di aggregazione.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
[Utilizzo di colonne in query di aggregazione &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/work-with-columns-in-aggregate-queries-visual-database-tools.md)  
Vengono descritte le nozioni di base per il raggruppamento e il riepilogo delle colonne con le clausole GROUP BY, WHERE e HAVING.  
  
[Conteggio delle righe di una tabella &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/count-rows-in-a-table-visual-database-tools.md)  
Viene descritta la procedura per contare il numero di righe di una tabella o il numero di righe di una tabella corrispondenti a un set di criteri.  
  
[Riepilogo o aggregazione di valori per tutte le righe di una tabella &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-or-aggregate-values-for-all-rows-in-a-table-visual-database-tools.md)  
Viene descritta la procedura per riepilogare tutte le righe anziché un set di righe raggruppate.  
  
[Riepilogo o aggregazione di valori mediante l'utilizzo di espressioni personalizzate &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-or-aggregate-values-using-custom-expressions-visual-database-tools.md)  
Viene descritta la procedura per utilizzare le espressioni per il riepilogo o l'aggregazione anziché le clausole prestabilite.  
  
## <a name="related-sections"></a>Sezioni correlate  
[Procedure per la progettazione di query e viste &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
Vengono forniti collegamenti ad argomenti in cui viene descritto come utilizzare Progettazione query e Progettazione viste.  
  
