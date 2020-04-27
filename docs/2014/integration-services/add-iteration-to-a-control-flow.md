---
title: Aggiungere un'iterazione a un flusso di controllo | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- repeating workflows
- adding iterations
- control flow [Integration Services], iterations
- expressions [Integration Services], control flow
- iterations [Integration Services]
- For Loop containers
ms.assetid: eb3a7494-88ae-4165-9d0f-58715eb1734a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b96f5f900e8c1a3adf136c7bdaf1b89f297e4921
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66061976"
---
# <a name="add-iteration-to-a-control-flow"></a>Aggiunta di un'iterazione a un flusso di controllo
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] include il contenitore Ciclo For, un elemento del flusso di controllo che semplifica l'implementazione di un ciclo che consente la ripetizione condizionale di un flusso di controllo in un pacchetto. Per altre informazioni, vedere [Contenitore Ciclo For](control-flow/for-loop-container.md).  
  
 Il contenitore Ciclo For valuta una condizione a ogni iterazione del ciclo e si arresta quando la condizione restituisce False. Il contenitore Ciclo For include espressioni per l'inizializzazione del ciclo, la definizione della condizione da valutare per determinare se arrestare o meno l'esecuzione del flusso di controllo ripetuto, nonché l'assegnazione di un valore a un'espressione che aggiorna il valore con cui confrontare la condizione da valutare. La condizione da valutare è obbligatoria, mentre le espressioni di inizializzazione e di assegnazione sono facoltative.  
  
 Il contenitore Ciclo For non offre funzionalità, ma solo una struttura in cui compilare un flusso di controllo ripetibile. Per aggiungere funzionalità al contenitore Ciclo For è necessario includervi almeno un'attività. Per altre informazioni, vedere [Attività di Integration Services](control-flow/integration-services-tasks.md).  
  
 Il contenitore Ciclo For può includere un flusso di controllo con più attività e altri contenitori. L'aggiunta di attività e contenitori a un contenitore Ciclo For è analoga all'aggiunta di tali elementi a un pacchetto, con la differenza che è necessario trascinare attività e contenitori nel contenitore Ciclo For anziché nel pacchetto. Se il contenitore Ciclo For include più di un contenitore o attività, sarà possibile connettere tali elementi utilizzando vincoli di precedenza, come avviene nei pacchetti. Per altre informazioni, vedere [Vincoli di precedenza](control-flow/precedence-constraints.md).  
  
## <a name="using-expressions-in-for-loop-configuration"></a>Utilizzo di espressioni nella configurazione di un Ciclo For  
 Quando si configura il contenitore Ciclo For specificando una condizione da valutare, un valore di inizializzazione o un valore di assegnazione, è possibile utilizzare valori letterali o espressioni.  
  
 Le espressioni possono includere variabili. Il vantaggio delle variabili è che possono essere aggiornate in fase di esecuzione, rendendo il pacchetto più flessibile e più facile da gestire. Un'espressione può avere una lunghezza massima di 4000 caratteri.  
  
 Quando si specifica una variabile in un'espressione è necessario anteporre il simbolo @ al nome della variabile. Per una variabile denominata `Counter`, ad esempio, immettere @Counter nell'espressione utilizzata dal contenitore ciclo for. Se la variabile include la proprietà Namespace, sarà necessario racchiudere la variabile e lo spazio dei nomi tra parentesi quadre. Per una `Counter` variabile nello `MyNamespace` spazio dei nomi, ad esempio, digitare@MyNamespace::Counter[].  
  
 Le variabili utilizzate dal contenitore Ciclo For devono essere definite nell'ambito del contenitore Ciclo For o di un altro contenitore di livello superiore nella gerarchia dei contenitori del pacchetto. Un contenitore Ciclo For può ad esempio utilizzare sia variabili definite nel proprio ambito, sia variabili definite nell'ambito del pacchetto. Per altre informazioni, vedere [Variabili di Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md) e [Utilizzo di variabili nei pacchetti](../../2014/integration-services/use-variables-in-packages.md).  
  
 La grammatica delle espressioni di [!INCLUDE[ssIS](../includes/ssis-md.md)] offre un set completo di operatori e funzioni per l'implementazione di espressioni complesse che è possibile utilizzare per la valutazione, l'inizializzazione o l'assegnazione. Per altre informazioni, vedere [Espressioni di Integration Services &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md).  
  
### <a name="to-implement-a-for-loop-container-in-a-control-flow"></a>Per implementare un contenitore Ciclo For in un flusso di controllo  
  
1.  Aggiungere il contenitore Ciclo For al pacchetto. Per altre informazioni, vedere [aggiungere o eliminare un'attività o un contenitore in un flusso di controllo](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  .  
  
2.  Aggiungere attività e contenitori al contenitore Ciclo For. Per altre informazioni, vedere [aggiungere o eliminare un'attività o un contenitore in un flusso di controllo](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  .  
  
3.  Connettere le attività e i contenitori inclusi nel contenitore Ciclo For tramite vincoli di precedenza. Per altre informazioni, vedere [Connessione di attività e contenitori tramite un vincolo di precedenza predefinito](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md).  
  
4.  Configurare il contenitore Ciclo For. Per altre informazioni, vedere [Configurazione di un contenitore Ciclo For](../../2014/integration-services/configure-a-for-loop-container.md).  
  
## <a name="see-also"></a>Vedi anche  
 [Aggiungere o eliminare un'attività o un contenitore in un flusso di controllo](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)   
 [Raggruppare o disraggruppare componenti](group-or-ungroup-components.md)   
 [Connessione di attività e contenitori tramite un vincolo di precedenza predefinito](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)   
 [Aggiungere un'enumerazione a un flusso di controllo](../../2014/integration-services/add-enumeration-to-a-control-flow.md)   
 [Flusso di controllo](control-flow/control-flow.md)  
  
  
