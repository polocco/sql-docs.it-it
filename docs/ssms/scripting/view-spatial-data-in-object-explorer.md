---
title: Visualizzazione di dati spaziali in Esplora oggetti
description: Informazioni su come usare gli strumenti di mapping visivo della finestra Risultati spaziali dell'editor di query per visualizzare i risultati dei dati spaziali (geometrici o geografici).
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.technology: ssms
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 59cca562-e3f5-4257-b868-adcbcc0142cc
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 73ca53f14b81c42bf32f6dbc42ed8229a87a0aa4
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/14/2020
ms.locfileid: "92036074"
---
# <a name="view-spatial-data-in-object-explorer"></a>Visualizzazione di dati spaziali in Esplora oggetti
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
  La finestra **Risultati spaziali** dell'editor di query fornisce strumenti di mapping visivo per la visualizzazione di risultati di dati spaziali in aggiunta alla visualizzazione dei dati in formato griglia nella finestra **Risultati** . Per visualizzare i dati spaziali nella finestra **Risultati spaziali**, i risultati delle query devono contenere almeno una colonna di dati spaziali con dati geometrici o geografici.  
  
### <a name="to-view-spatial-data-in-the-spatial-results-window"></a>Per visualizzare i dati spaziali nella finestra Risultati spaziali  
  
1.  Nell'editor di query fare clic sulla scheda **Risultati spaziali** .  
  
    > [!NOTE]  
    >  Questa finestra non è disponibile se i risultati delle query non contengono dati spaziali o si richiede la restituzione dei risultati come testo.  
  
2.  Selezionare la colonna che si desidera visualizzare nell'elenco **Selezionare la colonna spaziale** . Se la tabella contiene una sola colonna spaziale, questa sarà l'opzione predefinita dell'elenco.  
  
3.  Selezionare la colonna non spaziale che si vuole usare come etichette dei dati nell'elenco **Selezionare la colonna etichetta** .  
  
4.  Selezionare la proiezione desiderata per i dati geografici nell'elenco **Selezionare la proiezione** . La proiezione predefinita è Equirectangular. Le altre proiezioni disponibili sono Mercator, Robinson e Bonne.  
  
    > [!NOTE]  
    >  **Selezionare la proiezione** non è disponibile se la colonna spaziale contiene dati geometrici.  
  
5.  Regolare il dispositivo di scorrimento **Zoom** per aumentare la dimensione visiva degli elementi di cui è stato eseguito il mapping. Per le forme poligonali, l'etichetta è visibile solo se la forma è grande abbastanza da contenere il testo dell'etichetta.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestra Risultati spaziali](./spatial-results-window.md)   
 [Editor di query del motore di database &#40;SQL Server Management Studio&#41;](../f1-help/database-engine-query-editor-sql-server-management-studio.md)   
 [Editor di query e di testo &#40;SQL Server Management Studio&#41;](../f1-help/database-engine-query-editor-sql-server-management-studio.md?view=sql-server-ver15)  
  
