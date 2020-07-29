---
title: Ordinare con ORDER BY
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- ORDER BY clause [Visual Database Tools]
ms.assetid: 459f5640-8058-4c24-97e7-7bbd6168bc39
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 840ceec41624cf11604d4db2b2eb90f9b4c03c53
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "85999309"
---
# <a name="sort-with-order-by-visual-database-tools"></a>Ordinamento tramite la clausola ORDER BY (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Utilizzando la clausola ORDER BY è possibile ordinare i risultati delle query in base a una o più colonne delle righe restituite. Per definire una clausola ORDER BY, scegliere le opzioni desiderate nel riquadro Criteri.  
  
### <a name="to-sort-a-query-using-an-order-by-clause"></a>Per ordinare una query utilizzando una clausola ORDER BY  
  
1.  Aprire una query esistente o crearne una nuova.  
  
2.  Nel [riquadro Criteri](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)fare clic sulla colonna **Tipo di ordinamento** della riga corrispondente alla colonna da usare per ordinare i risultati della query.  
  
3.  Scegliere *Crescente* o *Decrescente* dall'elenco a discesa.  
  
> [!NOTE]  
> Se si deseleziona la voce **Tipo di ordinamento** per una colonna, la colonna verrà rimossa dalla clausola ORDER BY.  
  
Quando si utilizza il riquadro Criteri, la clausola UNION della query cambia in base alle azioni più recenti.  
  
> [!NOTE]  
> Per ordinare i risultati in base a più colonne, usare la colonna **Ordinamento** per specificare l'ordine in cui deve essere effettuata la ricerca nelle diverse colonne. Per altre informazioni, vedere **Procedura: Ordinare più colonne nelle query**.  
  
## <a name="see-also"></a>Vedere anche  
[Ordinare e raggruppare i risultati delle query &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[Creare un riepilogo dei risultati di query &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Procedure per la progettazione di query e viste &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
