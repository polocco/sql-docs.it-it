---
title: Aggiornamento di Monitoraggio attività processi | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.jobactivitymon.refresh.f1
ms.assetid: 413a368e-fd2b-4e1f-b370-002cdbc85bab
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5f290825f8a776c954ef802b184f7600aea5dc9d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85024357"
---
# <a name="job-activity-monitor-refresh"></a>Aggiornamento di Monitoraggio attività processi
  Utilizzare la finestra di dialogo **Impostazioni aggiornamento** per configurare la frequenza di acquisizione di nuove informazioni sull'attività del server da parte di Monitoraggio attività processi. Monitoraggio attività processi deve eseguire query sul server monitorato per ottenere informazioni per la griglia Monitoraggio attività processi. Quando l'intervallo di aggiornamento automatico è impostato su un valore inferiore a 30 secondi, il tempo impiegato per eseguire queste query può ridurre le prestazioni del server.  
  
 Per aprire questa finestra di dialogo fare clic su **Visualizza impostazioni di aggiornamento**nella sezione **Stato** di Monitoraggio attività processi.  
  
## <a name="options"></a>Opzioni  
 **Aggiorna automaticamente ogni**  
 Selezionare questa opzione per iniziare l'aggiornamento automatico delle informazioni di Monitoraggio attività. Questa opzione è deselezionata per impostazione predefinita.  
  
 **secondi**  
 Il numero di secondi che intercorrono tra i tentativi di aggiornamento automatici. Il valore predefinito è 60 secondi. Quando questa opzione è impostata su un valore uguale o inferiore a 5 l'aggiornamento viene eseguito comunque ogni 5 secondi.  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio delle attività del processo](../../ssms/agent/monitor-job-activity.md)  
  
  
