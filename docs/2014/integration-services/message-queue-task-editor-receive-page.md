---
title: Editor attività Message Queue (pagina ricezione) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msgqueuetask.receive.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 7028756d-1dcc-480c-bbcd-e9654f0772a0
author: janinezhang
ms.author: janinez
ms.openlocfilehash: b30a7863fe50843f4408931b2b766bcb520f3a2c
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84950991"
---
# <a name="message-queue-task-editor-receive-page"></a>Editor attività Message Queue (pagina Ricezione)
  Usare la pagina **Ricezione** della finestra di dialogo **Editor attività Message Queue** per configurare un'attività Message Queue che consenta di ricevere messaggi di [!INCLUDE[msCoName](../includes/msconame-md.md)] Message Queuing (MSMQ).  
  
 Per ulteriori informazioni su questa attività, vedere [Message Queue Task](control-flow/message-queue-task.md).  
  
## <a name="options"></a>Opzioni  
 **RemoveFromMessageQueue**  
 Consente di indicare se rimuovere il messaggio dalla coda dopo averlo ricevuto. Per impostazione predefinita, questo valore è impostato su `False`.  
  
 **ErrorIfMessageTimeOut**  
 Consente di indicare se l'attività viene interrotta quando si verifica il timeout del messaggio, visualizzando un messaggio di errore. Il valore predefinito è `False`.  
  
 **TimeoutAfter**  
 Se si sceglie di visualizzare un messaggio di errore in caso di errore dell'attività, specificare il numero di secondi di attesa prima della visualizzazione del messaggio di timeout.  
  
 **MessageType**  
 Consente di selezionare il tipo di messaggio. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|**Messaggio file di dati**|Il messaggio viene archiviato in un file. La selezione del valore determina la visualizzazione dell'opzione dinamica **DataFileMessage**.|  
|**Messaggio variabili**|Il messaggio viene archiviato in una variabile. La selezione del valore determina la visualizzazione dell'opzione dinamica **VariableMessage**.|  
|**Messaggio stringa**|Il messaggio viene archiviato nell'attività Message Queue. La selezione del valore determina la visualizzazione dell'opzione dinamica **StringMessage**.|  
|**Messaggio stringa in variabile**|Il messaggio viene archiviato in una variabile.<br /><br /> La selezione del valore determina la visualizzazione dell'opzione dinamica **StringMessage**.|  
  
## <a name="messagetype-dynamic-options"></a>Opzioni dinamiche di MessageType  
  
### <a name="messagetype--data-file-message"></a>MessageType = Messaggio file di dati  
 **SaveFileAs**  
 Digitare il percorso del file da usare o fare clic sul pulsante con i puntini di sospensione **(...)** e quindi individuare il file.  
  
 **Sovrascrivere**  
 Consente di indicare se sovrascrivere i dati in un file esistente durante il salvataggio del contenuto di un messaggio con file di dati. Il valore predefinito è `False`.  
  
 **Filter**  
 Consente di specificare se applicare un filtro al messaggio. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|**Nessun filtro**|L'attività non filtra i messaggi. La selezione del valore determina la visualizzazione dell'opzione dinamica **IdentifierReadOnly**.|  
|**Dal pacchetto**|Il messaggio riceve solo messaggi dal pacchetto specificato. La selezione del valore determina la visualizzazione dell'opzione dinamica **Identifier**.|  
  
### <a name="filter-dynamic-options"></a>Opzioni dinamiche di filtro  
  
#### <a name="filter--no-filter"></a>Filter = Nessun filtro  
 **IdentifierReadOnly**  
 Questa opzione è di sola lettura. Può essere vuota o contenere il GUID di un pacchetto se la proprietà Filter è stata impostata in precedenza.  
  
#### <a name="filter--from-package"></a>Filter = Dal pacchetto  
 **Identificatore**  
 Se si sceglie di applicare un filtro, digitare l'identificatore univoco del pacchetto da cui si possono ricevere i messaggi oppure fare clic sul pulsante con i puntini di sospensione **(...)** e specificare il pacchetto.  
  
 **Argomenti correlati:** [Seleziona pacchetto](control-flow/select-a-package.md)  
  
