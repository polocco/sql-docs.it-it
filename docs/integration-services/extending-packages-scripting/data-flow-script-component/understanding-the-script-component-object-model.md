---
description: Informazioni sul modello a oggetti del componente script
title: Informazioni sul modello a oggetti del componente script | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], object model
ms.assetid: 2a0aae82-39cc-4423-b09a-72d2f61033bd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bc5034010508f0a24f703962e4b78b7c9376ee9f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88425343"
---
# <a name="understanding-the-script-component-object-model"></a>Informazioni sul modello a oggetti del componente script

[!INCLUDE[sqlserver-ssis](../../../includes/applies-to-version/sqlserver-ssis.md)]


  Come illustrato in [Codifica e debug del componente script](../../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md), il progetto del componente script contiene tre elementi:  
  
1.  L'elemento **ScriptMain** che contiene la classe **ScriptMain** in cui viene scritto il codice. La classe **ScriptMain** eredita dalla classe **UserComponent**.  
  
2.  L'elemento **ComponentWrapper**, che contiene la classe **UserComponent**, un'istanza di <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> che contiene i metodi e le proprietà da usare per elaborare i dati e interagire con il pacchetto. L'elemento **ComponentWrapper** contiene anche le classi delle raccolte **Connections** e **Variables**.  
  
3.  L'elemento **BufferWrapper**, che contiene le classi che ereditano da <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> per ogni input e output, nonché le proprietà tipizzate per ogni colonna.  
  
 Quando si scrive il codice nell'elemento **ScriptMain** si useranno gli oggetti, i metodi e le proprietà illustrati in questo argomento. Ogni componente non utilizzerà tutti i metodi elencati, ma se li utilizza la sequenza sarà quella illustrata.  
  
 La classe di base <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> non contiene codice di implementazione per i metodi descritti in questo argomento. Pertanto, non è necessario aggiungere una chiamata all'implementazione della classe di base nell'implementazione del metodo, anche se questa operazione non genera errori.  
  
 Per informazioni su come usare i metodi e le proprietà di queste classi in un tipo di componente script specifico, vedere la sezione [Ulteriori esempi di componente script](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md). Negli argomenti di esempio vengono inoltre presentati esempi di codice completi.  
  
## <a name="acquireconnections-method"></a>Metodo AcquireConnections  
 Le origini e le destinazioni devono in genere connettersi a un'origine dati esterna. Eseguire l'override del metodo <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A> della classe di base <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> per recuperare la connessione o le informazioni di connessione dalla gestione connessione appropriata.  
  
 Nell'esempio seguente viene restituito **System.Data.SqlClient.SqlConnection** da una gestione connessione ADO.NET.  
  
```vb  
Dim connMgr As IDTSConnectionManager100  
Dim sqlConn As SqlConnection  
  
Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
    connMgr = Me.Connections.MyADONETConnection  
    sqlConn = CType(connMgr.AcquireConnection(Nothing), SqlConnection)  
  
End Sub  
```  
  
 Nell'esempio seguente vengono restituiti un percorso completo e un nome file da una gestione connessione file flat, quindi il file viene aperto usando **System.IO.StreamReader**.  
  
```vb  
Private textReader As StreamReader  
Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
    Dim connMgr As IDTSConnectionManager100 = _  
        Me.Connections.MyFlatFileSrcConnectionManager  
    Dim exportedAddressFile As String = _  
        CType(connMgr.AcquireConnection(Nothing), String)  
    textReader = New StreamReader(exportedAddressFile)  
  
End Sub  
```  
  
## <a name="preexecute-method"></a>Metodo PreExecute  
 Eseguire l'override del metodo <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PreExecute%2A> della classe di base <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> quando è necessario eseguire un'elaborazione una volta solo prima di avviare l'elaborazione delle righe di dati. In una destinazione, ad esempio, è possibile configurare il comando con parametri che verrà utilizzato dalla destinazione stessa per inserire ogni riga di dati nell'origine dati.  
  
```vb  
    Dim sqlConn As SqlConnection  
    Dim sqlCmd As SqlCommand  
    Dim sqlParam As SqlParameter  
...  
    Public Overrides Sub PreExecute()  
  
        sqlCmd = New SqlCommand("INSERT INTO Person.Address2(AddressID, City) " & _  
            "VALUES(@addressid, @city)", sqlConn)  
        sqlParam = New SqlParameter("@addressid", SqlDbType.Int)  
        sqlCmd.Parameters.Add(sqlParam)  
        sqlParam = New SqlParameter("@city", SqlDbType.NVarChar, 30)  
        sqlCmd.Parameters.Add(sqlParam)  
  
    End Sub  
```  
  
