---
title: Configurare i checkpoint per il riavvio di un pacchetto non riuscito | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- checkpoints [Integration Services]
- restarting packages
- starting packages
ms.assetid: 9afffa5a-d803-4653-8afc-386453fc163f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c3345ff33c620b1e6fee62b5adba5c2695c47061
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "85438578"
---
# <a name="configure-checkpoints-for-restarting-a-failed-package"></a>Configurazione dei checkpoint per il riavvio di un pacchetto non riuscito
  Impostando le proprietà relative ai checkpoint, è possibile configurare i pacchetti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in modo che vengano riavviati dal momento dell'errore, anziché essere eseguiti nuovamente dall'inizio.  
  
### <a name="to-configure-a-package-to-restart"></a>Per configurare un pacchetto per il riavvio  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenente il pacchetto che si desidera configurare.  
  
2.  In **Esplora soluzioni**fare doppio clic sul pacchetto per aprirlo.  
  
3.  Fare clic sulla scheda **Flusso di controllo** .  
  
4.  Fare clic con il pulsante destro del mouse in un punto qualsiasi dello sfondo dell'area di progettazione del flusso di controllo, quindi scegliere **Proprietà**.  
  
5.  Impostare la proprietà SaveCheckpoints su `True` .  
  
6.  Digitare il nome del file del checkpoint nella proprietà CheckpointFileName.  
  
7.  Impostare la proprietà CheckpointUsage su uno dei due valori seguenti:  
  
    -   Selezionare `Always` per riavviare sempre il pacchetto dal checkpoint.  
  
        > [!IMPORTANT]  
        >  Se il file del checkpoint non è disponibile, viene generato un errore.  
  
    -   Selezionare `IfExists` per riavviare il pacchetto solo se il file del checkpoint è disponibile.  
  
8.  Configurare le attività e i contenitori da cui è possibile riavviare il pacchetto.  
  
    -   Fare clic con il pulsante destro del mouse su un'attività o un contenitore, quindi scegliere **Proprietà**.  
  
    -   Impostare la proprietà FailPackageOnFailure su `True` per ogni attività e contenitore selezionati.  
  
## <a name="see-also"></a>Vedere anche  
 [Riavvio dei pacchetti tramite checkpoint](packages/restart-packages-by-using-checkpoints.md)  
  
  
