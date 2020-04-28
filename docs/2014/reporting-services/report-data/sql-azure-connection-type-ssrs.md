---
title: Tipo di connessione SQL Azure (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c84def6c-e8cf-43d9-9912-098171a7ce79
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e2c3d3e75117996f088cff96b2b7a8d4cd504127
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "78176901"
---
# <a name="sql-azure-connection-type-ssrs"></a>Tipo di connessione a SQL Azure (SSRS)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] è un database relazionale basato su cloud e ospitato basato sulle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tecnologie. Per includere dati da un'origine dati esterna [!INCLUDE[ssSDS](../../includes/sssds-md.md)] nel report, è necessario disporre di un set di dati basato su un'origine dati del report di tipo [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Questo tipo di origine dati predefinito è basato sull'estensione per i dati di [!INCLUDE[ssSDS](../../includes/sssds-md.md)] . Questo tipo di origine dati può essere utilizzato per connettersi e recuperare dati da [!INCLUDE[ssSDS](../../includes/sssds-md.md)].

 Questa estensione per i dati supporta parametri multivalore, aggregazioni server e credenziali gestiti separatamente dalla stringa di connessione.

 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] è simile a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locale e, a parte alcune eccezioni, l'acquisizione di dati da [!INCLUDE[ssSDS](../../includes/sssds-md.md)] è identica a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

