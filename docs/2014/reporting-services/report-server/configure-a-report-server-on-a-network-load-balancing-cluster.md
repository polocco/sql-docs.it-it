---
title: Configurare un server di report in un cluster per il bilanciamento del carico di rete | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], network load balancing
ms.assetid: 6bfa5698-de65-43c3-b940-044f41c162d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bff66ca0f644f862b7cdcfb534b55c4e8ebdd888
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66104086"
---
# <a name="configure-a-report-server-on-a-network-load-balancing-cluster"></a>Configurare un server di report in un cluster per il bilanciamento del carico di rete
  Se si intende configurare la scalabilità orizzontale di un server di report per l'esecuzione in un cluster per il bilanciamento del carico di rete (NLB, Network Load Balancing), è necessario effettuare le operazioni seguenti:  
  
-   Verificare che il cluster per il bilanciamento del carico di rete sia accessibile tramite un nome del server virtuale di cui viene eseguito il mapping all'indirizzo IP del server virtuale. Un nome del server virtuale è necessario per poter configurare un singolo punto di ingresso nel cluster per il bilanciamento del carico di rete. Quando si configura un URL per ogni istanza del server di report, è necessario specificare il nome del server virtuale come host.  
  
-   Configurare la convalida dello stato di visualizzazione per supportare la visualizzazione di report interattivi. Il rendering dei report interattivi viene in genere eseguito diverse volte durante una singola sessione utente per visualizzare dati nuovi o diversi in risposta alle azioni dell'utente. La configurazione della convalida dello stato di visualizzazione consente di mantenere la continuità all'interno della sessione utente, indipendentemente dal server di report che risponde alla richiesta effettiva.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] non fornisce la funzionalità per il bilanciamento del carico di una distribuzione con scalabilità orizzontale, né per la definizione di un singolo punto di accesso tramite un URL condiviso. Per supportare una distribuzione con scalabilità orizzontale di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , è necessario implementare una soluzione cluster per il bilanciamento del carico di rete software o hardware distinta.  
  
 È possibile installare [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in nodi che fanno già parte di un cluster per il bilanciamento del carico di rete oppure configurare innanzitutto una distribuzione con scalabilità orizzontale e quindi installare il software del cluster.  
  
## <a name="steps-for-report-server-deployment-on-an-nlb-cluster"></a>Passaggi per la distribuzione del server di report in un cluster per il bilanciamento del carico di rete  
 Per installare e configurare la distribuzione, utilizzare le linee guida seguenti:  
  
|Passaggio|Descrizione|Ulteriori informazioni|  
|----------|-----------------|----------------------|  
|1|Prima di installare Reporting Services nei nodi del server in un cluster per il bilanciamento del carico di rete, verificare i requisiti per la distribuzione con scalabilità orizzontale.|[Configurare una distribuzione con scalabilità orizzontale di un server di report in modalità nativa &#40;SSRS Configuration Manager&#41;](../install-windows/configure-a-native-mode-report-server-scale-out-deployment.md) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentazione online di|  
|2|Configurare il cluster per il bilanciamento del carico di rete e verificarne il corretto funzionamento.<br /><br /> Assicurarsi di eseguire il mapping di un nome dell'intestazione host all'IP del server virtuale del cluster per il bilanciamento del carico di rete. Il nome dell'intestazione host viene utilizzato nell'URL del server di report ed è più semplice da ricordare e digitare rispetto a un indirizzo IP.|Per ulteriori informazioni, vedere la documentazione di Windows Server relativa alla versione del sistema operativo Windows utilizzato.|  
|3|Aggiungere il nome del NetBIOS e il nome di dominio completo (FQDN) per l'intestazione host all'elenco di **BackConnectionHostNames** archiviato nel Registro di sistema di Windows. Seguire i passaggi descritti in **Method 2: Specify host names** (Metodo 2: Specificare i nomi host) nell'articolo [KB 896861](https://support.microsoft.com/kb/896861) (https://support.microsoft.com/kb/896861), con la rettifica seguente. In base a quanto specificato nel**passaggio 7** dell'articolo della KB: uscire dall'editor del Registro di sistema e riavviare il servizio IISAdmin. Si consiglia, invece, di riavviare il computer per assicurarsi che le modifiche abbiano effetto.<br /><br /> Ad esempio, se il nome dell'intestazione host \<MyServer> è un nome virtuale per il nome computer Windows "contoso", probabilmente è possibile fare riferimento al modulo FQDN come "contoso.domain.com". Sarà necessario aggiungere il nome di intestazione host (MyServer ) e il nome FQDN (contoso.domain.com) all'elenco in **BackConnectionHostNames**.|Questo passaggio è obbligatorio se l'ambiente server implica l'autenticazione NTLM sul computer locale, creando una connessione loopback.<br /><br /> In tal caso, le richieste tra Gestione report e Server di report restituiscono un errore 401 (Unauthorized).|  
|4|Installare [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in modalità solo file in nodi che appartengono già a un cluster per il bilanciamento del carico di rete e configurare le istanze del server di report per la distribuzione con scalabilità orizzontale.<br /><br /> La scalabilità orizzontale configurata potrebbe non rispondere a richieste indirizzate all'IP del server virtuale. La configurazione della scalabilità orizzontale per l'utilizzo dell'IP del server virtuale viene effettuata in un passaggio successivo, dopo la configurazione della convalida dello stato di visualizzazione.|[Configurare una distribuzione con scalabilità orizzontale di un server di report in modalità nativa &#40;Gestione configurazione SSRS&#41;](../install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)|  
|5|Configurare la convalida dello stato di visualizzazione.<br /><br /> Per ottenere risultati ottimali, eseguire questo passaggio dopo avere configurato la distribuzione con scalabilità orizzontale e prima di configurare le istanze del server di report per l'utilizzo dell'IP del server virtuale. Configurando innanzitutto la convalida dello stato di visualizzazione, è possibile evitare eccezioni a causa di errori di convalida dello stato quando gli utenti tentano di accedere a report interattivi.|[Come configurare la convalida dello stato di visualizzazione](#ViewState) in questo argomento.|  
|6|Configurare `Hostname` e `UrlRoot` per l'utilizzo dell'IP del server virtuale del cluster per il bilanciamento del carico di rete.|[Come configurare Hostname e UrlRoot](#SpecifyingVirtualServerName) in questo argomento.|  
|7|Verificare che sia possibile accedere ai server tramite il nome host specificato.|[Verificare l'accesso al server di report](#Verify) in questo argomento.|  
  
##  <a name="how-to-configure-view-state-validation"></a><a name="ViewState"></a>Come configurare la convalida dello stato di visualizzazione  
 Per eseguire una distribuzione con scalabilità orizzontale in un cluster per il bilanciamento del carico di rete, è necessario configurare la convalida dello stato di visualizzazione in modo che gli utenti possano visualizzare report HTML interattivi. Questa operazione deve essere eseguita sia per il server di report che per Gestione report.  
  
 La convalida dello stato di visualizzazione è controllata da ASP.NET, è abilitata per impostazione predefinita e utilizza l'identità del servizio Web per eseguire la convalida. In uno scenario di cluster per il bilanciamento del carico di rete, tuttavia, sono presenti più istanze del servizio e identità del servizio Web eseguite in computer diversi. Poiché l'identità del servizio varia per ciascun nodo, non è possibile basarsi su una singola identità del processo per eseguire la convalida.  
  
 Per risolvere questo problema, è possibile generare una chiave di convalida arbitraria per supportare la convalida dello stato di visualizzazione e quindi configurare manualmente ciascun nodo del server di report per l'utilizzo della stessa chiave. È possibile utilizzare qualsiasi sequenza esadecimale generata casualmente. L'algoritmo di convalida, ad esempio SHA1, determina la lunghezza della sequenza esadecimale.  
  
1.  Generare una chiave di convalida e una chiave di decrittografia mediante la funzionalità di generazione automatica disponibile in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Alla fine, è necessario disporre di una singola <`machineKey`> voce che può essere incollata nel file Web. config per ogni istanza di gestione report nella distribuzione con scalabilità orizzontale.  
  
     Nell'esempio seguente viene illustrato il valore che è necessario ottenere: Non copiare l'esempio nei file di configurazione in uso, in quanto i valori di chiave non sono validi.  
  
    ```  
    <machineKey validationKey="123455555" decryptionKey="678999999" validation="SHA1" decryption="AES"/>  
    ```  
  
2.  Aprire il file Web. config per Gestione report e nella sezione <`system.web`> incollare l'elemento <`machineKey`> generato. Per impostazione predefinita, il file Web.config di Gestione report si trova in \Programmi\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportManager\Web.config.  
  
3.  Salvare il file.  
  
4.  Ripetere il passaggio precedente per ogni server di report presente nella distribuzione con scalabilità orizzontale.  
  
5.  Verificare che tutti i file Web. config nelle cartelle \Reporting Services\Report Manager contengano `machineKey` elementi <> identici `system.web` nella sezione <>.  
  
##  <a name="how-to-configure-hostname-and-urlroot"></a><a name="SpecifyingVirtualServerName"></a>Come configurare hostname e UrlRoot  
 Per configurare una distribuzione con scalabilità orizzontale del server di report in un cluster per il bilanciamento del carico di rete, è necessario definire un unico nome del server virtuale che fornisce un singolo punto di accesso al cluster di server. Successivamente, registrare il nome del server virtuale con Domain Name Server (DNS) nel proprio ambiente.  
  
 Dopo avere definito il nome del server virtuale, è possibile configurare le proprietà `Hostname` e `UrlRoot` nel file RSReportServer.config per includere tale nome nell'URL del server di report.  
  
 Configurare la proprietà `Hostname` quando si utilizzano prenotazioni URL con caratteri jolly nell'ambiente di gestione dei report. Quando si specifica la proprietà `Hostname` come nome del server virtuale del server con bilanciamento del carico di rete, il traffico di rete relativo all'ambiente di gestione dei report viene indirizzato a quest'ultimo server, che distribuisce quindi le richieste tra i nodi del server di report.  
  
 Configurare inoltre la proprietà `UrlRoot` in modo che i collegamenti al report funzionino nei report esportati in report statici, ad esempio in formato Excel o PDF, oppure in report generati da sottoscrizioni, ad esempio una sottoscrizione con recapito tramite posta elettronica.  
  
 Se si integra [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] con [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 3,0 o [!INCLUDE[offSPServ](../../includes/offspserv-md.md)] 2007 oppure si ospitano i report in un'applicazione Web personalizzata, potrebbe essere necessario configurare solo la `UrlRoot` proprietà. In questo caso, configurare la proprietà `UrlRoot` in modo che rappresenti l'URL del sito di SharePoint o dell'applicazione Web. In questo modo il traffico di rete relativo all'ambiente di gestione dei report verrà indirizzato all'applicazione che gestisce i report anziché al server di report o al cluster per il bilanciamento del carico di rete.  
  
 Non modificare `ReportServerUrl` per evitare di introdurre un round trip aggiuntivo attraverso il server virtuale ogni volta che viene gestita una richiesta interna. Per altre informazioni, vedere [Modificare un file di configurazione di Reporting Services &#40;RSreportserver.config&#41;](../install-windows/urls-in-configuration-files-ssrs-configuration-manager.md). Per altre informazioni sulla modifica del file di configurazione, vedere [Modificare un file di configurazione di Reporting Services &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md) nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
1.  Aprire RSReportServer.config in un editor di testo.  
  
2.  Trovare la sezione del ** \<>di servizio** e aggiungere le informazioni seguenti al file di configurazione, sostituendo il `Hostname` valore con il nome del server virtuale per il server NLB:  
  
    ```  
    <Hostname>virtual_server</Hostname>  
    ```  
  
3.  Individuare `UrlRoot`. L'elemento non è specificato nel file di configurazione, ma il valore predefinito usato è un URL nel formato seguente: http://o https://\<*nomecomputer*>/\<*ReportServer*>, dove \< *ReportServer*> è il nome della directory virtuale del servizio Web ReportServer.  
  
4.  Digitare un valore per `UrlRoot` che includa il nome virtuale del cluster nel formato seguente: http://o https://\<*virtual_server*>/\<*ReportServer*>.  
  
5.  Salvare il file.  
  
6.  Ripetere questi passaggi in ciascun file RSReportServer.config per ogni server di report presente nella distribuzione con scalabilità orizzontale.  
  
##  <a name="verify-report-server-access"></a><a name="Verify"></a>Verificare l'accesso al server di report  
 Verificare che sia possibile accedere alla distribuzione con scalabilità orizzontale tramite il nome del server virtuale, https://MyVirtualServerName/reportserver ad esempio https://MyVirtualServerName/reports)e.  
  
 È possibile determinare il nodo che elabora effettivamente i report esaminando i file di log del server di report o controllando il log di esecuzione di RS. La tabella del log di esecuzione contiene una colonna denominata **InstanceName** che indica l'istanza che ha elaborato una richiesta specifica. Per altre informazioni, vedere [File di log e origini di Reporting Services](../report-server/reporting-services-log-files-and-sources.md) nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Se non è possibile connettersi al server di report, controllare il bilanciamento del carico di rete per verificare che le richieste vengano inviate al server di report e visualizzare il log HTTP del server di report per appurare che il server le stia ricevendo.  
  
#### <a name="troubleshooting-failed-requests"></a>Risoluzione dei problemi relativi alle richieste non riuscite  
 Se le richieste non raggiungono le istanze del server di report, controllare il file RSReportServer.config per verificare che il nome del server virtuale sia specificato come nome host per gli URL del server di report:  
  
1.  Aprire il file RSReportServer.config in un editor di testo.  
  
2.  Trovare <`Hostname`>, <`ReportServerUrl`> e <`UrlRoot`> e verificare il nome host per ogni impostazione. Se il valore non corrisponde al nome host previsto, sostituirlo con il nome host corretto.  
  
 Se si avvia lo strumento di configurazione di Reporting Services dopo avere apportato queste modifiche, lo `ReportServerUrl` strumento potrebbe modificare le impostazioni di <> sul valore predefinito. Mantenere sempre una copia di backup dei file di configurazione per i casi in cui sia necessario sostituirli con la versione contenente le impostazioni che si desidera utilizzare.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione configurazione Reporting Services &#40;modalità nativa&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Configurare un URL &#40;Configuration Manager SSRS&#41;](../install-windows/configure-a-url-ssrs-configuration-manager.md)   
 [Configurare una distribuzione con scalabilità orizzontale di un server di report in modalità nativa &#40;Configuration Manager SSRS&#41;](../install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)   
 [Gestire un server di report in modalità nativa di Reporting Services](manage-a-reporting-services-native-mode-report-server.md)  
  
  
