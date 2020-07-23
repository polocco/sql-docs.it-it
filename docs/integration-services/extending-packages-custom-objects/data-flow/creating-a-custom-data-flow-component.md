---
title: Creazione di un componente flusso di dati personalizzato | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- design-time component interface [Integration Services]
- custom data flow components [Integration Services], about data flow components
- custom data flow components [Integration Services]
- data flow components [Integration Services]
- data flow components [Integration Services], developing
ms.assetid: 9d96bcf5-eba8-44bd-b113-ed51ad0d0521
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f7acd3f9c218a068f5af09da21ec21b1fcf6e065
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2020
ms.locfileid: "86921257"
---
# <a name="creating-a-custom-data-flow-component"></a>Creazione di un componente flusso di dati personalizzato

[!INCLUDE[sqlserver-ssis](../../../includes/applies-to-version/sqlserver-ssis.md)]


  In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] l'attività Flusso di dati espone un modello a oggetti che consente agli sviluppatori di creare componenti flusso di dati personalizzati, ovvero origini, trasformazioni e destinazioni, usando [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] e codice gestito.  
  
 Un'attività Flusso di dati è costituita da componenti che contengono un'interfaccia <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> e una raccolta di oggetti <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100> che definiscono lo spostamento di dati tra componenti.  
  
> [!NOTE]  
>  Quando si crea un provider personalizzato, è necessario aggiornare il file ProviderDescriptors.xml con i valori delle colonne di metadati.  
  
## <a name="design-time-and-run-time"></a>Fase di progettazione e di esecuzione  
 Prima dell'esecuzione, l'attività Flusso di dati si trova nel cosiddetto stato della fase di progettazione, quando viene sottoposta a modifiche incrementali. Tali modifiche possono includere l'aggiunta o la rimozione di componenti, l'aggiunta o la rimozione degli oggetti percorso che connettono i componenti e modifiche ai metadati dei componenti. Quando si verificano modifiche ai metadati, il componente può monitorarle e rispondere. Ad esempio, un componente può impedire determinate modifiche o aggiungerne altre in risposta a una modifica. In fase di progettazione la finestra di progettazione interagisce con un componente tramite l'interfaccia <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> della fase di progettazione.  
  
 In fase di esecuzione l'attività Flusso di dati esamina la sequenza di componenti, prepara un piano di esecuzione e gestisce un pool di thread di lavoro che eseguono il piano di lavoro. Anche se ogni thread di lavoro esegue alcune operazioni interne all'attività Flusso di dati, la principale attività di questo thread è chiamare i metodi del componente tramite l'interfaccia <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> di runtime.  
  
## <a name="creating-a-component"></a>Creazione di un componente  
 Per creare un componente flusso di dati, derivare una classe dalla classe di base <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>, applicare la classe <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>, quindi eseguire l'override dei metodi appropriati della classe di base. L'oggetto <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> implementa le interfacce <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> e <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> ed espone i relativi metodi da sottoporre a override nel componente.  
  
 A seconda degli oggetti utilizzati dal componente, il progetto richiederà riferimenti ad alcuni o a tutti gli assembly seguenti:  
  
|Funzionalità|Assembly a cui fare riferimento|Spazio dei nomi da importare|  
|-------------|---------------------------|-------------------------|  
|Flusso di dati|Microsoft.SqlServer.PipelineHost|<xref:Microsoft.SqlServer.Dts.Pipeline>|  
|Wrapper del flusso di dati|Microsoft.SqlServer.DTSPipelineWrap|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>|  
|Runtime|Microsoft.SQLServer.ManagedDTS|<xref:Microsoft.SqlServer.Dts.Runtime>|  
|Wrapper del runtime|Microsoft.SqlServer.DTSRuntimeWrap|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper>|  
  
 Nell'esempio di codice seguente è illustrato un componente semplice che deriva dalla classe di base e applica <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>. È necessario aggiungere un riferimento all'assembly Microsoft.SqlServer.DTSPipelineWrap.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.Samples.SqlServer.Dts  
{  
    [DtsPipelineComponent(DisplayName = "SampleComponent", ComponentType = ComponentType.Transform )]  
    public class BasicComponent: PipelineComponent  
    {  
        // TODO: Override the base class methods.  
    }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
<DtsPipelineComponent(DisplayName:="SampleComponent", ComponentType:=ComponentType.Transform)> _  
Public Class BasicComponent  
  
    Inherits PipelineComponent  
  
    ' TODO: Override the base class methods.  
  
End Class  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un'interfaccia utente per un componente flusso di dati](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-user-interface-for-a-data-flow-component.md)  
  
  