> [!NOTE]
>  Quando si apre una connessione a [!INCLUDE[ssSDS](../../includes/sssds-md.md)], impostare il timeout connessione su 30 secondi.

 Per altre informazioni, vedere la [documentazione del database SQL di Azure](https://docs.microsoft.com/azure/sql-database/).

 Usare le informazioni presenti in questo argomento per compilare un'origine dati. Per istruzioni dettagliate, vedere [aggiungere e verificare una connessione dati o un'origine dati &#40;Generatore report e SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md).

##  <a name="connection-string"></a><a name="Connection"></a>Stringa di connessione
 Quando ci si connette a [!INCLUDE[ssSDS](../../includes/sssds-md.md)], si esegue la connessione a un oggetto di database nel cloud. Proprio come i database in loco, il database di hosting potrebbe disporre di più schemi aventi più tabelle, viste e stored procedure. L'oggetto di database viene specificato in Progettazione query. Se non si specifica un database nella stringa di connessione, la connessione viene eseguita al database predefinito assegnato dall'amministratore.

 Contattare l'amministratore del database per ottenere le informazioni di connessione e le credenziali da utilizzare per connettersi all'origine dati. Nella seguente stringa di connessione di esempio viene specificato un database di hosting di esempio denominato AdventureWorks.

```
Data Source=<host>;Initial Catalog=AdventureWorks; Encrypt=True;
```

 Viene inoltre utilizzata la finestra di dialogo **Proprietà origini dati** per fornire credenziali quale il nome utente e la password. Le opzioni `User Id` e `Password` vengono aggiunte automaticamente alla stringa di connessione; non è necessario digitarle come parte della stringa di connessione.

 Per altre informazioni ed esempi di stringhe di connessione, vedere [Connessioni dati, origini dati e stringhe di connessione in Generatore report](../data-connections-data-sources-and-connection-strings-in-report-builder.md).

##  <a name="credentials"></a><a name="Credentials"></a>Credenziali
 L'autenticazione di Windows (sicurezza integrata) non è supportata. Se si tenta di connettersi a [!INCLUDE[ssSDS](../../includes/sssds-md.md)] utilizzando l'autenticazione di Windows, si verificherà un errore. [!INCLUDE[ssSDS](../../includes/sssds-md.md)] supporta solo l'autenticazione di SQL Server (nome utente e password) e gli utenti devono fornire le proprie credenziali (account di accesso e password) ogni volta che si connettono a [!INCLUDE[ssSDS](../../includes/sssds-md.md)].

 Le credenziali devono essere sufficienti per accedere al database. A seconda della query, potrebbe essere necessario utilizzare altre autorizzazioni, ad esempio le autorizzazioni per eseguire stored procedure e accedere a tabelle e viste. Il proprietario dell'origine dati esterna deve configurare le credenziali sufficienti a fornire l'accesso in sola lettura agli oggetti di database di cui si necessita.

 Da un client di creazione di report sono disponibili le opzioni seguenti per la specifica delle credenziali:

-   Utilizzare un nome utente e una password archiviati. Per negoziare il doppio hop che si verifica quando il database contenente i dati del report è diverso dal server di report, selezionare le opzioni per utilizzare le credenziali come credenziali di Windows. È inoltre possibile scegliere di rappresentare l'utente autenticato dopo essersi connessi all'origine dati.

-   Non sono necessarie credenziali. Per utilizzare questa opzione, è necessario aver configurato l'account di esecuzione automatica sul server di report. Per altre informazioni, vedere [Configurare l'account di esecuzione automatica &#40;Gestione configurazione SSRS&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md) nella [documentazione relativa a Reporting Services](https://go.microsoft.com/fwlink/?linkid=121312) nel sito msdn.microsoft.com.

 Per ulteriori informazioni, vedere [connessioni dati, origini dati e stringhe di connessione in Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md) o [specificare le credenziali in Generatore report](../specify-credentials-in-report-builder.md).

 

##  <a name="queries"></a><a name="Query"></a>Query
 Una query consente di specificare quali dati recuperare per un set di dati del report. Le colonne nel set di risultati per una query popolano la raccolta dei campi per un set di dati. Se la query restituisce più set di risultati, nel report viene elaborato solo il primo set di risultati. Anche se esistono alcune differenze tra i database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e i [!INCLUDE[ssSDS](../../includes/sssds-md.md)], quali ad esempio le dimensioni di database supportate, scrivere query per [!INCLUDE[ssSDS](../../includes/sssds-md.md)]è simile allo scrivere query per database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Alcune istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] , ad esempio BACKUP, non sono supportate in [!INCLUDE[ssSDS](../../includes/sssds-md.md)], ma non sono quelle che si utilizzano nelle query del report. Per altre informazioni, vedere [Tipo di connessione SQL Server &#40;SSRS&#41;](sql-server-connection-type-ssrs.md).

 Per impostazione predefinita, se si crea una nuova query o si apre una query esistente che può essere rappresentata nella finestra Progettazione query con interfaccia grafica, è disponibile la progettazione query relazionale. È possibile specificare una query nei modi seguenti:

-   Compilare una query in modo interattivo. Utilizzare la finestra Progettazione query relazionale in cui è visualizzata una vista gerarchica di tabelle, viste, stored procedure e altri elementi del database organizzati in base allo schema del database. Selezionare le colonne dalle tabelle o dalle viste o specificare le stored procedure o le funzioni con valori di tabella. Limitare il numero di righe di dati da recuperare specificando i criteri di filtro. Personalizzare il filtro quando il report viene eseguito impostando l'opzione del parametro.

-   Digitare o incollare una query. Usare questa finestra per immettere direttamente testo [!INCLUDE[tsql](../../includes/tsql-md.md)] , per incollare testo di query da un'altra origine, per immettere query complesse che non è possibile compilare usando la progettazione query relazionale o per immettere espressioni basate su query.

-   Consente di importare una query esistente da un file o un report. Utilizzare il pulsante **Importa** da una finestra Progettazione query per individuare un file con estensione sql o rdl e importare una query.

 La finestra Progettazione query basata su testo supporta le due modalità seguenti:

-   [Testo](#QueryText) Digitare comandi [!INCLUDE[tsql](../../includes/tsql-md.md)] che selezionano dati dall'origine dati.

-   [Stored procedure](#QueryStoredProcedure) Scegliere da un elenco di stored procedure.

 Per altre informazioni, vedere [Interfaccia utente di Progettazione query relazionale &#40;Generatore report&#41;](relational-query-designer-user-interface-report-builder.md) e [Interfaccia utente di Progettazione query basata su testo &#40;Generatore report&#41;](text-based-query-designer-user-interface-report-builder.md).

 La finestra Progettazione query con interfaccia grafica usata da [!INCLUDE[ssSDS](../../includes/sssds-md.md)] offre il supporto predefinito per il raggruppamento e le aggregazioni per semplificare la scrittura di query che recuperano solo dati di riepilogo. Le funzionalità relative al linguaggio [!INCLUDE[tsql](../../includes/tsql-md.md)] sono: la clausola GROUP BY, parola chiave DISTINCT e gli aggregati quali SUM e COUNT. La finestra Progettazione query basata su testo offre il supporto completo per il linguaggio [!INCLUDE[tsql](../../includes/tsql-md.md)] , inclusi il raggruppamento e le aggregazioni. Per altre informazioni su [!INCLUDE[tsql](../../includes/tsql-md.md)], vedere la [Guida di riferimento a Transact-SQL &#40;Motore di database& #41;](/sql/t-sql/language-reference) nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Documentazione online](https://go.microsoft.com/fwlink/?LinkId=141687) di  sul sito msdn.microsoft.com.

###  <a name="using-query-type-text"></a><a name="QueryText"></a>Utilizzo del testo del tipo di query
 Nella finestra Progettazione query basata su testo, è possibile digitare i comandi [!INCLUDE[tsql](../../includes/tsql-md.md)] per definire i dati in un set di dati. La query [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente, ad esempio, seleziona i nomi di tutti i dipendenti con mansioni di assistente marketing:

```
SELECT
  HumanResources.Employee.BusinessEntityID
  ,HumanResources.Employee.JobTitle
  ,Person.Person.FirstName
  ,Person.Person.LastName
FROM
  Person.Person
  INNER JOIN HumanResources.Employee
    ON Person.Person.BusinessEntityID = HumanResources.Employee.BusinessEntityID
WHERE HumanResources.Employee.JobTitle = 'Marketing Assistant' 
```

 Fare clic sul pulsante **Esegui** (**!**) sulla barra degli strumenti per eseguire la query e visualizzare il set di risultati.

 Per parametrizzare questa query, aggiungere un parametro di query. Modificare ad esempio la clausola WHERE nella stringa seguente:

```
WHERE HumanResources.Employee.JobTitle = (@JobTitle)
```

 Quando si esegue la query, i parametri del report corrispondenti ai parametri di query verranno creati automaticamente. Per ulteriori informazioni, vedere [Parametri di query](#Parameters) di seguito in questo argomento.



###  <a name="using-query-type-storedprocedure"></a><a name="QueryStoredProcedure"></a>Utilizzo del tipo di query StoredProcedure
 È possibile specificare una stored procedure per una query del set di dati in uno dei seguenti modi:

-   Nella finestra di dialogo **Proprietà set di dati** , impostare l'opzione **Stored procedure** . Scegliere dall'elenco a discesa di stored procedure e funzioni con valori di tabella.

-   Nel riquadro Vista di database della finestra Progettazione query relazionale, selezionare una stored procedure o una funzione con valori di tabella.

-   Nella finestra Progettazione query basata su testo, selezionare **StoredProcedure** sulla barra degli strumenti.

 Dopo aver selezionato una stored procedure o una funzione con valori di tabella, è possibile eseguire la query. Verranno richiesti i valori dei parametri di input. Quando si esegue la query, i parametri del report corrispondenti ai parametri di input verranno creati automaticamente. Per ulteriori informazioni, vedere [Parametri di query](#Parameters) di seguito in questo argomento.

 È supportato solo il primo set di risultati recuperato per una stored procedure. Se una stored procedure restituisce più set di risultati, viene utilizzato solo il primo.

 Se in una stored procedure è presente un parametro con un valore predefinito, è possibile accedere a tale valore utilizzando la parola chiave DEFAULT come valore per il parametro. Se il parametro di query è collegato a un parametro di report, l'utente può digitare o selezionare la parola DEFAULT nella casella di input del parametro di report.

 Per altre informazioni sulle stored procedure, vedere "Stored Procedure (Motore di database)" nella [documentazione online di SQL Server](https://go.microsoft.com/fwlink/?linkid=98335) sul sito msdn.microsoft.com.



##  <a name="parameters"></a><a name="Parameters"></a> Parametri
 Quando il testo della query contiene variabili di query o stored procedure con parametri di input, vengono generati automaticamente i parametri di query corrispondenti per il set di dati e i parametri di report per il report. Il testo della query non deve includere l'istruzione DECLARE per ogni variabile della query.

 La query SQL seguente, ad esempio, crea un parametro di report denominato `EmpID`:

```
SELECT FirstName, LastName FROM HumanResources.Employee E INNER JOIN
       Person.Contact C ON  E.ContactID=C.ContactID 
WHERE EmployeeID = (@EmpID)
```

 Per impostazione predefinita, ogni parametro del report dispone di tipo di dati Text e un set di dati creato automaticamente per fornire un elenco a discesa di valori disponibili. Dopo aver creato i parametri di report, potrebbe essere necessario modificare i valori predefiniti. Per ulteriori informazioni, vedere la pagina relativa al [Parametri report &#40;Generatore report e Progettazione report&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).



##  <a name="remarks"></a>Osservazioni su <a name="Remarks"></a>

###### <a name="alternate-data-extensions"></a>Estensioni per i dati alternative
 È possibile recuperare i dati anche da un database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite un tipo di origine dati ODBC. La connessione a [!INCLUDE[ssSDS](../../includes/sssds-md.md)] tramite OLE DB non è supportata.

 Per altre informazioni, vedere [Tipo di connessione ODBC &#40;SSRS&#41;](odbc-connection-type-ssrs.md).

###### <a name="platform-and-version-information"></a>Informazioni sulla piattaforma e sulla versione
 Per altre informazioni sul supporto della piattaforma e della versione, vedere [Origini dati supportate da Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) nella documentazione relativa a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] inclusa nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [documentazione online](https://go.microsoft.com/fwlink/?linkid=121312) di .



##  <a name="how-to-topics"></a><a name="HowTo"></a>Procedure
 In questa sezione sono contenute istruzioni dettagliate per l'utilizzo di connessioni dati, origini dati e set di dati.

 [Aggiungere e verificare una connessione dati o un'origine dati &#40;Generatore report e SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)

 [Creare un set di dati condiviso o un set di dati incorporato &#40;Generatore report e SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)

 [Aggiungere un filtro a un set di dati &#40;Generatore report e SSRS&#41;](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)



##  <a name="related-sections"></a><a name="Related"></a>Sezioni correlate
 In queste sezioni della documentazione sono incluse informazioni concettuali approfondite sui dati dei report, nonché le procedure per definire, personalizzare e utilizzare parti di un report correlate ai dati.

 [Aggiungere dati a un Report &#40;Generatore report e SSRS&#41;](report-datasets-ssrs.md) Viene fornita una panoramica sull'accesso ai dati per il report.

 [Connessioni dati, origini dati e stringhe di connessione in Generatore report](../data-connections-data-sources-and-connection-strings-in-report-builder.md) Vengono fornite informazioni sulle connessioni dati e sulle origini dati.

 Set di set di impostazioni e set di [impostazioni di set di report incorporati &#40;Generatore report e SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) Fornisce informazioni sui set di dati incorporati e condivisi.

 [Raccolta di campi del set di dati &#40;Generatore report e SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md) Fornisce informazioni sulla raccolta di campi del set di dati generata dalla query.

 [Origini dati supportate da Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) nella documentazione relativa a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] inclusa nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [documentazione online](https://go.microsoft.com/fwlink/?linkid=121312) di .
Vengono fornite informazioni dettagliate sul supporto delle piattaforme e delle versioni per ogni estensione per i dati.



## <a name="see-also"></a>Vedere anche
 [Parametri del Report &#40;Generatore report e Progettazione report&#41;](../report-design/report-parameters-report-builder-and-report-designer.md) [filtrare, raggruppare e ordinare i dati &#40;Generatore report e SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) [espressioni &#40;Generatore report e SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)


