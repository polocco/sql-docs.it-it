---
title: Trasformazione Query di data mining | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingquerytrans.f1
helpviewer_keywords:
- Data Mining Query transformation
- prediction queries [Integration Services]
ms.assetid: 7960133b-a3e1-48af-ba43-55ed78c38e71
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 278fdc3b1abd38b63f01e967e28d11983a09e682
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "85430778"
---
# <a name="data-mining-query-transformation"></a>Query di data mining - trasformazione
  La trasformazione Query di data mining esegue query di stima basate su modelli di data mining. Questa trasformazione contiene un generatore di query per la creazione di query DMX (Data Mining Extensions). Il generatore di query consente di creare istruzioni personalizzate per la valutazione dei dati di input della trasformazione in base a un modello di data mining esistente, utilizzando il linguaggio DMX. Per altre informazioni, vedere [Guida di riferimento a DMX &#40;Data Mining Extensions&#41;](/sql/dmx/data-mining-extensions-dmx-reference).  
  
 Una singola trasformazione può eseguire più query di stima, se i modelli sono compilati in base alla stessa struttura di data mining. Per ulteriori informazioni, vedere [interfacce di query di data mining](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools).  
  
## <a name="configuration-of-the-data-mining-query-transformation"></a>Configurazione della trasformazione Query di data mining  
 La trasformazione Query di data mining usa una gestione connessione [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] per connettersi al progetto di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] o all'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] che contiene la struttura e i modelli di data mining. Per altre informazioni, vedere [Gestione connessione Analysis Services](../../connection-manager/analysis-services-connection-manager.md).  
  
 Questa trasformazione include un input e un output. Non supporta un output degli errori.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor trasformazione Query di data mining** o a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Editor trasformazione Query di data mining &#40;scheda Modello di data mining&#41;](../../data-mining-query-transformation-editor-mining-model-tab.md)  
  
-   [Editor trasformazione Query di data mining &#40;scheda Modello di data mining&#41;](../../data-mining-query-transformation-editor-mining-model-tab.md)  
  
 Nella finestra di dialogo **Editor avanzato** sono disponibili le proprietà che è possibile impostare a livello di codice. Per ulteriori informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor avanzato** o a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Proprietà comuni](../../common-properties.md)  
  
-   [proprietà personalizzate della trasformazione](transformation-custom-properties.md)  
  
 Per altre informazioni su come impostare le proprietà, vedere [Impostazione delle proprietà di un componente del flusso di dati](../set-the-properties-of-a-data-flow-component.md).  
  
  
