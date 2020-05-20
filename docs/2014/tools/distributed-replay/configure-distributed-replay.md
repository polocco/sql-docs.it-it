---
title: Configurare Riesecuzione distribuita | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: aee11dde-daad-439b-b594-9f4aeac94335
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 40cbece7c2ee5aad3b65a0b4066b409d9f0b6b6e
ms.sourcegitcommit: 5a9ec5e28543f106bf9e7aa30dd0a726bb750e25
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/08/2020
ms.locfileid: "82925055"
---
# <a name="configure-distributed-replay"></a>Configurare Distributed Replay
  I dettagli relativi alla configurazione della Riesecuzione distribuita di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono specificati in file XML nel controller della Riesecuzione distribuita, nei client e nella posizione in cui è installato lo strumento di amministrazione, ovvero i file seguenti:  
  
-   [File di configurazione del controller](#DReplayController)  
  
-   [File di configurazione del client](#DReplayClient)  
  
-   [File di configurazione della pre-elaborazione](#PreprocessConfig)  
  
-   [File di configurazione della riproduzione](#ReplayConfig)  
  
##  <a name="controller-configuration-file-dreplaycontrollerconfig"></a><a name="DReplayController"></a> File di configurazione del controller: DReplayController.config  
 All'avvio del servizio Distributed Replay Controller di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , viene caricato il livello di registrazione dal file di configurazione del controller, ovvero `DReplayController.config`. Questo file si trova nella cartella in cui è stato installato il servizio Distributed Replay Controller:  
  
 **\<percorso installazione controller>\DReplayController.config**  
  
 Nel livello di registrazione specificato nel file di configurazione del controller è inclusa la seguente impostazione:  
  
|Impostazione|Elemento XML|Descrizione|Valori consentiti|Obbligatoria|  
|-------------|-----------------|-----------------|--------------------|--------------|  
|Livello di registrazione|`<LoggingLevel>`|Specifica il livello di registrazione per il servizio controller.|`INFORMATION` &#124; `WARNING` &#124; `CRITICAL`|No. Per impostazione predefinita, il valore è `CRITICAL`.|  
  
### <a name="example"></a>Esempio  
 In questo esempio viene illustrato un file di configurazione del controller che è stato modificato per eliminare le voci di log `INFORMATION` e `WARNING` .  
  
```  
<?xml version='1.0'?>  
<Options>  
<LoggingLevel>CRITICAL</LoggingLevel>  
</Options>  
```  
  
##  <a name="client-configuration-file-dreplayclientconfig"></a><a name="DReplayClient"></a> File di configurazione del client: DReplayClient.config  
 All'avvio del servizio client Distributed Replay di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vengono caricate le impostazioni di configurazione dal file di configurazione del client, ovvero `DReplayClient.config`. Questo file si trova in ogni client, nella cartella in cui è stato installato il servizio client Distributed Replay:  
  
 **\<percorso installazione client>\DReplayClient.config**  
  
 Di seguito vengono indicate le impostazioni specificate nel file di configurazione del client:  
  
|Impostazione|Elemento XML|Descrizione|Valori consentiti|Obbligatoria|  
|-------------|-----------------|-----------------|--------------------|--------------|  
|Controller|`<Controller>`|Specifica il nome computer del controller. Il client tenterà di registrarsi nell'ambiente Distributed Replay contattando il controller.|È possibile utilizzare "`localhost`" o "`.`" per fare riferimento al computer locale.|No. Per impostazione predefinita, viene effettuato un tentativo di registrazione del client nell'istanza del controller eseguita in locale ("`.`"), se presente.|  
|Directory di lavoro client|`<WorkingDirectory>`|Percorso locale nel client in cui vengono salvati i file di recapito.<br /><br /> I file inclusi in questa directory vengono sovrascritti alla riproduzione successiva.|Nome di directory completo, che inizia con la lettera di unità.|No. Se non è specificato alcun valore, i file di recapito verranno salvati nello stesso percorso del file di configurazione del client predefinito. Se viene specificato un valore e la cartella non esiste nel client, il servizio client non verrà avviato.|  
|Directory dei risultati del client|`<ResultDirectory>`|Percorso locale nel client in cui viene salvato il file di traccia dei risultati dall'attività di riproduzione (per il client).<br /><br /> I file inclusi in questa directory vengono sovrascritti alla riproduzione successiva.|Nome di directory completo, che inizia con la lettera di unità.|No. Se non è specificato alcun valore, il file di traccia dei risultati verrà salvato nello stesso percorso del file di configurazione del client predefinito. Se viene specificato un valore e la cartella non esiste nel client, il servizio client non verrà avviato.|  
|Livello di registrazione|`<LoggingLevel>`|Livello di registrazione per il servizio client.|`INFORMATION` &#124; `WARNING` &#124; `CRITICAL`|No. Per impostazione predefinita, il valore è `CRITICAL`.|  
  
### <a name="example"></a>Esempio  
 In questo esempio viene illustrato un file di configurazione del client che è stato modificato per specificare che il servizio controller viene eseguito in un computer diverso, denominato `Controller1`. Gli elementi `WorkingDirectory` e `ResultDirectory` sono stati configurati per utilizzare rispettivamente le cartelle `c:\ClientWorkingDir` e `c:\ResultTraceDir`. Il livello di registrazione è stato modificato rispetto al valore predefinito per eliminare le voci di log `INFORMATION` e `WARNING` .  
  
```  
<?xml version='1.0'?>  
<Options>  
    <Controller>Controller1</Controller>  
    <WorkingDirectory>c:\ClientWorkingDir</WorkingDirectory>  
    <ResultDirectory>c:\ResultTraceDir</ResultDirectory>  
    <LoggingLevel>CRITICAL</LoggingLevel>  
</Options>  
```  
  
##  <a name="preprocess-configuration-file-dreplayexepreprocessconfig"></a><a name="PreprocessConfig"></a> File di configurazione della pre-elaborazione: DReplay.exe.preprocess.config  
 Quando si utilizza lo strumento di amministrazione per avviare la fase di pre-elaborazione, lo strumento di amministrazione carica le impostazioni di pre-elaborazione dal file di configurazione della pre-elaborazione, ovvero `DReplay.exe.preprocess.config`.  
  
 Usare il file di configurazione predefinito o il parametro **-c** dello strumento di amministrazione per specificare il percorso di un file di configurazione di pre-elaborazione modificato. Per altre informazioni sull'uso dell'opzione preprocess dello strumento di amministrazione, vedere [Opzione preprocess &#40;strumento di amministrazione Riesecuzione distribuita&#41;](preprocess-option-distributed-replay-administration-tool.md).  
  
 Il file di configurazione della pre-elaborazione predefinito si trova nella cartella in cui è stato installato lo strumento di amministrazione:  
  
 **\<percorso installazione strumento di amministrazione>\DReplayAdmin\DReplay.exe.preprocess.config**  
  
 Le impostazioni di configurazione della pre-elaborazione vengono specificate in elementi XML figli dell'elemento `<PreprocessModifiers>` nel file di configurazione della pre-elaborazione. Tali impostazioni includono quanto segue:  
  
|Impostazione|Elemento XML|Descrizione|Valori consentiti|Obbligatoria|  
|-------------|-----------------|-----------------|--------------------|--------------|  
|Inclusione delle attività della sessione di sistema|`<IncSystemSession>`|Indica se le attività della sessione di sistema eseguite durante l'acquisizione verranno incluse durante la riproduzione.|`Yes` &#124; `No`|No. Per impostazione predefinita, il valore è `No`.|  
|Tempo massimo di inattività|`<MaxIdleTime>`|Fissa il tempo di inattività su un numero assoluto (in secondi).|Intero >=-1<br /><br /> `-1` indica nessuna modifica rispetto al valore originale nel file di traccia originale.<br /><br /> `0` indica che sono in corso una o più attività in un momento specificato.|No. Per impostazione predefinita, il valore è `-1`.|  
  
### <a name="example"></a>Esempio  
 File di configurazione della pre-elaborazione predefinito:  
  
```  
<?xml version='1.0'?>  
<Options>  
    <PreprocessModifiers>  
        <IncSystemSession>No</IncSystemSession>  
        <MaxIdleTime>-1</MaxIdleTime>  
    </PreprocessModifiers>  
</Options>  
```  
  
##  <a name="replay-configuration-file-dreplayexereplayconfig"></a><a name="ReplayConfig"></a> File di configurazione della riproduzione: DReplay.exe.replay.config  
 Quando si utilizza lo strumento di amministrazione per avviare la fase di riproduzione dell'evento, lo strumento di amministrazione carica le impostazioni di riproduzione dal file di configurazione della riproduzione, ovvero `DReplay.exe.replay.config`.  
  
 Usare il file di configurazione predefinito o il parametro **-c** dello strumento di amministrazione per specificare il percorso di un file di configurazione della riproduzione modificato. Per altre informazioni sull'uso dell'opzione replay dello strumento di amministrazione, vedere [Opzione replay &#40;strumento di amministrazione Riesecuzione distribuita&#41;](replay-option-distributed-replay-administration-tool.md).  
  
 Il file di configurazione della riproduzione predefinito si trova nella cartella in cui è stato installato lo strumento di amministrazione:  
  
 **\<percorso installazione strumento di amministrazione>\DReplayAdmin\DReplay.exe.replay.config**  
  
 Le impostazioni di configurazione della riproduzione vengono specificate in elementi XML figli degli elementi `<ReplayOptions>` e `<OutputOptions>` del file di configurazione della riproduzione.  
  
### <a name="replayoptions-element"></a>Elemento \<ReplayOptions>  
 Di seguito vengono indicate le impostazioni specificate dal file di configurazione della riproduzione nell'elemento `<ReplayOptions>` :  
  
|Impostazione|Elemento XML|Descrizione|Valori consentiti|Obbligatoria|  
|-------------|-----------------|-----------------|--------------------|--------------|  
|Istanza di destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (server di prova)|`<Server>`|Specifica il nome del server e dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a cui connettersi.|*server_name*[\\*instance_name*]<br /><br /> Non è possibile utilizzare "`localhost`" o "`.`" per rappresentare l'host locale.|No, se il nome del server è già specificato con il parametro **-s**_target server_ con l'opzione **replay** dello strumento di amministrazione.|  
|Modalità di sequenza|`<SequencingMode>`|Specifica la modalità utilizzata per la pianificazione degli eventi.|`synchronization` &#124; `stress`|No. Per impostazione predefinita, il valore è `stress`.|  
|Granularità di scala di stress|`<StressScaleGranularity>`|Specifica se tutte le connessioni nel Servizio Profilo l'Identificatore (SPID) devono essere ridimensionate, insieme (SPID) o indipendentemente (Connessione), in modalità di stress.|SPID &#124; Connessione|Sì. Per impostazione predefinita, il valore è `SPID`.|  
|Scala del tempo di connessione|`<ConnectTimeScale>`|Viene utilizzata per ridimensionare il tempo di connessione in modalità di stress.|Numero intero compreso tra `1` e `100`.|No. Per impostazione predefinita, il valore è `100`.|  
|Scala del tempo interazione utente|`<ThinkTimeScale>`|Viene utilizzata per ridimensionare il tempo interazione utente in modalità di stress.|Numero intero compreso tra `0` e `100`.|No. Per impostazione predefinita, il valore è `100`.|  
|Utilizzare un pool di connessioni|`<UseConnectionPooling>`|Specifica se il pool di connessioni sarà abilitato su ogni client di riproduzione distribuita.|Yes &#124; No|Sì. Per impostazione predefinita, il valore è `Yes`.|  
|Intervallo di Health Monitor|`<HealthmonInterval>`|Indica la frequenza, in secondi, con cui eseguire Health Monitor.<br /><br /> Questo valore viene utilizzato solo in modalità di sincronizzazione.|Numero intero >= 1<br /><br /> (`-1` per disabilitare l'impostazione)|No. Per impostazione predefinita, il valore è `60`.|  
|Timeout query|`<QueryTimeout>`|Specifica il valore di timeout query in secondi. Questo valore è valido solo fino a quando non viene restituita la prima riga.|Numero intero >= 1<br /><br /> (`-1` per disabilitare l'impostazione)|No. Per impostazione predefinita, il valore è `3600`.|  
|Thread per client|`<ThreadsPerClient>`|Specifica il numero di thread di riproduzione da utilizzare per ogni client di riproduzione.|Numero intero compreso tra `1` e `512`.|No. Se non è specificata, in Distributed Replay verrà utilizzato il valore `255`.|  
  
### <a name="outputoptions-element"></a>Elemento \<OutputOptions>  
 Di seguito vengono indicate le impostazioni specificate dal file di configurazione della riproduzione nell'elemento `<OutputOptions>` :  
  
|Impostazione|Elemento XML|Descrizione|Valori consentiti|Obbligatoria|  
|-------------|-----------------|-----------------|--------------------|--------------|  
|Registrazione del conteggio delle righe|`<RecordRowCount>`|Indica se deve essere registrato il conteggio delle righe per ogni set di risultati.|`Yes` &#124; `No`|No. Per impostazione predefinita, il valore è `Yes`.|  
|Registrazione del set di risultati|`<RecordResultSet>`|Indica se deve essere registrato il contenuto di tutti i set di risultati.|`Yes` &#124; `No`|No. Per impostazione predefinita, il valore è `No`.|  
  
### <a name="example"></a>Esempio  
 File di configurazione della riproduzione predefinito:  
  
```  
<?xml version='1.0'?>  
<Options>  
    <ReplayOptions>  
        <Server></Server>  
        <SequencingMode>stress</SequencingMode>  
        <ConnectTimeScale></ConnectTimeScale>  
        <ThinkTimeScale></ThinkTimeScale>  
        <HealthmonInterval>60</HealthmonInterval>  
        <QueryTimeout>3600</QueryTimeout>  
        <ThreadsPerClient></ThreadsPerClient>  
    </ReplayOptions>  
    <OutputOptions>  
        <ResultTrace>  
            <RecordRowCount>Yes</RecordRowCount>  
            <RecordResultSet>No</RecordResultSet>  
        </ResultTrace>  
    </OutputOptions>  
</Options>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni della riga di comando dello strumento di amministrazione &#40;Distributed Replay Utility&#41;](administration-tool-command-line-options-distributed-replay-utility.md)   
 [SQL Server Distributed Replay](sql-server-distributed-replay.md)   
 [Forum di SQL Server Distributed Replay](https://social.technet.microsoft.com/Forums/sl/sqldru/)   
 [Using Distributed Replay to Load Test Your SQL Server - Part 2](https://docs.microsoft.com/archive/blogs/msdn/mspfe/using-distributed-replay-to-load-test-your-sql-serverpart-2)  (Uso di Riesecuzione distribuita per testare il caricamento di SQL Server, seconda parte)  
 [Using Distributed Replay to Load Test Your SQL Server - Part 1](https://docs.microsoft.com/archive/blogs/batuhanyildiz/using-distributed-replay-to-load-test-your-sql-serverpart-1) (Uso di Riesecuzione distribuita per testare il caricamento di SQL Server, prima parte)  
  
  
