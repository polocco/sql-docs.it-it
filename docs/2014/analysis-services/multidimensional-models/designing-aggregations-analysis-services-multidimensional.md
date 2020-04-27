---
title: Progettazione di aggregazioni (Analysis Services-multidimensionale) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- aggregations [Analysis Services], partitions
- partitions [Analysis Services], aggregations
ms.assetid: 3072b7e0-6961-42ad-a287-16f391f2cec4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 307d2ff0419cf5def9f422f08daf349b80bcad2e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66075213"
---
# <a name="designing-aggregations-analysis-services---multidimensional"></a>Progettazione di aggregazioni (Analysis Services - Multidimensionale)
  Le aggregazioni sono riepiloghi precalcolati dei dati del cubo che consentono a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] di fornire rapidamente le risposte alle query.  
  
 Per impostare le opzioni di archiviazione e progettare le aggregazioni per una partizione, è possibile utilizzare Progettazione guidata aggregazioni. Questa procedura guidata viene eseguita su una singola partizione alla volta di un gruppo di misure in modo da consentire la selezione di opzioni e progettazioni diverse per ogni partizione. La procedura guidata consente di eseguire in modo semplificato i passaggi necessari per configurare l'archiviazione e progettare l'aggregazione per una partizione. Per ulteriori informazioni sulla configurazione dell'archiviazione, vedere.  
  
 Selezionare un metodo per il controllo del numero di aggregazioni che verranno progettate dalla procedura guidata e quindi eseguire automaticamente il processo di progettazione delle aggregazioni.  
  
 L'obiettivo è la progettazione di un numero ottimale di aggregazioni. Tale numero deve consentire non solo di ottenere tempi di risposta soddisfacenti, ma anche di impedire la creazione di partizioni con dimensioni eccessive. Un numero maggiore di aggregazioni produce tempi di risposta più brevi ma richiede anche uno spazio di archiviazione maggiore e tempi di calcolo più lunghi. Inoltre, a mano a mano che la procedura guidata progetta nuove aggregazioni, le aggregazioni precedenti generano miglioramenti delle prestazioni decisamente superiori rispetto alle nuove. Anche la riduzione delle aggregazioni di minore utilità contribuisce a migliorare le prestazioni. È possibile controllare il numero di aggregazioni progettate automaticamente utilizzando uno dei metodi seguenti disponibili nella procedura guidata:  
  
-   Specificare un limite per lo spazio di archiviazione delle aggregazioni.  
  
-   Specificare un limite per il miglioramento delle prestazioni.  
  
-   Arrestare manualmente la procedura guidata quando la curva del raffronto tra prestazioni e dimensioni visualizzata inizia a stabilizzarsi su un miglioramento delle prestazioni accettabile.  
  
-   Scegliere di non progettare aggregazioni.  
  
 Per configurare l'archiviazione, la procedura guidata deve connettersi a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] nel server di destinazione. Se [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] non viene eseguito nel server di destinazione o il processo di configurazione dell'archiviazione non riesce a connettersi in altro modo al server di destinazione, verrà visualizzato un messaggio di errore.  
  
 Il passaggio finale della procedura guidata consente di scegliere se eseguire immediatamente l'elaborazione o posticiparla. In caso di elaborazione immediata, vengono create le aggregazioni progettate con la procedura guidata. Se invece si posticipa il processo, le aggregazioni progettate vengono salvate per la futura elaborazione, consentendo tuttavia di proseguire le attività di configurazione. A seconda delle dimensioni della partizione, l'elaborazione potrebbe richiedere tempi lunghi. Se necessario, è possibile scegliere di interrompere l'elaborazione di una partizione.  
  
## <a name="see-also"></a>Vedi anche  
 [Aggregations and Aggregation Designs](../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  
