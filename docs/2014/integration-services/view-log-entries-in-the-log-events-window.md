---
title: Visualizzare le voci di log nella finestra Registra eventi | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], viewing
- Integration Services packages, logs
- packages [Integration Services], logs
ms.assetid: c02123c3-67fc-4370-ad14-91ed259f1873
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7a2fddc08a92477d18f4bf7ce14312d1ef531fae
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "85420088"
---
# <a name="view-log-entries-in-the-log-events-window"></a>Visualizzare le voci di log nella finestra Registra eventi
  In questo argomento viene descritta la procedura per eseguire un pacchetto e visualizzare le voci di log scritte da tale pacchetto. È possibile visualizzare le voci di log in tempo reale. Le voci di log scritte nella finestra **Registra eventi** possono inoltre essere copiate e salvate per analisi ulteriori.  
  
 Per scrivere le voci di log nella finestra **Registra eventi** non è necessario scriverle in un log.  
  
### <a name="to-view-log-entries"></a>Per visualizzare voci di log  
  
1.  In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  Scegliere **Registra eventi**dal menu **SSIS** . Facoltativamente, è possibile visualizzare la finestra **Registra eventi** eseguendo il mapping tra il comando View.LogEvents e una combinazione di tasti scelta dall'utente nella pagina **Tastiera** della finestra di dialogo **Opzioni** .  
  
3.  Scegliere **Avvia debug**dal menu **debug** .  
  
     Quando il runtime rileva i messaggi personalizzati e gli eventi per cui è attivata la registrazione, le voci di log per ogni evento o messaggio vengono scritte nella finestra **Registra eventi** .  
  
4.  Scegliere **Arresta debug** dal menu **Debug**.  
  
     Le voci di log rimangono disponibili nella finestra **Registra eventi** finché non si esegue nuovamente il pacchetto, non si esegue un pacchetto diverso o non si chiude [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
5.  Esaminare le voci di log nella finestra **Registra eventi** .  
  
6.  Facoltativamente, selezionare le voci di log da copiare, fare clic con il pulsante destro del mouse e quindi scegliere **Copia**.  
  
7.  Facoltativamente, fare doppio clic su una voce di log e, nella finestra di dialogo **Voce log** , esaminare i dettagli della singola voce di log selezionata.  
  
8.  Nella finestra di dialogo **Voce log** usare le frecce SU o GIÙ per visualizzare la voce di log precedente o successiva e quindi fare clic sull'icona Copia per copiare la voce di log selezionata.  
  
9. Aprire un editor di testo, incollare e quindi salvare la voce di log in un file di testo.  
  
## <a name="see-also"></a>Vedere anche  
 [Registrazione di Integration Services &#40;SSIS&#41;](performance/integration-services-ssis-logging.md)  
  
  
