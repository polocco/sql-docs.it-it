---
title: Confronto tra soluzioni di scripting e oggetti personalizzati | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- managed tasks [Integration Services]
- Script task [Integration Services], vs. custom managed tasks
- SSIS Script task, vs. custom managed tasks
- custom tasks [Integration Services], scripts
ms.assetid: c0aea822-a21e-44e1-a3d3-8777bd0a1c34
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5c57c208eb0e8c359d25b85766a738d72e591696
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2020
ms.locfileid: "86917851"
---
# <a name="comparing-scripting-solutions-and-custom-objects"></a>Confronto tra soluzioni di scripting e oggetti personalizzati

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Un'attività Script o un componente script di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] può implementare molte delle funzionalità disponibili in un componente flusso di dati o un'attività gestita personalizzata. Di seguito sono riportate alcune considerazioni che consentono di scegliere il tipo di attività appropriato per specifiche esigenze:  
  
-   Se la configurazione o la funzionalità è specifica di un singolo pacchetto, è consigliabile utilizzare l'attività Script o il componente di script anziché sviluppare un oggetto personalizzato.  
  
-   Se la funzionalità è generica e può essere utilizzata in futuro per altri pacchetti e da altri sviluppatori, è consigliabile creare un oggetto personalizzato anziché utilizzare una soluzione di scripting. È possibile utilizzare un oggetto personalizzato in qualsiasi pacchetto, mentre uno script può essere utilizzato solo nel pacchetto per cui è stato creato.  
  
-   Se il codice sarà riutilizzato all'interno dello stesso pacchetto, è consigliabile creare un oggetto personalizzato. La copia di codice tra attività Script o componenti script diversi riduce le possibilità di manutenzione in quanto rende più difficile mantenere e aggiornare più copie del codice.  
  
-   Se l'implementazione cambia nel corso del tempo, è consigliabile utilizzare un oggetto personalizzato. Gli oggetti personalizzati possono essere sviluppati e distribuiti separatamente rispetto al pacchetto padre, mentre un aggiornamento apportato a una soluzione di scripting richiede la ridistribuzione dell'intero pacchetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di pacchetti tramite oggetti personalizzati](../../integration-services/extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
  
  