```csharp  
SqlConnection sqlConn;   
SqlCommand sqlCmd;   
SqlParameter sqlParam;   
  
public override void PreExecute()   
{   
  
    sqlCmd = new SqlCommand("INSERT INTO Person.Address2(AddressID, City) " + "VALUES(@addressid, @city)", sqlConn);   
    sqlParam = new SqlParameter("@addressid", SqlDbType.Int);   
    sqlCmd.Parameters.Add(sqlParam);   
    sqlParam = new SqlParameter("@city", SqlDbType.NVarChar, 30);   
    sqlCmd.Parameters.Add(sqlParam);   
  
}  
```  
  
## <a name="processing-inputs-and-outputs"></a>Elaborazione di input e output  
  
### <a name="processing-inputs"></a>Elaborazione di input  
 I componenti script configurati come trasformazioni o destinazioni prevedono un unico input.  
  
#### <a name="what-the-bufferwrapper-project-item-provides"></a>Contenuto dell'elemento di progetto BufferWrapper  
 Per ogni input configurato, l'elemento di progetto **BufferWrapper** contiene una classe che deriva da <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> e ha lo stesso nome dell'input. Ogni classe del buffer di input contiene le proprietà, le funzioni e i metodi seguenti:  
  
-   Proprietà delle funzioni di accesso denominate e tipizzate per ogni colonna di input selezionata. Queste proprietà sono di sola lettura o di lettura/scrittura a seconda del **Tipo di utilizzo** specificato per la colonna nella pagina **Colonne di input** di **Editor trasformazione Script**.  
  
-   Una proprietà **\<column>_IsNull** per ogni colonna di input selezionata. Anche questa proprietà è di sola lettura o di lettura/scrittura a seconda del **Tipo di utilizzo** specificato per la colonna.  
  
-   Metodo **DirectRowTo\<outputbuffer>** per ogni output configurato. Questi metodi verranno usati per filtrare le righe in uno dei diversi output dello stesso elemento **ExclusionGroup**.  
  
-   Una funzione **NextRow** per ottenere la riga di input successiva e una funzione **EndOfRowset** per determinare se è stato elaborato l'ultimo buffer di dati. Queste funzioni non sono in genere necessarie quando si usano i metodi di elaborazione dell'input implementati nella classe di base **UserComponent**. La sezione seguente contiene altre informazioni sulla classe di base **UserComponent**.  
  
#### <a name="what-the-componentwrapper-project-item-provides"></a>Contenuto dell'elemento di progetto ComponentWrapper  
 L'elemento di progetto ComponentWrapper contiene una classe denominata **UserComponent** che deriva da <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>. La classe **ScriptMain** in cui si scrive il codice personalizzato deriva a sua volta da **UserComponent**. La classe **UserComponent** contiene i metodi seguenti:  
  
-   Un'implementazione sottoposta a override del metodo **ProcessInput**. Si tratta del metodo chiamato in fase di esecuzione dal motore flusso di dati dopo il metodo **PreExecute** e può essere chiamato più volte. **ProcessInput** passa l'elaborazione al metodo **\<inputbuffer>_ProcessInput**. Il metodo **ProcessInput** verifica quindi se è stata raggiunta la fine del buffer di input e, in caso affermativo, chiama il metodo **FinishOutputs** sottoponibile a override e il metodo **MarkOutputsAsFinished** privato. Il metodo **MarkOutputsAsFinished** chiama quindi **SetEndOfRowset** sull'ultimo buffer di output.  
  
-   Un'implementazione sovrascrivibile del metodo **\<inputbuffer>_ProcessInput**. Questa implementazione predefinita esegue il ciclo di ogni riga di input e chiama **\<inputbuffer>_ProcessInputRow**.  
  
-   Un'implementazione sovrascrivibile del metodo **\<inputbuffer>_ProcessInputRow**. L'implementazione predefinita è vuota. Si tratta del metodo di cui in genere si esegue l'override per scrivere il codice personalizzato di elaborazione dati.  
  
#### <a name="what-your-custom-code-should-do"></a>Funzione del codice personalizzato  
 Per elaborare l'input nella classe **ScriptMain** è possibile usare i metodi seguenti:  
  
-   Eseguire l'override di **\<inputbuffer>_ProcessInputRow** per elaborare i dati in ogni riga di input non appena vengono passati.  
  
-   Eseguire l'override di **\<inputbuffer>_ProcessInput** solo se è necessario eseguire operazioni aggiuntive mentre si esegue il ciclo delle righe di input, ad esempio se è necessario verificare la presenza di **EndOfRowset** per eseguire un'altra azione dopo l'elaborazione di tutte le righe. Chiamare **\<inputbuffer>_ProcessInputRow** per eseguire l'elaborazione delle righe.  
  
-   Eseguire l'override di **FinishOutputs** se è necessario eseguire operazioni sugli output prima che vengano chiusi.  
  
 Il metodo **ProcessInput** assicura che questi metodi vengano chiamati nel momento appropriato.  
  
### <a name="processing-outputs"></a>Elaborazione degli output  
 I componenti script configurati come origini o trasformazioni includono uno o più output.  
  
