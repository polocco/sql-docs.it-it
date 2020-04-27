---
title: Generazione e definizione di eventi in un'attività personalizzata | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SSIS events, custom
- status information [SQL Server], task events
- custom tasks [Integration Services], events
- SSIS custom tasks, events
- IDTSComponentEvents interface
- events [Integration Services], custom
- events [Integration Services], runtime
- custom events [Integration Services]
- SSIS events, runtime
- IDTSEvents interface
ms.assetid: e0898aa1-e90c-4c4e-99d4-708a76efddfd
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: af647a446366ea03063ea0deb84603a3f8f90dd8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62896129"
---
# <a name="raising-and-defining-events-in-a-custom-task"></a>Generazione e definizione di eventi in un'attività personalizzata
  Il motore di runtime di [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] include una raccolta di eventi che forniscono lo stato di avanzamento durante la convalida e l'esecuzione di un'attività. L'interfaccia <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents> definisce questi eventi e viene fornita alle attività come parametro per i metodi <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Validate%2A> e <xref:Microsoft.SqlServer.Dts.Runtime.Executable.Execute%2A>.  
  
 È disponibile un altro set di eventi, definiti nell'interfaccia <xref:Microsoft.SqlServer.Dts.Runtime.IDTSEvents>, che vengono generati per conto dell'attività da <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>. L'oggetto <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> genera gli eventi che si verificano prima e dopo la convalida e l'esecuzione, mentre l'attività genera gli eventi che si verificano durante l'esecuzione e la convalida.  
  
## <a name="creating-custom-events"></a>Creazione di eventi personalizzati  
 Gli sviluppatori di attività personalizzate possono definire nuovi eventi personalizzati creando un nuovo oggetto <xref:Microsoft.SqlServer.Dts.Runtime.EventInfo> nell'implementazione sottoposta a override del metodo <xref:Microsoft.SqlServer.Dts.Runtime.Task.InitializeTask%2A>. L'oggetto <xref:Microsoft.SqlServer.Dts.Runtime.EventInfo>, una volta creato, viene aggiunto alla raccolta `EventInfos` tramite il metodo <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos.Add%2A>. La firma del metodo <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos.Add%2A> è la seguente:  
  
 `public void Add(string eventName, string description, bool allowEventHandlers, string[] parameterNames, TypeCode[] parameterTypes, string[] parameterDescriptions);`  
  
 Nell'esempio di codice seguente è illustrato il metodo `InitializeTask` di un'attività personalizzata, in cui vengono creati due eventi e vengono impostate le relative proprietà. I nuovi eventi vengono quindi aggiunti alla raccolta <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos>.  
  
 Il primo evento personalizzato presenta un elemento *eventName* di "**OnBeforeIncrement**" e un elemento *description* di "**Fires after the initial value is updated.** " Il parametro successivo, il valore `true`, indica che questo evento deve consentire la creazione di un contenitore del gestore eventi. Il gestore eventi è un contenitore che fornisce la struttura in un pacchetto e servizi alle attività, analogamente ad altri contenitori come Sequence, ForLoop e ForEachLoop. Quando il parametro *AllowEventHandlers* è `true`, <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> gli oggetti vengono creati per l'evento. I parametri definiti per l'evento sono ora disponibili per <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler> nella raccolta di variabili di <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>.  
  
```csharp  
public override void InitializeTask(Connections connections,  
   VariableDispenser variables, IDTSInfoEvents events,  
   IDTSLogging log, EventInfos eventInfos,  
   LogEntryInfos logEntryInfos, ObjectReferenceTracker refTracker)  
{  
    this.eventInfos = eventInfos;  
    string[] paramNames = new string[1];  
    TypeCode[] paramTypes = new TypeCode[1]{TypeCode.Int32};  
    string[] paramDescriptions = new string[1];  
  
    paramNames[0] = "InitialValue";  
    paramDescriptions[0] = "The value before it is incremented.";  
  
    this.eventInfos.Add("OnBeforeIncrement",   
      "Fires before the task increments the value.",  
      true,paramNames,paramTypes,paramDescriptions);  
    this.onBeforeIncrement = this.eventInfos["OnBeforeIncrement"];  
  
    paramDescriptions[0] = "The value after it has been incremented.";  
    this.eventInfos.Add("OnAfterIncrement",  
      "Fires after the initial value is updated.",  
      true,paramNames, paramTypes,paramDescriptions);  
    this.onAfterIncrement = this.eventInfos["OnAfterIncrement"];  
}  
```  
  
```vb  
Public Overrides Sub InitializeTask(ByVal connections As Connections, _  
ByVal variables As VariableDispenser, ByVal events As IDTSInfoEvents, _  
ByVal log As IDTSLogging, ByVal eventInfos As EventInfos, _  
ByVal logEntryInfos As LogEntryInfos, ByVal refTracker As ObjectReferenceTracker)   
  
    Dim paramNames(0) As String  
    Dim paramTypes(0) As TypeCode = {TypeCode.Int32}  
    Dim paramDescriptions(0) As String  
  
    Me.eventInfos = eventInfos  
  
    paramNames(0) = "InitialValue"  
    paramDescriptions(0) = "The value before it is incremented."  
  
    Me.eventInfos.Add("OnBeforeIncrement", _  
      "Fires before the task increments the value.", _  
      True, paramNames, paramTypes, paramDescriptions)  
    Me.onBeforeIncrement = Me.eventInfos("OnBeforeIncrement")  
  
    paramDescriptions(0) = "The value after it has been incremented."  
    Me.eventInfos.Add("OnAfterIncrement", _  
      "Fires after the initial value is updated.", True, _  
      paramNames, paramTypes, paramDescriptions)  
    Me.onAfterIncrement = Me.eventInfos("OnAfterIncrement")  
  
End Sub  
```  
  
