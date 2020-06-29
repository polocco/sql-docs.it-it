---
title: Estensione del flusso di dati con il componente script | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- data flow task [Integration Services], components
- data flow [Integration Services], extending
- debugging [Integration Services], components
- code design mode [Integration Services]
- metadata [Integration Services]
- scripts [Integration Services], extending data flow
- data flow components [Integration Services], Script component
- components [Integration Services], data flow
- Script component [Integration Services], about Script component
- Script component [Integration Services]
- data flow [Integration Services], components
ms.assetid: 072bc4b8-363a-4131-87c3-240338e2fa5c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c47b45be2c3df0bc0c25a39535a1823dcfa0cefa
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "85426378"
---
# <a name="extending-the-data-flow-with-the-script-component"></a>Estensione del flusso di dati con il componente script
  Il componente script estende le funzionalità del flusso di dati dei pacchetti di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] con codice personalizzato scritto in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic o [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# che viene compilato ed eseguito in fase di esecuzione del pacchetto. Il componente script semplifica lo sviluppo di un'origine, di una trasformazione o di una destinazione personalizzata del flusso di dati quando le origini, le trasformazioni e le destinazioni incluse in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] non soddisfano pienamente specifici requisiti. Dopo aver configurato il componente con gli input e gli output previsti, scrive automaticamente tutto il codice dell'infrastruttura richiesto, consentendo agli sviluppatori di concentrarsi esclusivamente sul codice necessario per l'elaborazione personalizzata.  
  
 Un componente script interagisce con il pacchetto che lo contiene e con il flusso di dati tramite le classi generate automaticamente negli elementi di progetto `ComponentWrapper` e `BufferWrapper`, che sono rispettivamente istanze delle classi <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> e <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer>. Queste classi rendono disponibili connessioni, variabili e altri elementi del pacchetto come oggetti tipizzati e gestiscono input e output. Il componente script può inoltre utilizzare lo spazio dei nomi [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] e la libreria di classi [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], nonché assembly personalizzati, per implementare la funzionalità personalizzata.  
  
 Il componente script e il codice dell'infrastruttura che genera semplificano in modo significativo il processo di sviluppo di un componente del flusso di dati personalizzato. Tuttavia, per comprendere il funzionamento del componente script, può risultare utile leggere informazioni sui passaggi necessari per lo sviluppo di un componente flusso di dati personalizzato nella sezione [Sviluppo di un componente flusso di dati personalizzato](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
 Se si crea un'origine, una trasformazione o una destinazione che si prevede di riutilizzare in più pacchetti, è consigliabile sviluppare un componente personalizzato anziché utilizzare il componente script. Per altre informazioni, vedere [Sviluppo di un componente del flusso di dati personalizzato](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 Negli argomenti seguenti vengono fornite ulteriori informazioni sul componente script.  
  
 [Configurazione del componente script nell'editor corrispondente](configuring-the-script-component-in-the-script-component-editor.md)  
 Le proprietà che si configurano in **Editor trasformazione Script** influiscono sulle funzionalità e sulle prestazioni del codice del componente script.  
  
 [Codifica e debug del componente script] (coding-and-debugging-the-script-component.md  
 Usare l'ambiente di sviluppo di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) per sviluppare gli script contenuti nel componente script.  
  
 [Informazioni sul modello a oggetti del componente script](understanding-the-script-component-object-model.md)  
 Un nuovo progetto di componente script contiene tre elementi di progetto con diverse classi, nonché proprietà e metodi generati automaticamente.  
  
 [Uso di variabili nel componente script](using-variables-in-the-script-component.md)  
 L'elemento di progetto `ComponentWrapper` contiene le proprietà delle funzioni di accesso fortemente tipizzate per le variabili del pacchetto.  
  
 [Connessione a origini dati nel componente script](connecting-to-data-sources-in-the-script-component.md)  
 L'elemento di progetto `ComponentWrapper` contiene le proprietà delle funzioni di accesso fortemente tipizzate per le connessioni definite nel pacchetto.  
  
 [Generazione di eventi nel componente script](raising-events-in-the-script-component.md)  
 È possibile generare eventi per fornire la notifica di problemi ed errori.  
  
 [Registrazione nel componente script](logging-in-the-script-component.md)  
 È possibile registrare informazioni nei provider di log abilitati nel pacchetto.  
  
 [Sviluppo di tipi specifici di componenti script](../../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)  
 In questi semplici esempi viene illustrato come utilizzare il componente script per sviluppare origini, trasformazioni e destinazioni del flusso di dati.  
  
 [Ulteriori esempi di componente script](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
 In questi semplici esempi vengono illustrati alcuni possibili utilizzi del componente script.  
  
![Integration Services icona (piccola)](../../media/dts-16.gif "Icona di Integration Services (piccola)")  **rimane aggiornata con Integration Services**<br /> Per i download, gli articoli, gli esempi e i video [!INCLUDE[msCoName](../../../includes/msconame-md.md)] più recenti, oltre alle soluzioni selezionate dalla community, visitare la pagina [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] su MSDN:<br /><br /> [Visitare la pagina relativa a Integration Services su MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Per ricevere una notifica automatica su questi aggiornamenti, sottoscrivere i feed RSS disponibili nella pagina.  
  
## <a name="see-also"></a>Vedere anche  
 [Componente script](../../data-flow/transformations/script-component.md)   
 [Confronto tra l'attività Script e il componente script](../comparing-the-script-task-and-the-script-component.md)  
  
  
