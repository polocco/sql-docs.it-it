---
title: Creare query con parametri senza nome
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- unnamed parameters
- parameters [SQL Server], unnamed
ms.assetid: 5f4b664b-3d3d-4d07-a0e7-791d78743504
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 263788197ce8beda6c25287155544b40d0edb824
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86000054"
---
# <a name="create-queries-with-unnamed-parameters-visual-database-tools"></a>Creazione di query con parametri senza nome (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Per creare una query con un parametro senza nome, è possibile inserire un punto interrogativo (?) come segnaposto per un valore letterale. In Progettazione query e Progettazione viste gli verrà assegnato automaticamente un nome temporaneo. Nella query è possibile specificare qualsiasi numero di parametri senza nome.  
  
Al momento dell'esecuzione della query in Progettazione query e Progettazione viste, nella finestra di dialogo Parametri query viene visualizzato il nome temporaneo.  
  
### <a name="to-specify-an-unnamed-parameter"></a>Per specificare un parametro senza nome  
  
1.  Aggiungere al [riquadro Criteri](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)le colonne o le espressioni da includere nella ricerca. Per evitare che le colonne o le espressioni compaiano nell'output della query, rimuoverle dalle colonne di output.  
  
2.  Individuare la riga che contiene la colonna di dati o l'espressione da includere nella ricerca e aggiungere un punto interrogativo (?) nella colonna **Filtro** della griglia.  
  
    Per impostazione predefinita viene aggiunto l'operatore "=". In ogni caso, è possibile modificare la cella inserendo ">", "<" o qualsiasi altro operatore di confronto SQL.  
  
## <a name="see-also"></a>Vedere anche  
[Esecuzione di query con parametri &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-parameters-visual-database-tools.md)  
  
