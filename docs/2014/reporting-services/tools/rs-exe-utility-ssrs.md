---
title: Utilità RS.exe (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- automatic report server tasks
- rs utility
- command prompt utilities [Reporting Services]
- report servers [Reporting Services], automating tasks
- command prompt utilities [SQL Server], rs
- scripts [Reporting Services], command prompt
- deploying reports [Reporting Services]
ms.assetid: bd6f958f-cce6-4e79-8a0f-9475da2919ce
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a6c4bf8f67f787214d38148db40ea8122a064a42
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66099831"
---
# <a name="rsexe-utility-ssrs"></a>RS.exe Utility (SSRS)
  L'utilità rs.exe elabora lo script fornito in un file di input. Utilizzare questa utilità per automatizzare le attività di amministrazione e distribuzione dei server di report.  
  
> [!NOTE]  
>  A partire da [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], l'utilità **rs** è supportata sia nei server di report configurati per la modalità integrata SharePoint che in quelli configurati in modalità nativa. Le versioni precedenti supportano solo le configurazioni in modalità nativa.  
  
 **Contenuto dell'argomento:**  
  
-   [Percorso file](#bkmk_filelocation)  
  
-   [Argomenti](#bkmk_arguments)  
  
-   [Autorizzazioni](#bkmk_permissions)  
  
-   [Esempi](#bkmk_examples)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      rs {-?}  
{-i input_file=}  
{-s serverURL}  
{-u username}  
{-p password}  
{-e endpoint}  
{-l time_out}  
{-b batchmode}  
{-v globalvars=}  
{-t trace}  
```  
  
##  <a name="file-location"></a><a name="bkmk_filelocation"></a> Percorso del file  
 **RS.exe** si trova in **\Programmi\Microsoft SQL Server\110\Tools\Binn**. È possibile eseguire l'utilità da qualsiasi cartella del file system.  
  
##  <a name="arguments"></a><a name="bkmk_arguments"></a>Argomenti  
 **-?**  
 (Facoltativo) Visualizza la sintassi degli argomenti **rs** .  
  
 `-i`*input_file*  
 (Obbligatorio) Consente di specificare il file con estensione rss da eseguire. Come valore è possibile indicare il percorso relativo o completo di tale file.  
  
 `-s`*ServerURL*  
 (Obbligatorio) Consente di specificare il nome del server Web e il nome della directory virtuale del server di report in cui eseguire il file. Un esempio di URL del server di report è `http://examplewebserver/reportserver`. Il prefisso http:// o https:// all'inizio del nome del server è facoltativo. Se si omette il prefisso, lo script del server di report prima tenta di utilizzare https e, qualora non funzionasse, utilizza http.  
  
 `-u`[*dominio*\\] *nome utente*  
 (Facoltativo) Consente di specificare l'account utente utilizzato per connettersi al server di report. Se si omettono `-u` e `-p`, verrà utilizzato l'account utente di Windows corrente.  
  
 `-p` *password*  
 (Obbligatorio se si specifica `-u`) Consente di specificare la password da utilizzare con l'argomento `-u`. Per questo valore viene applicata la distinzione tra maiuscole e minuscole.  
  
 `-e`  
 (Facoltativo) Specifica l'endpoint SOAP in base al quale eseguire lo script. Di seguito sono riportati i valori validi:  
  
-   Mgmt2010  
  
-   Mgmt2006  
  
-   Mgmt2005  
  
-   Exec2005  
  
 Se non si specifica alcun valore, viene utilizzato l'endpoint Mgmt2005. Per ulteriori informazioni sugli endpoint SOAP, vedere [Report Server Web Service Endpoints](../report-server-web-service/methods/report-server-web-service-endpoints.md).  
  
 `-l`*time_out*  
 Opzionale Specifica il numero di secondi che devono trascorrere prima che si verifichi il timeout della connessione al server. Il valore predefinito è 60 secondi. Se non si specifica un valore per il timeout, verrà utilizzato il valore predefinito. Se si specifica il valore `0`, non si verificherà mai il timeout della connessione.  
  
 **-b**  
 (Facoltativo) Specifica che i comandi del file di script vengano eseguiti come batch. Se uno o più comandi hanno esito negativo, verrà eseguito il rollback dell'intero batch. Vi sono tuttavia comandi non eseguibili in batch. Tali comandi verranno eseguiti normalmente e verrà eseguito un rollback solo in caso di eccezioni generate e non gestite nell'ambito dello script. Se lo script gestisce un'eccezione e completa normalmente la routine `Main`, verrà eseguito il commit del batch. Se si omette questo parametro, i comandi verranno eseguiti senza la creazione di un batch. Per altre informazioni, vedere [Batching Methods](../report-server-web-service-net-framework-soap-headers/batching-methods.md).  
  
 `-v`*GlobalVar (*  
 (Facoltativo) Consente di specificare le variabili globali utilizzate nello script. Se lo script utilizza variabili globali, è necessario specificare questo argomento. Il valore specificato deve essere valido per la variabile globale definita nel file con estensione rss. È necessario specificare una variabile globale per ogni argomento **-v** .  
  
 L'argomento `-v` viene specificato nella riga di comando ed è utilizzato per impostare il valore per una variabile globale definita in fase di esecuzione nello script. Se, ad esempio, lo script contiene un variabile denominata *parentFolder*, è possibile specificare un nome per la cartella nella riga di comando:  
  
 `rs.exe -i myScriptFile.rss -s http://myServer/reportserver -v parentFolder="Financial Reports"`  
  
 Le variabili globali vengono create con i nomi indicati e impostate sui valori specificati. Ad esempio, **-v a =**"`1`" **-v b =**"`2`" restituisce `a` una variabile denominata con un valore di "`1`" e una variabile **b** con un valore "`2`".  
  
 Le variabili globali sono disponibili per qualsiasi funzione nello script. Una barra rovesciata e le virgolette (**\\"**) vengono interpretate come virgolette doppie. Le virgolette sono necessarie solo se la stringa contiene uno spazio. I nomi delle variabili devono essere [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]validi per; devono iniziare con un carattere alfabetico o un carattere di sottolineatura e contenere caratteri alfabetici, cifre o caratteri di sottolineatura. Le parole riservate non possono essere utilizzate come nomi di variabili. Per altre informazioni sull'uso delle variabili globali, vedere [Raccolte predefinite nelle espressioni &#40;Generatore report e SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).  
  
 **-t**  
 (Facoltativo) Crea l'output dei messaggi di errore nel log di traccia. Questo argomento non accetta un valore. Per altre informazioni, vedere [Report Server Service Trace Log](../report-server/report-server-service-trace-log.md).  
  
##  <a name="permissions"></a><a name="bkmk_permissions"></a> Autorizzazioni  
 Per eseguire questo strumento, è necessario disporre dell'autorizzazione per connettersi all'istanza del server di report in cui lo script è in esecuzione. È possibile eseguire script per apportare modifiche nel computer locale o in un computer remoto. Per apportare modifiche a un server di report installato in un computer remoto, specificare il computer remoto nell'argomento `-s`.  
  
##  <a name="examples"></a><a name="bkmk_examples"></a> Esempi  
 Nell'esempio seguente viene illustrato come specificare il file script contenente lo script di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET e i metodi del servizio Web che si desidera eseguire.  
  
```  
rs -i c:\scriptfiles\script_copycontent.rss -s http://localhost/reportserver  
```  
  
  Per un esempio dettagliato, vedere [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).  
  
 Per ulteriori esempi, vedere [Eseguire un file script di Reporting Services](run-a-reporting-services-script-file.md)  
  
## <a name="remarks"></a>Osservazioni  
 È possibile definire script per impostare le proprietà di sistema, pubblicare report e così via. Gli script creati possono includere qualsiasi metodo dell'API di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Per ulteriori informazioni sui metodi e sulle proprietà disponibili, vedere [Report Server Web Service](../report-server-web-service/report-server-web-service.md).  
  
 Lo script deve essere scritto in codice [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET e archiviato in un file di testo Unicode o UTF-8 con estensione di file rss. Non è possibile eseguire il debug degli script con l'utilità **rs** . Per eseguire il debug di uno script, eseguire [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]il codice all'interno di.  
  
> [!TIP]  
>   Per un esempio dettagliato, vedere [Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).  
  
## <a name="see-also"></a>Vedi anche  
 [Eseguire un file script di Reporting Services](run-a-reporting-services-script-file.md)   
 [Script per distribuzione e attività amministrative](script-deployment-and-administrative-tasks.md)   
 [Script con l'utilità rs. exe e il servizio Web](script-with-the-rs-exe-utility-and-the-web-service.md)   
 [Utilità della riga di comando del server di report &#40;SSRS&#41;](report-server-command-prompt-utilities-ssrs.md)  
  
  
