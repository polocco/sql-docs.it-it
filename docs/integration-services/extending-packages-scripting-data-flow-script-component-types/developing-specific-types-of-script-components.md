---
description: Sviluppo di tipi specifici di componenti script
title: Sviluppo di tipi specifici di componenti script | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], examples
ms.assetid: dfbbe959-6b4e-4b47-b9dd-bcc31929482d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fc1942c156469def05a8cf9aaa12ac3e09a8167c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88430443"
---
# <a name="developing-specific-types-of-script-components"></a>Sviluppo di tipi specifici di componenti script

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Il componente script è uno strumento configurabile che è possibile utilizzare nel flusso di dati di un pacchetto per rispondere ai requisiti non soddisfatti dalle origini, dalle trasformazioni e dalle destinazioni incluse in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Questa sezione contiene esempi di codice del componente script che dimostrano le quattro opzioni disponibili per la configurazione di questo componente.  
  
-   Come origine.  
  
-   Come trasformazione con output sincroni.  
  
-   Come trasformazione con output asincroni.  
  
-   Come destinazione.  
  
 Per altri esempi del componente script, vedere [Ulteriori esempi di componente script](../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Creazione di un'origine con il componente script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md)  
 Viene descritto e illustrato come creare un'origine del flusso di dati tramite il componente script.  
  
 [Creazione di una trasformazione sincrona con il componente script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)  
 Viene descritto e illustrato come creare una trasformazione del flusso di dati con output sincroni tramite il componente script. Questo tipo di trasformazione modifica righe di dati sul posto non appena attraversano il componente.  
  
 [Creazione di una trasformazione asincrona con il componente script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)  
 Viene descritto e illustrato come creare una trasformazione del flusso di dati con output asincroni tramite il componente script. Questo tipo di trasformazione deve leggere tutte le righe di dati prima di poter aggiungere ulteriori informazioni, ad esempio aggregazioni calcolate, ai dati che attraversano il componente.  
  
 [Creazione di una destinazione con il componente script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
 Viene descritto e illustrato come creare una destinazione del flusso di dati tramite il componente script.  
  
## <a name="see-also"></a>Vedere anche  
 [Confronto tra soluzioni di scripting e oggetti personalizzati](../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)   
 [Sviluppo di tipi specifici di componenti del flusso di dati](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)  
  
  
