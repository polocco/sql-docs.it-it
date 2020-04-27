---
title: Editor attività file System (pagina generale) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.filesystemtask.general.f1
helpviewer_keywords:
- File System Task Editor
ms.assetid: 51fe6614-3418-4eff-a28d-02ea31cc9aa9
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 594b87b3e2d58ffe60bd3c31324811a66038c82b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66058808"
---
# <a name="file-system-task-editor-general-page"></a>Editor attività File system (pagina Generale)
  Usare la pagina **Generale** della finestra di dialogo **Editor attività File system** per configurare l'operazione di file system eseguita dall'attività.  
  
 Per altre informazioni su questa attività, vedere [Attività Inserimento bulk](control-flow/file-system-task.md).  
  
 È necessario specificare una gestione connessione di origine e di destinazione impostando le proprietà SourceConnection e DestinationConnection. È possibile specificare i nomi delle gestioni connessione file che puntano ai file utilizzati dall'attività come origine o come destinazione oppure, se i percorsi dei file sono archiviati in variabili, è possibile specificare i nomi delle variabili. Per usare variabili per l'archiviazione dei percorsi dei file, è innanzitutto necessario impostare su **True**l'opzione IsSourcePathVariable per la connessione di origine e l'opzione IsDestinationPathVariable per la connessione di destinazione. È quindi possibile scegliere quali variabili utilizzare tra le variabili di sistema o definite dall'utente esistenti, oppure creare nuove variabili. Nella finestra di dialogo **Aggiungi variabile** è possibile configurare e specificare l'ambito delle variabili. L'ambito deve essere l'attività File system o un contenitore padre. Per ulteriori informazioni, vedere [Integration Services &#40;variabili&#41; SSIS](integration-services-ssis-variables.md) e [utilizzare variabili nei pacchetti](../../2014/integration-services/use-variables-in-packages.md).  
  
> [!NOTE]  
>  Per eseguire l'override delle variabili selezionate per `SourceConnection` le `DestinationConnection` proprietà e, immettere un'espressione per le proprietà di **origine** e di **destinazione** . Le espressioni devono essere immesse nella pagina **Espressioni** di **Editor attività File system**. Ad esempio, per impostare il percorso dei file utilizzati dall'attività come destinazione, potrebbe essere necessario utilizzare la variabile A in determinate condizione e la variabile B in altre.  
  
> [!NOTE]  
>  L'attività File system opera su un singolo file o directory. Pertanto, questa attività non supporta l'utilizzo di caratteri jolly per eseguire la stessa operazione su più file o directory. Affinché l'attività File system ripeta un'operazione su più file o directory, inserirla in un contenitore Ciclo Foreach. Per altre informazioni, vedere [Attività File system](control-flow/file-system-task.md).  
  
 Con le espressioni è possibile utilizzare variabili differenti per  
  
## <a name="options"></a>Opzioni  
 **IsDestinationPathVariable**  
 Consente di specificare se il percorso di destinazione è archiviato in una variabile. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|valore|Descrizione|  
|-----------|-----------------|  
|**True**|Il percorso di destinazione è archiviato in una variabile. Se si seleziona questo valore, viene visualizzata l'opzione dinamica **DestinationVariable**.|  
|**False**|Il percorso di destinazione è specificato in una gestione connessione file. Selezionando questo valore viene visualizzata l'opzione `DestinationConnection`dinamica.|  
  
 **OverwriteDestination**  
 Consente di specificare se l'operazione può sovrascrivere i file nella directory di destinazione.  
  
 **Nome**  
 Consente di specificare un nome univoco per l'attività File system. Tale nome viene utilizzato come etichetta nell'icona dell'attività.  
  
> [!NOTE]  
>  I nomi delle attività devono essere univoci all'interno di un pacchetto.  
  
 **Descrizione**  
 Consente di digitare una descrizione dell'attività File system.  
  
 **Operazione**  
 Consente di selezionare l'operazione di file system da eseguire. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|valore|Descrizione|  
|-----------|-----------------|  
|**Copia directory**|Consente di copiare una directory. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche per l'origine e la destinazione.|  
|**Copia file**|Consente di copiare un file. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche per l'origine e la destinazione.|  
|**Creare la directory**|Creare una directory. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche per una directory di origine e di destinazione.|  
|**Elimina directory**|Consente di eliminare una directory. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche per l'origine.|  
|**Elimina contenuto directory**|Consente di eliminare il contenuto di una directory. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche per l'origine.|  
|**Elimina file**|Consente di eliminare un file. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche per l'origine.|  
|**Sposta directory**|Consente di spostare una directory. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche per l'origine e la destinazione.|  
|**Sposta file**|Consente di spostare un file. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche per l'origine e la destinazione.<br /><br /> Nota: quando si trasferisce un file, non includere un nome file nel percorso della directory fornito come destinazione.|  
|**Rinomina file**|Consente di rinominare un file. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche per l'origine e la destinazione.<br /><br /> Nota: quando si rinomina un file, includere il nuovo nome del file nel percorso della directory fornito per la destinazione.|  
|**Imposta attributi**|Consente di impostare gli attributi di un file o di una directory. Quando si seleziona questo valore vengono visualizzate le opzioni dinamiche per l'origine e l'operazione.|  
  
 `IsSourcePathVariable`  
 Consente di specificare se il percorso di destinazione è archiviato in una variabile. Per questa proprietà sono disponibili le opzioni elencate nella tabella seguente.  
  
|valore||  
|-----------|-|  
|**True**|Il percorso di destinazione è archiviato in una variabile. Se si seleziona questo valore, viene visualizzata l'opzione dinamica **SourceVariable**.|  
|**False**|Il percorso di destinazione è specificato in una gestione connessione file. Se si seleziona questo valore, viene visualizzata l'opzione dinamica **DestinationVariable**.|  
  
## <a name="isdestinationpathvariable-dynamic-options"></a>Opzioni dinamiche di IsDestinationPathVariable  
  
### <a name="isdestinationpathvariable--true"></a>IsDestinationPathVariable = True  
 **DestinationVariable**  
 Consente di selezionare il nome della variabile nell'elenco o di creare una nuova variabile facendo clic su \<**Nuova variabile...**>.  
  
 **Argomenti correlati:** [Integration Services &#40;variabili di&#41; SSIS](integration-services-ssis-variables.md), [Aggiungi variabile](../../2014/integration-services/add-variable.md)  
  
### <a name="isdestinationpathvariable--false"></a>IsDestinationPathVariable = False  
 `DestinationConnection`  
 Selezionare una gestione connessione file nell'elenco oppure fare clic su \< **nuova connessione...**> per creare una nuova gestione connessione.  
  
 **Argomenti correlati:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
## <a name="issourcepathvariable-dynamic-options"></a>Opzioni dinamiche di IsSourcePathVariable  
  
### <a name="issourcepathvariable--true"></a>IsSourcePathVariable = True  
 **SourceVariable**  
 Consente di selezionare il nome della variabile nell'elenco o di creare una nuova variabile facendo clic su \<**Nuova variabile...**>.  
  
 **Argomenti correlati:** [Integration Services &#40;variabili di&#41; SSIS](integration-services-ssis-variables.md), [Aggiungi variabile](../../2014/integration-services/add-variable.md)  
  
### <a name="issourcepathvariable--false"></a>IsSourcePathVariable = False  
 `SourceConnection`  
 Selezionare una gestione connessione file nell'elenco oppure fare clic su \< **nuova connessione...**> per creare una nuova gestione connessione.  
  
 **Argomenti correlati:** [File Connection Manager](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
## <a name="operation-dynamic-options"></a>Opzioni dinamiche di Operation  
  
### <a name="operation--set-attributes"></a>Operation = Imposta attributi  
 **Nascosto**  
 Consente di specificare se il file o la directory è visibile.  
  
 **ReadOnly**  
 Consente di specificare se il file è di sola lettura.  
  
 **Archiviazione**  
 Consente di specificare se il file o la directory è pronta per l'archiviazione.  
  
 **Sistema**  
 Consente di specificare se il file è un file di sistema.  
  
### <a name="operation--create-directory"></a>Operation = Crea directory  
 `UseDirectoryIfExists`  
 Indica se l'operazione **Crea directory** usa una directory esistente con il nome specificato anziché creare una nuova directory.  
  
## <a name="see-also"></a>Vedi anche  
 [Integration Services riferimento a errori e messaggi](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Pagina Espressioni](expressions/expressions-page.md)  
  
  
