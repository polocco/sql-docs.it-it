---
title: Eseguire un caricamento incrementale di più tabelle | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],multiple tables
ms.assetid: 39252dd5-09c3-46f9-a17b-15208cfd336d
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 7f57e6ae2cf40092304aa0ee3ff99ef5c5725be1
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84922672"
---
# <a name="perform-an-incremental-load-of-multiple-tables"></a>Esecuzione di un caricamento incrementale di più tabelle
  Il diagramma incluso nell'argomento [Miglioramento dei caricamenti incrementali tramite Change Data Capture](change-data-capture-ssis.md)illustra un pacchetto di base che esegue un caricamento incrementale in un'unica tabella. Il caricamento di una tabella, tuttavia, non rappresenta un'operazione tanto comune quanto l'esecuzione di un caricamento incrementale di più tabelle.  
  
 Quando si esegue un caricamento incrementale di più tabelle, alcuni passaggi devono essere eseguiti una volta per tutte le tabelle, mentre altri passaggi devono essere ripetuti per ogni tabella di origine. Per implementare tali passaggi in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], sono disponibili più opzioni:  
  
-   Utilizzare un pacchetto padre e più pacchetti figlio.  
  
-   Utilizzare più attività Flusso di dati in un singolo pacchetto.  
  
## <a name="loading-multiple-tables-by-using-a-parent-package-and-multiple-child-packages"></a>Caricamento di più tabelle tramite un pacchetto padre e più pacchetti figlio  
 È possibile utilizzare un pacchetto padre per i passaggi che devono essere eseguiti solo una volta. I pacchetti figlio verranno utilizzati per i passaggi necessari per ogni tabella di origine.  
  
#### <a name="to-create-a-parent-package-that-performs-those-steps-that-only-have-to-be-done-once"></a>Per creare un pacchetto padre per l'esecuzione dei passaggi necessari solo una volta  
  
1.  Creare un pacchetto padre.  
  