#### <a name="what-the-bufferwrapper-project-item-provides"></a>Contenuto dell'elemento di progetto BufferWrapper  
 Per ogni output configurato, l'elemento di progetto BufferWrapper contiene una classe che deriva da <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> e ha lo stesso nome dell'output. Ogni classe del buffer di input contiene le proprietà e i metodi seguenti:  
  
-   Proprietà delle funzioni di accesso di sola scrittura, denominate e tipizzate per ogni colonna di output.  
  
-   Una proprietà **\<column>_IsNull** di sola scrittura per ogni colonna di output selezionata che è possibile usare per impostare il valore della colonna su **Null**.  
  
-   Un metodo **AddRow** per aggiungere una nuova riga vuota nel buffer di output.  
  
-   Un metodo **SetEndOfRowset** per indicare al motore flusso di dati che non sono previsti altri buffer di dati. È inoltre disponibile una funzione **EndOfRowset** per determinare se il buffer corrente è l'ultimo buffer di dati. Queste funzioni non sono in genere necessarie quando si usano i metodi di elaborazione dell'input implementati nella classe di base **UserComponent**.  
  
#### <a name="what-the-componentwrapper-project-item-provides"></a>Contenuto dell'elemento di progetto ComponentWrapper  
 L'elemento di progetto ComponentWrapper contiene una classe denominata **UserComponent** che deriva da <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>. La classe **ScriptMain** in cui si scrive il codice personalizzato deriva a sua volta da **UserComponent**. La classe **UserComponent** contiene i metodi seguenti:  
  
-   Un'implementazione sottoposta a override del metodo **PrimeOutput**. Il motore flusso di dati chiama questo metodo prima di **ProcessInput** in fase di esecuzione e viene chiamato solo una volta. **PrimeOutput** passa l'elaborazione al metodo **CreateNewOutputRows**. Quindi, se il componente è un'origine, ovvero non include input, **PrimeOutput** chiama il metodo **FinishOutputs** sottoponibile a override e il metodo **MarkOutputsAsFinished** privato. Il metodo **MarkOutputsAsFinished** chiama **SetEndOfRowset** sull'ultimo buffer di output.  
  
-   Un'implementazione sottoponibile a override del metodo **CreateNewOutputRows**. L'implementazione predefinita è vuota. Si tratta del metodo di cui in genere si esegue l'override per scrivere il codice personalizzato di elaborazione dati.  
  
#### <a name="what-your-custom-code-should-do"></a>Funzione del codice personalizzato  
 Per elaborare gli output nella classe **ScriptMain** è possibile usare i metodi seguenti:  
  
-   Eseguire l'override di **CreateNewOutputRows** solo quando è possibile aggiungere e popolare le righe di output prima dell'elaborazione delle righe di input. Ad esempio, è possibile usare **CreateNewOutputRows** in un'origine, ma in una trasformazione con output asincroni è necessario chiamare **AddRow** durante o dopo l'elaborazione dei dati di input.  
  
-   Eseguire l'override di **FinishOutputs** se è necessario eseguire operazioni sugli output prima che vengano chiusi.  
  
 Il metodo **PrimeOutput** assicura che questi metodi vengano chiamati nel momento appropriato.  
  
## <a name="postexecute-method"></a>Metodo PostExecute  
 Eseguire l'override del metodo <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.PostExecute%2A> della classe di base <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> quando è necessario eseguire un'elaborazione un'unica volta solo dopo aver elaborato le righe di dati. In un'origine, ad esempio, può essere opportuno chiudere l'oggetto **System.Data.SqlClient.SqlDataReader** usato per caricare i dati nel flusso di dati.  
  
> [!IMPORTANT]  
>  La raccolta di **ReadWriteVariables** è disponibile solo nel metodo **PostExecute**. Pertanto, non è possibile incrementare direttamente il valore di una variabile del pacchetto durante l'elaborazione di ogni riga di dati. Incrementare invece il valore di una variabile locale e impostare il valore della variabile del pacchetto sul valore della variabile locale nel metodo **PostExecute** dopo che tutti i dati sono stati elaborati.  
  
## <a name="releaseconnections-method"></a>Metodo ReleaseConnections  
 Le origini e le destinazioni devono in genere connettersi a un'origine dati esterna. Eseguire l'override del metodo <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ReleaseConnections%2A> della classe di base <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> per chiudere e rilasciare la connessione aperta in precedenza nel metodo <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.AcquireConnections%2A>.  
  
```vb  
    Dim connMgr As IDTSConnectionManager100  
...  
    Public Overrides Sub ReleaseConnections()  
  
        connMgr.ReleaseConnection(sqlConn)  
  
    End Sub  
```  
  
```csharp  
IDTSConnectionManager100 connMgr;  
  
public override void ReleaseConnections()  
{  
  
    connMgr.ReleaseConnection(sqlConn);  
  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione del componente script nell'editor corrispondente](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)   
 [Codifica e debug del componente script](../../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
  
  