### <a name="messagetype--variable-message"></a>MessageType = Messaggio variabili  
 **Filter**  
 Consente di specificare se applicare un filtro ai messaggi. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|**Nessun filtro**|L'attività non filtra i messaggi. La selezione del valore determina la visualizzazione dell'opzione dinamica **IdentifierReadOnly**.|  
|**Dal pacchetto**|Il messaggio riceve solo messaggi dal pacchetto specificato. La selezione del valore determina la visualizzazione dell'opzione dinamica **Identifier**.|  
  
 **Variabile**  
 Digitare il nome della variabile oppure fare clic su \<**New variable...**> e quindi configurare una nuova variabile.  
  
 **Argomenti correlati:** [Aggiungi variabile](../../2014/integration-services/add-variable.md)  
  
### <a name="filter-dynamic-options"></a>Opzioni dinamiche di filtro  
  
#### <a name="filter--no-filter"></a>Filter = Nessun filtro  
 **IdentifierReadOnly**  
 Questa opzione è vuota.  
  
#### <a name="filter--from-package"></a>Filter = Dal pacchetto  
 **Identificatore**  
 Se si sceglie di applicare un filtro, digitare l'identificatore univoco del pacchetto da cui si possono ricevere i messaggi oppure fare clic sul pulsante con i puntini di sospensione **(...)** e specificare il pacchetto.  
  
 **Argomenti correlati:** [Seleziona pacchetto](control-flow/select-a-package.md)  
  
### <a name="messagetype--string-message"></a>MessageType = Messaggio stringa  
 **Confronto**  
 Consente di specificare se applicare un filtro ai messaggi. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|valore|Descrizione|  
|-----------|-----------------|  
|**Nessuno**|I messaggi non vengono confrontati.|  
|**Corrispondenza esatta**|I messaggi devono corrispondere esattamente alla stringa nell'opzione indicata **CompareString** .|  
|**Ignora maiuscole/minuscole**|I messaggi devono corrispondere alla stringa indicata nell'opzione **CompareString** , ma nel confronto non viene rilevata la distinzione tra maiuscole e minuscole.|  
|**Stringa contenente**|Il messaggio deve contenere la stringa indicata nell'opzione **CompareString** .|  
  
 **CompareString**  
 Specificare la stringa con cui confrontare il messaggio, a meno che l'opzione **Compare** sia impostata su **Nessuno**.  
  
### <a name="messagetype--string-message-to-variable"></a>MessageType = Messaggio stringa in variabile  
 **Confronto**  
 Consente di specificare se applicare un filtro ai messaggi. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|valore|Descrizione|  
|-----------|-----------------|  
|**Nessuno**|I messaggi non vengono confrontati.|  
|**Corrispondenza esatta**|I messaggi devono corrispondere esattamente alla stringa indicata nell'opzione **CompareString** .|  
|**Ignora maiuscole/minuscole**|I messaggi devono corrispondere alla stringa indicata nell'opzione **CompareString** , ma nel confronto non viene rilevata la distinzione tra maiuscole e minuscole.|  
|**Stringa contenente**|Il messaggio deve contenere la stringa indicata nell'opzione **CompareString** .|  
  
 **CompareString**  
 Specificare la stringa con cui confrontare il messaggio, a meno che l'opzione **Compare** sia impostata su **Nessuno**.  
  
 **Variabile**  
 Digitare il nome della variabile in cui inserire il messaggio ricevuto oppure fare clic su \<**New variable...**> e quindi configurare una nuova variabile.  
  
 **Argomenti correlati:** [Aggiungi variabile](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Integration Services riferimento a errori e messaggi](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor attività Message Queue &#40;pagina generale&#41;](general-page-of-integration-services-designers-options.md)   
 [Editor attività Message Queue &#40;Invia pagina&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md)   
 [Pagina espressioni](expressions/expressions-page.md)   
 [Attività Message Queue](control-flow/message-queue-task.md)  
  
  
