---
title: Guida sensibile al contesto di Proprietà indice | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.indexproperties.storage.f1
- sql12.swb.indexproperties.columns.f1
- sql12.swb.indexproperties.partitions.f1
- sql12.swb.indexproperties.general.f1
- sql12.swb.indexproperties.filter.f1
- sql12.swb.indexproperties.options.f1
- sql12.swb.indexproperties.spatial.f1
ms.assetid: 45efd81a-3796-4b04-b0cc-f3deec94c733
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d97fecf49f9d74e2a74444c12dfdf598fb1da469
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "63161892"
---
# <a name="index-properties-f1-help"></a>Guida sensibile al contesto di Proprietà indice
  Le sezioni in questo argomento fanno riferimento a varie proprietà di indice disponibili tramite le finestre di dialogo di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
 **Contenuto dell'argomento:**  
  
 [Pagina Generale di Proprietà indice](#General)  
  
 [Finestra di dialogo Seleziona colonne (Indice)](#Columns)  
  
 [Pagina Archiviazione di Proprietà indice](#Storage)  
  
 [Pagina Spaziale di Proprietà indice](#Spatial)  
  
 [Pagina Filtro di Proprietà indice](#Filter)  
  
##  <a name="index-properties-general-page"></a><a name="General"></a> Pagina Generale di Proprietà indice  
 Usare la pagina Generale per visualizzare o modificare le proprietà di indice per la tabella o la vista selezionata. Le opzioni per ogni pagina possono cambiare a seconda del tipo di indice selezionato.  
  
 **Nome tabella**  
 Visualizza il nome della tabella o della vista in cui l'indice è stato creato. Questo campo è di sola lettura. Per selezionare una tabella diversa chiudere la pagina Proprietà indice, selezionare la tabella corretta e quindi riaprire la pagina Proprietà indice.  
  
 Non è possibile specificare indici spaziali in viste indicizzate. È possibile definire indici spaziali solo per una tabella con chiave primaria. Il numero massimo di colonne chiave primaria in una tabella è pari a 15. La dimensione combinata per riga delle colonne chiave primaria non può essere superiore a 895 byte.  
  
 **Nome indice**  
 Consente di visualizzare il nome dell'indice. Per un indice esistente questo campo è di sola lettura. Quando si crea un nuovo indice, digitare il nome dell'indice.  
  
 **Tipo di indice**  
 Indica il tipo di indice. Per i nuovi indici, indica il tipo di indice selezionato all'apertura della finestra di dialogo. Gli indici possono essere: **Cluster**, **Non cluster**, **AML primario**, **XML secondario**, **Spaziale**, **Columnstore cluster**o **Columnstore non cluster**.  
  
 **Nota** È consentito un solo indice cluster per ogni tabella. È consentito un solo indice columnstore con ottimizzazione per la memoria xVelocity per ogni tabella.  
  
 **Univoco**  
 Selezionando questa casella di controllo, si rende l'indice univoco. Due righe non potranno avere lo stesso valore di indice. Per impostazione predefinita, tale casella di controllo è deselezionata. Se due righe hanno lo stesso valore durante la modifica di un indice esistente, la creazione dell'indice avrà esito negativo. Per le colonne in cui sono consentiti valori Null, un indice univoco consente un solo valore Null.  
  
 Se nel campo **Tipo di indice** si seleziona **Spaziale** , la casella di controllo **Univoco** è visualizzata in grigio.  
  
 **Colonne chiave indice**  
 Consente di aggiungere le colonne desiderate alla griglia **Colonne chiave indice** . Quando viene aggiunta più di una colonna, le colonne devono essere elencate nell'ordine desiderato. L'ordine delle colonne in un indice può influenzare notevolmente le prestazioni dell'indice.  
  
 Non è possibile includere più di 16 colonne in un solo indice composto. Per un numero di colonne maggiore di 16, vedere la sezione dedicata a included_columns alla fine di questo argomento.  
  
 È possibile definire un indice spaziale solo in una colonna che contiene un tipo di dati spaziali ( *colonna spaziale*).  
  
 **Nome**  
 Consente di visualizzare il nome della colonna che partecipa alla chiave dell'indice.  
  
 **Ordinamento**  
 Consente di specificare la direzione di ordinamento, **Crescente** o **Decrescente**, della colonna dell'indice selezionata.  
  
> [!NOTE]  
>  Se il tipo di indice è **XML primario** o **Spaziale**, questa colonna non viene visualizzata nella tabella.  
  
 **Tipo di dati**  
 Consente di visualizzare informazioni sul tipo di dati.  
  
> [!NOTE]  
>  Se la colonna della tabella è una colonna calcolata, l'opzione **Tipo di dati** visualizza "colonna calcolata".  
  
 **Dimensione**  
 Consente di visualizzare il numero massimo di byte necessari per archiviare il tipo di dati della colonna. In caso di colonna spaziale o XML, il valore visualizzato è zero (0).  
  
 **Identità**  
 Indica se la colonna che partecipa alla chiave dell'indice è una colonna Identity.  
  
 **Consenti valori Null**  
 Indica se la colonna che partecipa alla chiave dell'indice consente l'archiviazione di valori Null nella colonna della tabella o della vista.  
  
 **Aggiungere**  
 Consente di aggiungere una colonna alla chiave dell'indice. Selezionare le colonne della tabella nella finestra di dialogo **Seleziona colonne da** *\<nome tabella>* che viene visualizzata quando si fa clic su **Aggiungi**. In caso di indice spaziale, questo pulsante viene visualizzato in grigio dopo la selezione di una colonna.  
  
 **Rimuovi**  
 Consente di rimuovere la colonna selezionata dalla partecipazione alla chiave dell'indice.  
  
 **Sposta su**  
 Consente di spostare verso l'alto la colonna selezionata nella griglia della chiave dell'indice.  
  
 **Sposta giù**  
 Consente di spostare verso il basso la colonna selezionata nella griglia della chiave dell'indice.  
  
 **Colonne columnstore**  
 Fare clic su **Aggiungi** per selezionare le colonne per l'indice columnstore. Per le limitazioni in un indice columnstore, vedere [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql).  
  
 **included_columns**  
 Consente di includere colonne non chiave nell'indice non cluster. Questa opzione consente di ignorare i limiti dell'indice corrente relativi alle dimensioni totali di una chiave di indice e il numero massimo di colonne che fanno parte di una chiave di indice aggiungendo colonne come colonne non chiave nel livello foglia dell'indice non cluster. Per altre informazioni, vedere [Creare indici con colonne incluse](create-indexes-with-included-columns.md).  
  
##  <a name="select-index-columns-dialog-box"></a><a name="Columns"></a> Finestra di dialogo Seleziona colonne (Indice)  
 Usare questa pagina per aggiungere colonne alla pagina Generale di **Proprietà indice** durante la creazione o la modifica di un indice.  
  
 **Casella di controllo**  
 È possibile selezionare le caselle di controllo per aggiungere le colonne desiderate.  
  
 **Nome**  
 Nome della colonna.  
  
 **Tipo di dati**  
 Tipo di dati della colonna.  
  
 **Byte**  
 Dimensioni in byte della colonna.  
  
 **Identità**  
 Il valore indicato è **Sì** per le colonne Identity oppure **No** se la colonna non è di tipo Identity.  
  
 **Consenti valori NULL**  
 Il valore indicato è **Sì** se la definizione della tabella consente valori Null per la colonna. oppure **No** se la definizione della tabella non consente valori Null per la colonna.  
  
##  <a name="storage-page-options"></a><a name="Storage"></a>Opzioni della pagina di archiviazione  
 Usare questa pagina per visualizzare o modificare proprietà di filegroup o di schemi di partizione per l'indice selezionato. Vengono mostrate solo le opzioni correlate al tipo di indice.  
  
 **Filegroup**  
 Archivia l'indice nel filegroup specificato. Nell'elenco sono visualizzati solo filegroup standard (ROW). La selezione predefinita nell'elenco è il filegroup PRIMARY del database. Per altre informazioni, vedere [Database Files and Filegroups](../databases/database-files-and-filegroups.md).  
  
 **Filegroup FILESTREAM**  
 Specifica il filegroup per i dati FILESTREAM. Questo elenco visualizza solo i filegroup FILESTREAM. La selezione predefinita nell'elenco è il filegroup PRIMARY FILESTREAM del database. Per altre informazioni, vedere [FILESTREAM &#40;SQL Server&#41;](../blob/filestream-sql-server.md).  
  
 **Schema di partizione**  
 Archivia l'indice in uno schema di partizione. Facendo clic su **Schema partizione** si abilita la griglia sottostante. La selezione predefinita nell'elenco è lo schema di partizione usato per archiviare i dati di tabella. Selezionando uno schema di partizione diverso nell'elenco si aggiornano le informazioni visualizzate nella griglia. Per ulteriori informazioni, vedere [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md).  
  
 L'opzione relativa allo schema di partizione non è disponibile se il database non contiene schemi di partizione.  
  
 **Schema di partizione FILESTREAM**  
 Specifica lo schema di partizione per i dati FILESTREAM. Lo schema di partizione deve essere simmetrico con la combinazione specificata nell'opzione **Schema partizione** .  
  
 Se la tabella non è partizionata, il campo è vuoto.  
  
 **Parametro schema partizione**  
 Consente di visualizzare il nome della colonna che partecipa allo schema di partizione.  
  
 **Colonne della tabella**  
 Consente di selezionare la tabella o la vista su cui eseguire il mapping allo schema di partizione.  
  
 **Tipo di dati column**  
 Consente di visualizzare le informazioni sul tipo di dati relative alla colonna.  
  
> [!NOTE]  
>   Se la colonna della tabella è una colonna calcolata, l'opzione **Tipo di dati colonna** visualizza "colonna calcolata".  
  
 **Consenti elaborazione online di istruzioni DML durante lo spostamento dell'indice**  
 Consente agli utenti di accedere ai dati della tabella o dell'indice cluster sottostanti e a eventuali indici non cluster associati durante l'operazione sull'indice. Per altre informazioni, vedere [Perform Index Operations Online](perform-index-operations-online.md).  
  
> [!NOTE]  
>  Questa opzione non è disponibile per gli indici XML o se l'indice è un indice cluster disabilitato.  
  
 **Imposta massimo grado di parallelismo**  
 Consente di limitare il numero di processori da usare durante l'esecuzione di piani paralleli. Il valore predefinito è 0 e corrisponde al numero effettivo di CPU disponibili. L'impostazione del valore su 1 impedisce la generazione di piani paralleli. L'impostazione del valore su un numero maggiore di 1 limita il numero massimo di processori usati da una singola esecuzione della query. Questa opzione diventa disponibile solo se la finestra di dialogo è nello stato **Ricompila** o **Ricrea** . Per altre informazioni, vedere [Impostazione dell'opzione relativa al massimo grado di parallelismo per ottenere prestazioni ottimali](../policy-based-management/set-the-max-degree-of-parallelism-option-for-optimal-performance.md).  
  
> [!NOTE]  
>  Se viene specificato un valore maggiore del numero di CPU disponibili, verrà usato l'effettivo numero di CPU disponibili.  
  
##  <a name="spatial-page-index-options"></a><a name="Spatial"></a>Opzioni per gli indici di pagine spaziali  
 Usare la pagina **Spaziale** per visualizzare o specificare i valori delle proprietà spaziali. Per altre informazioni, vedere [Dati spaziali &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md).  
  
### <a name="bounding-box"></a>Riquadro  
 Si definisce *riquadro* il perimetro della griglia di livello principale di un piano geometrico. I parametri del riquadro sono presenti solo nello schema a mosaico griglia geometrica. Questi parametri non sono disponibili se **Schema a mosaico** è impostato su **Griglia geografica**.  
  
 Nel pannello vengono visualizzate **le*`X-min`* coordinate*`Y-min`*(,)** e ***`X-max`*(,*`Y-max`*)** del rettangolo di delimitazione. Non esistono valori predefiniti, pertanto, quando si crea un indice spaziale nuovo su una colonna di tipo `geometry`, è necessario specificare i valori delle coordinate.  
  
 `X-min`  
 La coordinata X dell'angolo inferiore sinistro del riquadro.  
  
 `Y-min`  
 La coordinata Y dell'angolo inferiore sinistro del riquadro.  
  
 `X-max`  
 La coordinata X dell'angolo superiore destro del riquadro.  
  
 `Y-max`  
 La coordinata Y dell'angolo superiore destro del riquadro.  
  
### <a name="general"></a>Generale  
 **Schema a mosaico**  
 Indica lo schema a mosaico dell'indice. Sono supportati gli schemi a mosaico seguenti.  
  
 **Griglia geometrica**  
 Specifica lo schema a mosaico per griglia geometrica che viene applicato a una colonna del tipo di dati `geometry`.  
  
 **Griglia geometrica automatica**  
 Questa opzione è abilitata per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] quando il livello di compatibilità del database è impostato su 110 o su un valore maggiore.  
  
 **Griglia geografica**  
 Specifica lo schema a mosaico per griglia geografica che viene applicato a una colonna con il tipo di dati **geography** .  
  
 **Griglia geografica automatica**  
 Questa opzione è abilitata per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] quando il livello di compatibilità del database è impostato su 110 o su un valore maggiore.  
  
 Per informazioni sull'implementazione dello schema a mosaico in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vedere [Dati spaziali &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md).  
  
 **Celle per oggetto**  
 Indica il numero di celle per oggetto di mosaico utilizzabile per un singolo oggetto spaziale nell'indice. È possibile usare qualsiasi numero intero compreso tra 1 e 8192. Quando il livello di compatibilità del database è impostato su 110 o su un valore maggiore, il valore predefinito è 16, mentre è 8 per le versioni precedenti di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
 Se al livello principale un oggetto include più celle rispetto a quanto specificato da *n*, l'indicizzazione usa il numero di celle necessario per offrire uno schema a mosaico di livello principale completo. In tali casi un oggetto può ricevere un numero di celle maggiore di quello specificato: il numero massimo è il numero di celle generate dalla griglia di livello principale che dipende dalla densità di **Livello 1** .  
  
### <a name="grids"></a>Griglie  
 In questo pannello è visualizzata la densità della griglia a ogni livello dello schema a mosaico. Le opzioni disponibili sono **Bassa**, **Media**o **Alta**. Il valore predefinito è **Media**. **Bassa** rappresenta una griglia 4x4 (16 celle), **Media** una griglia 8x8 (64 celle) e **Alta** una griglia 16x16 (256 celle). Queste opzioni non sono disponibili se si scelgono le opzioni di schema a mosaico **Griglia geometrica automatica** o **Griglia geografica automatica** .  
  
 **Livello 1**  
 Densità della griglia di primo livello (principale).  
  
 **Livello 2**  
 Densità della griglia di secondo livello.  
  
 **Livello 3**  
 Densità della griglia di terzo livello.  
  
 **Livello 4**  
 Densità della griglia di quarto livello.  
  
##  <a name="filter-page"></a><a name="Filter"></a>Pagina filtro  
 Usare questa pagina per immettere il predicato del filtro per un indice filtrato. Per altre informazioni, vedere [Create Filtered Indexes](create-filtered-indexes.md).  
  
 **Espressione filtro**  
 Definisce le righe di dati da includere nell'indice filtrato. Ad esempio: `StartDate > '20000101' AND EndDate IS NOT NULL'.`  
  
## <a name="see-also"></a>Vedi anche  
 [Impostare le opzioni per gli indici](set-index-options.md)   
 [INDEXPROPERTY &#40;&#41;Transact-SQL](/sql/t-sql/functions/indexproperty-transact-sql)   
 [sys.indexes &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)  
  
  
