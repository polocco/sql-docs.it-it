---
title: Editor attività Message Queue (pagina generale) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msgqueuetask.general.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 09368b18-37a5-4321-a173-7cfe5d42d2a2
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 25053ac966629c1265d735df8502eccad1d8a290
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84950931"
---
# <a name="message-queue-task-editor-general-page"></a>Editor attività Message Queue (pagina Generale)
  Utilizzare la pagina **Generale** della finestra di dialogo **Editor attività Message Queue** per assegnare un nome e una descrizione all'attività Message Queue, specificare il formato dei messaggi e impostare l'attività per l'invio o la ricezione dei messaggi.  
  
 Per ulteriori informazioni su questa attività, vedere [Message Queue Task](control-flow/message-queue-task.md).  
  
## <a name="options"></a>Opzioni  
 **Nome**  
 Consente di specificare un nome univoco per l'attività Message Queue. Tale nome viene utilizzato come etichetta nell'icona dell'attività.  
  
> [!NOTE]  
>  I nomi delle attività devono essere univoci all'interno di un pacchetto.  
  
 **Descrizione**  
 Consente di digitare una descrizione dell'attività Message Queue.  
  
 **Use2000Format**  
 Consente di indicare se utilizzare il formato 2000 di Microsoft Message Queuing (noto anche come MSMQ). Il valore predefinito è `False`.  
  
 **MSMQConnection**  
 Selezionare una gestione connessione MSMQ esistente oppure fare clic su \<**New connection...**> per creare una nuova gestione connessione.  
  
 **Argomenti correlati**: [Gestione connessione MSMQ](connection-manager/msmq-connection-manager.md), [Editor gestione connessione MSMQ](../../2014/integration-services/msmq-connection-manager-editor.md)  
  
 **Message**  
 Consente di specificare se l'attività Message Queue invia o riceve messaggi. Se si seleziona **Invia messaggio**, nel riquadro sinistro della finestra di dialogo viene inserita la pagina Invia. Se invece si seleziona **Ricevi messaggio**, viene inserita la pagina Ricevi. Per impostazione predefinita, questo valore è impostato su **Invia messaggio**.  
  
## <a name="see-also"></a>Vedere anche  
 [Integration Services riferimento a errori e messaggi](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor attività Message Queue &#40;pagina ricezione&#41;](../../2014/integration-services/message-queue-task-editor-receive-page.md)   
 [Editor attività Message Queue &#40;Invia pagina&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md)   
 [Pagina Espressioni](expressions/expressions-page.md)  
  
  