## <a name="raising-custom-events"></a>Generazione di eventi personalizzati  
 Gli eventi personalizzati vengono generati con una chiamata al metodo <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A>. La riga di codice seguente genera un evento personalizzato.  
  
```csharp  
componentEvents.FireCustomEvent(this.onBeforeIncrement.Name,  
   this.onBeforeIncrement.Description, ref arguments,  
   null, ref bFireOnBeforeIncrement);  
```  
  
```vb  
componentEvents.FireCustomEvent(Me.onBeforeIncrement.Name, _  
Me.onBeforeIncrement.Description, arguments, _  
Nothing,  bFireOnBeforeIncrement)  
```  
  
## <a name="sample"></a>Esempio  
 Nell'esempio di codice seguente è illustrata un'attività che definisce un evento personalizzato nel metodo`InitializeTask`, aggiunge l'evento personalizzato alla raccolta <xref:Microsoft.SqlServer.Dts.Runtime.EventInfos>, quindi genera l'evento personalizzato durante il relativo metodo `Execute` chiamando il metodo <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireCustomEvent%2A>.  
  
```csharp  
[DtsTask(DisplayName = "CustomEventTask")]  
    public class CustomEventTask : Task  
    {  
        public override DTSExecResult Execute(Connections connections,   
          VariableDispenser variableDispenser, IDTSComponentEvents componentEvents,  
           IDTSLogging log, object transaction)  
        {  
            bool fireAgain;  
            object[] args = new object[1] { "The value of the parameter." };  
            componentEvents.FireCustomEvent( "MyCustomEvent",   
              "Firing the custom event.", ref args,  
              "CustomEventTask" , ref fireAgain );  
            return DTSExecResult.Success;  
        }  
  
        public override void InitializeTask(Connections connections,  
          VariableDispenser variableDispenser, IDTSInfoEvents events,  
          IDTSLogging log, EventInfos eventInfos,  
          LogEntryInfos logEntryInfos, ObjectReferenceTracker refTracker)  
        {  
            string[] names = new string[1] {"Parameter1"};  
            TypeCode[] types = new TypeCode[1] {TypeCode.String};  
            string[] descriptions = new string[1] {"Parameter description." };  
  
            eventInfos.Add("MyCustomEvent",  
             "Fires when my interesting event happens.",  
             true, names, types, descriptions);  
  
        }  
   }  
```  
  
```vb  
<DtsTask(DisplayName = "CustomEventTask")> _   
    Public Class CustomEventTask  
     Inherits Task  
        Public Overrides Function Execute(ByVal connections As Connections, _  
          ByVal variableDispenser As VariableDispenser, _  
          ByVal componentEvents As IDTSComponentEvents, _  
          ByVal log As IDTSLogging, ByVal transaction As Object) _  
          As DTSExecResult  
  
            Dim fireAgain As Boolean  
            Dim args() As Object =  New Object(1) {"The value of the parameter."}  
  
            componentEvents.FireCustomEvent("MyCustomEvent", _  
              "Firing the custom event.", args, _  
              "CustomEventTask" ,  fireAgain)  
            Return DTSExecResult.Success  
        End Function  
  
        Public Overrides  Sub InitializeTask(ByVal connections As Connections, _  
          ByVal variableDispenser As VariableDispenser,  
          ByVal events As IDTSInfoEvents,  
          ByVal log As IDTSLogging, ByVal eventInfos As EventInfos, ByVal logEnTryInfos As LogEnTryInfos, ByVal refTracker As ObjectReferenceTracker)  
  
            Dim names() As String =  New String(1) {"Parameter1"}  
            Dim types() As TypeCode =  New TypeCode(1) {TypeCode.String}  
            Dim descriptions() As String =  New String(1) {"Parameter description."}  
  
            eventInfos.Add("MyCustomEvent", _  
              "Fires when my interesting event happens.", _  
              True, names, types, descriptions)  
  
        End Sub  
  
    End Class  
```  
  
![Integration Services icona (piccola)](../../media/dts-16.gif "Icona di Integration Services (piccola)")  **rimane aggiornata con Integration Services**<br /> Per i download, gli articoli, gli esempi e i video Microsoft più recenti, oltre alle soluzioni selezionate dalla community, visitare la pagina [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sul sito MSDN:<br /><br /> [Visitare la pagina relativa a Integration Services su MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Per ricevere una notifica automatica su questi aggiornamenti, sottoscrivere i feed RSS disponibili nella pagina.  
  
## <a name="see-also"></a>Vedi anche  
 [Integration Services &#40;i gestori eventi&#41; SSIS](../../integration-services-ssis-event-handlers.md)   
 [Aggiunta di un gestore eventi a un pacchetto](../../add-an-event-handler-to-a-package.md)  
  
  
