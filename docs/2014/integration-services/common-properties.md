---
title: Proprietà comuni | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- external metadata column properties [Integration Services]
- output properties [Integration Services]
- data types [Integration Services], properties
- input properties [Integration Services]
- component properties [Integration Services]
ms.assetid: 51973502-5cc6-4125-9fce-e60fa1b7b796
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 06b9c8378d08f8eb1e27df8b545acc12ceaa7e2b
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "85435098"
---
# <a name="common-properties"></a>Proprietà comuni
  Gli oggetti flusso di dati nel [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] modello a oggetti hanno proprietà comuni e proprietà personalizzate a livello di componente, input e output e colonna di input e colonna di output. Molte proprietà hanno valori di sola lettura assegnati in fase di esecuzione dal motore del flusso di dati.  
  
 In questo argomento vengono elencate e descritte le proprietà comuni degli oggetti del flusso di dati.  
  
-   [Componenti](#components)  
  
-   [Input](#inputs)  
  
-   [Colonne di input](#inputcolumns)  
  
-   [Output](#outputs)  
  
-   [Colonne di output](#outputcolumns)  
  
 Per informazioni sulle proprietà dei clienti, vedere gli argomenti seguenti:  
  
-   [Proprietà personalizzate ADO NET](data-flow/ado-net-custom-properties.md)  
  
-   [Proprietà personalizzate dell'attività di controllo CDC](control-flow/cdc-control-task-custom-properties.md)  
  
-   [Proprietà personalizzate dell'origine CDC](data-flow/cdc-source-custom-properties.md)  
  
-   [Proprietà personalizzate della destinazione Training modello di data mining](data-flow/data-mining-model-training-destination-custom-properties.md)  
  
-   [Proprietà personalizzate della destinazione DataReader](data-flow/datareader-destination-custom-properties.md)  
  
-   [Proprietà personalizzate della destinazione elaborazione dimensione](data-flow/dimension-processing-destination-custom-properies.md)  
  
-   [Proprietà personalizzate di Excel](data-flow/excel-custom-properties.md)  
  
-   [Proprietà personalizzate del file flat](data-flow/flat-file-custom-properties.md)  
  
-   [Proprietà personalizzate della destinazione ODBC](data-flow/odbc-destination-custom-properties.md)  
  
-   [Proprietà personalizzate dell'origine ODBC](data-flow/odbc-source-custom-properties.md)  
  
-   [Proprietà personalizzate OLE DB](data-flow/ole-db-custom-properties.md)Proprietà personalizzate OLE DB  
  
-   [Proprietà personalizzate della destinazione elaborazione partizione](data-flow/partition-processing-destination-custom-properties.md)  
  
-   [Proprietà personalizzate del file non elaborato](data-flow/raw-file-custom-properties.md)  
  
-   [Proprietà personalizzate della destinazione recordset](data-flow/recordset-destination-custom-properties.md)  
  
-   [Proprietà personalizzate della destinazione SQL Server Compact Edition](data-flow/sql-server-compact-edition-destination-custom-properties.md)  
  
-   [Proprietà personalizzate della destinazione SQL Server](data-flow/sql-server-destination-custom-properties.md)  
  
-   [proprietà personalizzate della trasformazione](data-flow/transformations/transformation-custom-properties.md)  
  
-   [Proprietà personalizzate dell'origine XML](data-flow/xml-source-custom-properties.md)  
  
##  <a name="component-properties"></a><a name="components"></a>Proprietà del componente  
 Nel modello a oggetti [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] un componente nel flusso di dati implementa l'interfaccia <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>.  
  
 Nella tabella seguente vengono descritte le proprietà dei componenti in un flusso di dati. Alcune proprietà hanno valori di sola lettura assegnati in fase di esecuzione dal motore del flusso di dati.  
  
|Proprietà|Tipo di dati|Descrizione|  
|--------------|---------------|-----------------|  
|ComponentClassID|string|Valore CLSID del componente.|  
|ContactInfo|string|Informazioni di contatto dello sviluppatore di un componente.|  
|Descrizione|string|Descrizione del componente flusso di dati. Il valore predefinito di questa proprietà è il nome del componente flusso di dati.|  
|ID|Integer|Valore che identifica in modo univoco questa istanza del componente.|  
|IdentificationString|string|Identifica il componente.|  
|IsDefaultLocale|Boolean|Indica se il componente utilizza le impostazioni locali dell'attività Flusso di dati alla quale appartiene.|  
|LocaleID|Integer|Impostazioni locali che il componente flusso di dati utilizza durante l'esecuzione del pacchetto. Tutte le impostazioni locali di Windows sono disponibili per l'utilizzo nei componenti flusso di dati.|  
|Nome|string|Nome del componente del flusso di dati.|  
|PipelineVersion|Integer|Versione dell'attività Flusso di dati nella quale il componente è progettato per l'esecuzione.|  
|UsesDispositions|Boolean|Indica se un componente ha un output degli errori.|  
|ValidateExternalMetadata|Boolean|Indica se i metadati delle colonne esterne sono convalidati. Il valore predefinito di questa proprietà è `True`.|  
|Versione|Integer|Versione di un componente.|  
  
##  <a name="input-properties"></a><a name="inputs"></a>Proprietà di input  
 Nel modello a oggetti [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , le trasformazioni e le destinazioni includono input. L'input di un componente nel flusso di dati implementa l'interfaccia <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100>.  
  
 Nella tabella seguente vengono descritte le proprietà degli input dei componenti in un flusso di dati. Alcune proprietà hanno valori di sola lettura assegnati in fase di esecuzione dal motore del flusso di dati.  
  
|Proprietà|Tipo di dati|Descrizione|  
|--------------|---------------|-----------------|  
|Descrizione|string|Descrizione dell'input.|  
|ErrorOrTruncationOperation|string|Stringa facoltativa che specifica i tipi di errori o troncamenti che possono verificarsi durante l'elaborazione di una riga.|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Valore che specifica la gestione degli errori. I possibili valori sono `Fail component`, `Ignore failure` e `Redirect row`.|  
|HasSideEffects|Boolean|Indica se un componente può essere rimosso dal piano di esecuzione del flusso di dati quando non è collegato a un componente downstream e quando `RunInOptimizedMode` è `true` .|  
|ID|Integer|Valore che identifica l'input in modo univoco.|  
|IdentificationString|string|Stringa che identifica l'input.|  
|IsSorted|Boolean|Indica se i dati nell'input sono ordinati.|  
|Nome|string|Nome dell'input.|  
|SourceLocale|Integer|ID delle impostazioni locali (LCID) dei dati di input.|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Valore che determina la gestione dei troncamenti da parte del componente durante l'elaborazione delle righe. . I possibili valori sono `Fail component`, `Ignore failure` e `Redirect row`.|  
  
 Le destinazioni e alcune trasformazioni non supportano gli output degli errori e le proprietà ErrorRowDisposition e TruncationRowDisposition di questi componenti sono di sola lettura.  
  
###  <a name="input-column-properties"></a><a name="inputcolumns"></a>Proprietà delle colonne di input  
 Nel modello a oggetti [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , un input contiene una raccolta di colonne di input. Una colonna di input di un componente nel flusso di dati implementa l'interfaccia <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInputColumn100>.  
  
 Nella tabella seguente vengono descritte le proprietà delle colonne di input dei componenti in un flusso di dati. Alcune proprietà hanno valori di sola lettura assegnati in fase di esecuzione dal motore del flusso di dati.  
  
|Proprietà|Tipo di dati|Descrizione|  
|--------------|---------------|-----------------|  
|ComparisonFlags|Integer|Set di flag che specificano il confronto di colonne che hanno un tipo di dati character. Per altre informazioni, vedere [Comparing String Data](data-flow/comparing-string-data.md).|  
|Descrizione|string|Descrive la colonna di input.|  
|ErrorOrTruncationOperation|string|Stringa facoltativa che specifica i tipi di errori o troncamenti che possono verificarsi durante l'elaborazione di una riga.|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Valore che specifica la gestione degli errori. I possibili valori sono `Fail component`, `Ignore failure` e `Redirect row`.|  
|ExternalMetadataColumnID|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumn100>|ID della colonna di metadati esterna assegnato a una colonna di input.|  
|ID|Integer|Valore che identifica la colonna di input in modo univoco.|  
|IdentificationString|string|Stringa che identifica la colonna di input.|  
|LineageID|Integer|ID della colonna a monte.|  
|Nome|string|Nome della colonna di input.|  
|SortKeyPosition|Integer|Valore che indica se una colonna è ordinata, l'ordinamento e la sequenza di ordinamento di più colonne. Il valore **0** indica che la colonna non è ordinata.  Per altre informazioni, vedere [Ordinamento dei dati per le trasformazioni Unione e Merge Join](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Valore che determina la gestione dei troncamenti da parte del componente durante l'elaborazione delle righe. I possibili valori sono `Fail component`, `Ignore failure` e `Redirect row`.|  
|UpstreamComponentName|string|Nome del componente a monte.|  
|UsageType|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSUsageType>|Valore che determina come una colonna di input viene utilizzata dal componente.|  
  
 Le colonne di input includono anche le proprietà del tipo di dati descritte in "Proprietà del tipo di dati".  
  
##  <a name="output-properties"></a><a name="outputs"></a>Proprietà di output  
 Nel modello a oggetti [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , le origini e le trasformazioni includono output. L'output di un componente nel flusso di dati implementa l'interfaccia <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100>.  
  
 Nella tabella seguente vengono descritte le proprietà degli output dei componenti in un flusso di dati. Alcune proprietà hanno valori di sola lettura assegnati in fase di esecuzione dal motore del flusso di dati.  
  
|Proprietà|Tipo di dati|Descrizione|  
|--------------|---------------|-----------------|  
|DeleteOutputOnPathDetached|Boolean|Valore che determina se il motore del flusso di dati elimina l'output quando viene scollegato da un percorso.|  
|Descrizione|string|Descrive l'output.|  
|ErrorOrTruncationOperation|string|Stringa facoltativa che specifica i tipi di errori o troncamenti che possono verificarsi durante l'elaborazione di una riga.|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Valore che specifica la gestione degli errori. I possibili valori sono `Fail component`, `Ignore failure` e `Redirect row`.|  
|ExclusionGroup|Integer|Valore che identifica un gruppo di output che si escludono a vicenda.|  
|HasSideEffects|Boolean|Valore che indica se un componente può essere rimosso dal piano di esecuzione del flusso di dati se non è collegato a un componente a monte e se la proprietà `RunInOptimizedMode` è impostata su `true`.|  
|ID|Integer|Valore che identifica l'output in modo univoco.|  
|IdentificationString|string|Stringa che identifica l'output.|  
|IsErrorOut|Boolean|Indica se l'output è un output degli errori.|  
|IsSorted|Boolean|Indica se l'output è ordinato. Il valore predefinito è `False`.<br /><br /> Importante l'impostazione del valore della proprietà su **non \* \* consente di ordinare i dati. \* \* ** `IsSorted` `True` Questa proprietà fornisce solo un hint ai componenti a valle in relazione all'ordinamento precedente dei dati. Per altre informazioni, vedere [Ordinamento dei dati per le trasformazioni Unione e Merge Join](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).|  
|Nome|string|Nome dell'output.|  
|SynchronousInputID|Integer|ID di un input sincrono all'output.|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Valore che determina la gestione dei troncamenti da parte del componente durante l'elaborazione delle righe. I possibili valori sono `Fail component`, `Ignore failure` e `Redirect row`.|  
  
###  <a name="output-column-properties"></a><a name="outputcolumns"></a>Proprietà della colonna di output  
 Nel modello a oggetti [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , un output contiene una raccolta di colonne di output. Una colonna di output di un componente nel flusso di dati implementa l'interfaccia <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100>.  
  
 Nella tabella seguente vengono descritte le proprietà delle colonne di output dei componenti in un flusso di dati. Alcune proprietà hanno valori di sola lettura assegnati in fase di esecuzione dal motore del flusso di dati.  
  
|Proprietà|Tipo di dati|Descrizione|  
|--------------|---------------|-----------------|  
|ComparisonFlags|Integer|Set di flag che specificano il confronto di colonne che hanno un tipo di dati character. Per altre informazioni, vedere [Comparing String Data](data-flow/comparing-string-data.md).|  
|Descrizione|string|Descrive la colonna di output.|  
|ErrorOrTruncationOperation|string|Stringa facoltativa che specifica i tipi di errori o troncamenti che possono verificarsi durante l'elaborazione di una riga.|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Valore che specifica la gestione degli errori. I possibili valori sono `Fail component`, `Ignore failure` e `Redirect row`. Il valore predefinito è `Fail component`.|  
|ExternalMetadataColumnID|Integer|ID della colonna di metadati esterna assegnato a una colonna di input.|  
|ID|Integer|Valore che identifica la colonna di output in modo univoco.|  
|IdentificationString|string|Stringa che identifica la colonna di output.|  
|LineageID|Integer|ID della colonna di output. I componenti a valle fanno riferimento alla colonna utilizzando questo valore.|  
|Nome|string|Nome della colonna di output.|  
|SortKeyPosition|Integer|Valore che indica se una colonna è ordinata, l'ordinamento e la sequenza di ordinamento di più colonne. Il valore **0** indica che la colonna non è ordinata. Per altre informazioni, vedere [Ordinamento dei dati per le trasformazioni Unione e Merge Join](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).|  
|SpecialFlags|Integer|Valore che contiene i flag speciali della colonna di output.|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|Valore che determina la gestione dei troncamenti da parte del componente durante l'elaborazione delle righe. I possibili valori sono `Fail component`, `Ignore failure` e `Redirect row`. Il valore predefinito è `Fail component`.|  
  
 Le colonne di output includono anche un set di proprietà del tipo di dati.  
  
## <a name="external-metadata-column-properties"></a>Proprietà delle colonne di metadati esterne  
 Nel modello a oggetti [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , input e output possono contenere un insieme di colonne di metadati esterne. Una colonna di metadati esterna di un componente nel flusso di dati implementa l'interfaccia <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumn100>.  
  
 Nella tabella seguente vengono descritte le proprietà delle colonne di metadati esterne dei componenti in un flusso di dati. Alcune proprietà hanno valori di sola lettura assegnati in fase di esecuzione dal motore del flusso di dati.  
  
|Proprietà|Tipo di dati|Descrizione|  
|--------------|---------------|-----------------|  
|Descrizione|string|Descrive la colonna esterna.|  
|ID|Integer|Valore che identifica la colonna in modo univoco.|  
|IdentificationString|string|Stringa che identifica la colonna.|  
|Nome|string|Nome della colonna esterna.|  
  
 Le colonne di metadati esterne includono anche un set di proprietà del tipo di dati.  
  
## <a name="data-type-properties"></a>Proprietà del tipo di dati  
 Le colonne di metadati esterne e le colonne di output includono anche un set di proprietà del tipo di dati. A seconda del tipo di dati della colonna, le proprietà possono essere di lettura/scrittura o di sola lettura.  
  
 Nella tabella seguente vengono descritte le proprietà del tipo di dati delle colonne di metadati esterne e delle colonne di output.  
  
|Proprietà|Tipo di dati|Descrizione|  
|--------------|---------------|-----------------|  
|CodePage|Integer|Specifica la tabella codici per i dati stringa non Unicode.|  
|DataType|Integer (enumerazione)|Tipo di dati [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] della colonna. Per ulteriori informazioni, vedere [Integration Services tipi di dati](data-flow/integration-services-data-types.md).|  
|Length|Integer|Lunghezza della colonna in caratteri.|  
|Precision|Integer|Precisione di una colonna numerica.|  
|Scalabilità|Integer|Scala di una colonna numerica.|  
  
## <a name="see-also"></a>Vedere anche  
 [Flusso di dati](data-flow/data-flow.md)   
 [Proprietà personalizzate della trasformazione](data-flow/transformations/transformation-custom-properties.md)   
 [Proprietà percorso](../../2014/integration-services/path-properties.md)   
 [Proprietà del flusso di dati che è possibile impostare tramite espressioni](../../2014/integration-services/data-flow-properties-that-can-be-set-by-using-expressions.md)  
  
  