2.  Nel flusso di controllo utilizzare un attività Esegui SQL o espressioni [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per calcolare gli endpoint.  
  
     Per un esempio di come calcolare gli endpoint, vedere [Specificare un intervallo dei dati delle modifiche](specify-an-interval-of-change-data.md).  
  
3.  Se necessario, utilizzare un contenitore Ciclo For per rimandare l'esecuzione fino a quando i dati delle modifiche per il periodo selezionato non saranno pronti.  
  
     Per un esempio di un contenitore Ciclo For di questo tipo, vedere [Determinare se i dati delle modifiche sono pronti](determine-whether-the-change-data-is-ready.md).  
  
4.  Utilizzare più attività Esegui pacchetto per eseguire pacchetti figlio per ogni tabella da caricare. Passare gli endpoint calcolati nel pacchetto padre a ciascun pacchetto figlio utilizzando le configurazioni Variabile pacchetto padre.  
  
     Per altre informazioni, vedere [Attività Esegui pacchetto](../control-flow/execute-package-task.md) e [Utilizzare i valori di variabili e parametri in un pacchetto figlio](../use-the-values-of-variables-and-parameters-in-a-child-package.md).  
  
#### <a name="to-create-child-packages-to-perform-those-steps-that-have-to-be-done-for-each-source-table"></a>Per creare pacchetti figlio per l'esecuzione dei passaggi necessari per ogni tabella di origine  
  
1.  Creare un pacchetto figlio per ogni tabella di origine.  
  
2.  Nel flusso di controllo utilizzare un'attività Script o un'attività Esegui SQL per assemblare l'istruzione SQL da utilizzare per eseguire una query per le modifiche.  
  
     Per un esempio di come assemblare la query, vedere [Preparare l'esecuzione di una query per i dati delle modifiche](prepare-to-query-for-the-change-data.md).  
  
3.  Utilizzare una singola attività Flusso di dati in ogni pacchetto figlio per caricare i dati delle modifiche e applicarli alla destinazione. Configurare il flusso di dati come descritto nei passaggi seguenti:  
  
    1.  Nel flusso di dati utilizzare un componente di origine per eseguire una query sulle tabelle delle modifiche comprese tra gli endpoint selezionati.  
  
         Per un esempio di come eseguire una query sulle tabelle delle modifiche, vedere [Recuperare e comprendere i dati delle modifiche](retrieve-and-understand-the-change-data.md).  
  
    2.  Utilizzare una trasformazione Suddivisione condizionale per indirizzare inserimenti, aggiornamenti ed eliminazioni a output diversi per l'elaborazione appropriata.  
  
         Per un esempio di come configurare questa trasformazione per indirizzare l'output, vedere [Elaborare inserimenti, aggiornamenti ed eliminazioni](process-inserts-updates-and-deletes.md).  
  
    3.  Utilizzare un componente di destinazione per applicare gli inserimenti alla destinazione. Utilizzare trasformazioni Comando OLE DB con istruzioni UPDATE e DELETE con parametri per applicare aggiornamenti ed eliminazioni alla destinazione.  
  
         Per un esempio di come usare questa trasformazione per applicare aggiornamenti ed eliminazioni, vedere [Applicare le modifiche alla destinazione](apply-the-changes-to-the-destination.md).  
  
## <a name="loading-multiple-tables-by-using-multiple-data-flow-tasks-in-a-single-package"></a>Caricamento di più tabelle tramite più attività Flusso di dati in un singolo pacchetto  
 In alternativa, è possibile utilizzare un singolo pacchetto contenente un'attività Flusso di dati distinta per ogni tabella di origine da caricare.  
  
#### <a name="to-load-multiple-tables-by-using-multiple-data-flow-tasks-in-a-single-package"></a>Per caricare più tabelle utilizzando più attività Flusso di dati in un singolo pacchetto  
  
1.  Creare un singolo pacchetto.  
  
2.  Nel flusso di controllo utilizzare un'attività Esegui SQL o espressioni [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per calcolare gli endpoint.  
  
     Per un esempio di come calcolare gli endpoint, vedere [Specificare un intervallo dei dati delle modifiche](specify-an-interval-of-change-data.md).  
  
3.  Se necessario, utilizzare un contenitore Ciclo For per rimandare l'esecuzione fino a quando i dati delle modifiche per l'intervallo selezionato non saranno pronti.  
  
     Per un esempio di un contenitore Ciclo For di questo tipo, vedere [Determinare se i dati delle modifiche sono pronti](determine-whether-the-change-data-is-ready.md).  
  
4.  Utilizzare un'attività Script o un'attività Esegui SQL per assemblare l'istruzione SQL da utilizzare per eseguire una query per le modifiche.  
  
     Per un esempio di come assemblare la query, vedere [Preparare l'esecuzione di una query per i dati delle modifiche](prepare-to-query-for-the-change-data.md).  
  
5.  Utilizzare più attività Flusso di dati per caricare i dati delle modifiche da ogni tabella di origine e applicarli alla destinazione. Configurare ogni attività Flusso di dati come descritto nei passaggi seguenti:  
  
    1.  In ogni flusso di dati utilizzare un componente di origine per eseguire una query sulle tabelle delle modifiche comprese tra gli endpoint selezionati.  
  
         Per un esempio di come eseguire una query sulle tabelle delle modifiche, vedere [Recuperare e comprendere i dati delle modifiche](retrieve-and-understand-the-change-data.md).  
  
    2.  Utilizzare una trasformazione Suddivisione condizionale per indirizzare inserimenti, aggiornamenti ed eliminazioni a output diversi per l'elaborazione appropriata.  
  
         Per un esempio di come configurare questa trasformazione per indirizzare l'output, vedere [Elaborare inserimenti, aggiornamenti ed eliminazioni](process-inserts-updates-and-deletes.md).  
  
    3.  Utilizzare un componente di destinazione per applicare gli inserimenti alla destinazione. Utilizzare trasformazioni Comando OLE DB con istruzioni UPDATE e DELETE con parametri per applicare aggiornamenti ed eliminazioni alla destinazione.  
  
         Per un esempio di come usare questa trasformazione per applicare aggiornamenti ed eliminazioni, vedere [Applicare le modifiche alla destinazione](apply-the-changes-to-the-destination.md).  
  
  
