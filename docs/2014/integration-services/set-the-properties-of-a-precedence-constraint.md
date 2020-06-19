---
title: Impostare le proprietà di un vincolo di precedenza | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Precedence Constraint Editor dialog box
- precedence constraints [Integration Services], properties
ms.assetid: d990f600-5c09-4cd5-8528-0a58d79dc9f2
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 679e61c37df7d31b80f47fff186589ce0081f838
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84963121"
---
# <a name="set-the-properties-of-a-precedence-constraint"></a>Impostazione delle proprietà di un vincolo di precedenza
  Per impostare le proprietà dei vincoli di precedenza, è possibile utilizzare uno dei seguenti strumenti:  
  
-   La finestra di dialogo **Editor vincoli di precedenza** .  
  
-   La finestra Proprietà. Nella finestra Proprietà sono elencate le proprietà per la configurazione dei vincoli di precedenza non disponibili nella finestra di dialogo **Editor vincoli di precedenza** . ed è possibile specificare una descrizione e un nome del vincolo di precedenza, nonché configurare l'annotazione da visualizzare per il vincolo di precedenza nell'area di progettazione.  
  
 Nelle procedure seguenti viene descritta l'impostazione delle proprietà dei vincoli di precedenza tramite ognuno di questi strumenti.  
  
### <a name="to-set-the-properties-of-a-precedence-constraint-by-using-the-precedence-constraint-editor"></a>Per impostare le proprietà di un vincolo di precedenza tramite Editor vincoli di precedenza  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  Fare clic sulla scheda **Flusso di controllo** .  
  
4.  Fare doppio clic sul vincolo di precedenza.  
  
     Verrà aperta la finestra di dialogo **Editor vincoli di precedenza** .  
  
5.  Nell'elenco a discesa **Operazione valutazione** selezionare un'operazione di valutazione.  
  
6.  Nell' `Value` elenco a discesa selezionare il risultato dell'esecuzione dell'eseguibile con precedenza.  
  
7.  Se l'operazione di valutazione utilizza un'espressione, `Expression` digitare un'espressione nella casella e fare clic su **test** per valutare l'espressione.  
  
    > [!NOTE]  
    >  Per i nomi delle variabili viene fatta distinzione tra maiuscole e minuscole.  
  
8.  Se all'eseguibile soggetto al vincolo sono connessi più contenitori o attività, selezionare **and logico** per specificare che i risultati dell'esecuzione di tutti i file eseguibili precedenti devono restituire `true` . Selezionare **OR logico** per specificare che un solo risultato di esecuzione deve restituire `true` .  
  
9. Scegliere **OK** per chiudere la finestra **Editor vincoli di precedenza**.  
  
10. Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
### <a name="to-set-the-properties-of-a-precedence-constraint-by-using-the-properties-window"></a>Per impostare le proprietà di un vincolo di precedenza tramite la finestra Proprietà  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] che contiene il pacchetto da modificare.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  Fare clic sulla scheda **flusso di controllo** . Nell'area di progettazione della scheda **flusso di controllo** fare clic con il pulsante destro del mouse sul vincolo di precedenza, quindi scegliere **Proprietà**. Nella finestra Proprietà modificare i valori delle proprietà.  
  
4.  Nella finestra **Proprietà** impostare le proprietà di lettura/scrittura seguenti dei vincoli di precedenza:  
  
    |Proprietà di lettura/scrittura|Azione di configurazione|  
    |--------------------------|--------------------------|  
    |Description|Specificare una descrizione.|  
    |EvalOp|Selezionare un'operazione di valutazione. Se `Expression` è selezionata l'operazione, **ExpressionAndConstant**o **ExpressionOrConstant** , è possibile specificare un'espressione.|  
    |Expression|Se l'operazione di valutazione include un'espressione, specificare l'espressione. L'espressione deve restituire un valore booleano. Per altre informazioni sul linguaggio delle espressioni, vedere [Espressioni di Integration Services &#40;SSIS&#41;](expressions/integration-services-ssis-expressions.md).|  
    |LogicalAnd|Impostare `LogicalAnd` per specificare se il vincolo di precedenza viene valutato insieme ad altri vincoli di precedenza, quando più eseguibili precedono e sono collegati all'eseguibile soggetto al vincolo|  
    |Nome|Aggiornare il nome del vincolo di precedenza.|  
    |ShowAnnotation|Specificare il tipo di annotazione da utilizzare. Selezionare **Never** per disabilitare le annotazioni, **AsNeeded** per attivare le annotazioni su richiesta, **ConstraintName** per aggiungere automaticamente annotazioni usando il valore della proprietà Name, **ConstraintDescription** per aggiungere automaticamente annotazioni usando il valore della proprietà Description e **ConstraintOptions** per aggiungere automaticamente annotazioni usando i valori delle proprietà Value ed Expression.|  
    |valore|Se l'operazione di valutazione specificata nella proprietà EvalOP include un vincolo, selezionare il risultato dell'esecuzione dell'eseguibile vincolante.|  
  
5.  Chiudere la finestra Proprietà.  
  
6.  Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
## <a name="see-also"></a>Vedere anche  
 [Vincoli di precedenza](control-flow/precedence-constraints.md)   
 [Connessione di attività e contenitori tramite un vincolo di precedenza predefinito](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)   
 [Impostare il valore di un vincolo di precedenza tramite il menu di scelta rapida](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md)   
 [Uso di un'espressione in un vincolo di precedenza](../../2014/integration-services/use-an-expression-in-a-precedence-constraint.md)  
  
  
