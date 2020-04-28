---
title: Connettere i componenti con i percorsi | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data flow [Integration Services], connections
- components [Integration Services], connections
- connections [Integration Services], data flow components
ms.assetid: 05633e4c-1370-4b05-802b-f36b07dd71c8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e6cc08adc2682b65b1e2de9a2c3fd1d483a33c92
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "78176486"
---
# <a name="connect-components-with-paths"></a>Connessione di componenti con i percorsi
  Per costruire il flusso di dati in un pacchetto, è possibile usare l'area di progettazione della scheda **Flusso di dati** di Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] . Se un flusso di dati contiene due componenti, sarà possibile connetterli connettendo l'output di un'origine o trasformazione all'input di una trasformazione o destinazione. Il connettore tra due componenti del flusso di dati è detto percorso.

 Nella figura seguente viene illustrato un semplice flusso di dati con un componente di origine, due trasformazioni, un componente di destinazione e i percorsi che li connettono.

 ![Flusso di dati](media/mw-dts-08.gif "Flusso di dati")

 Dopo aver connesso i due componenti è possibile visualizzare i metadati dei dati che si spostano lungo il percorso e le proprietà del percorso nella finestra **Editor percorso flusso di dati**. Per altre informazioni, vedere [Percorsi in Integration Services](data-flow/integration-services-paths.md).

 A un percorso è possibile aggiungere anche un visualizzatore dati, che consente di visualizzare i dati che si spostano tra i componenti del flusso di dati durante l'esecuzione del pacchetto.

### <a name="to-connect-components-in-a-data-flow"></a>Per connettere componenti in un flusso di dati

-   [Connessione di componenti in un flusso di dati](data-flow/connect-components-in-a-data-flow.md)

### <a name="to-set-path-properties"></a>Per impostare le proprietà di un percorso

-   [Impostazione delle proprietà di un percorso tramite l'Editor percorso flusso di dati](../../2014/integration-services/set-the-properties-of-a-path-by-using-the-data-flow-path-editor.md)

### <a name="to-view-path-metadata"></a>Per visualizzare i metadati di un percorso

-   [Visualizzazione dei metadati dei percorsi nell'Editor percorso flusso di dati](../../2014/integration-services/view-path-metadata-in-the-data-flow-path-editor.md)

### <a name="to-view-path-metadata"></a>Per visualizzare i metadati di un percorso

-   [Aggiungere un visualizzatore dati a un flusso di dati](../../2014/integration-services/add-a-data-viewer-to-a-data-flow.md)

## <a name="see-also"></a>Vedere anche
 [Flusso](data-flow/data-flow.md) di dati dell' [attività flusso](control-flow/data-flow-task.md) di dati [trasformare i dati con le trasformazioni](data-flow/transformations/transform-data-with-transformations.md) [gestione degli errori nei dati](data-flow/error-handling-in-data.md)


