---
title: Configurare connessioni SSL in un server di report in modalità nativa | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Secure Sockets Layer (SSL)
ms.assetid: 212f2042-456a-4c0a-8d76-480b18f02431
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7fb33e6ccb5afbdee1bf6c3673a24548d6fe9961
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66102126"
---
# <a name="configure-ssl-connections-on-a-native-mode-report-server"></a>Configurare connessioni SSL in un server di report in modalità nativa
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] La modalità nativa usa il servizio SSL HTTP (Secure Sockets Layer) per stabilire connessioni crittografate a un server di report. Se si dispone di un file di certificato (con estensione cer) installato in un archivio certificati locale nel server di report, è possibile associare il certificato a una prenotazione di URL di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per supportare le connessioni al server di report tramite un canale crittografato.  
  
> [!TIP]  
>  Se si utilizza la modalità SharePoint di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , vedere la documentazione su SharePoint per ulteriori informazioni. Ad esempio, [How to enable SSL on a SharePoint 2010 web application (https://blogs.msdn.com/b/sowmyancs/archive/2010/02/12/how-to-enable-ssl-on-a-sharepoint-web-application.aspx)](https://blogs.msdn.com/b/sowmyancs/archive/2010/02/12/how-to-enable-ssl-on-a-sharepoint-web-application.aspx) (Come abilitare SSL in un'applicazione Web SharePoint 2010).  
  
 Poiché anche Internet Information Services (IIS) usa il servizio SSL HTTP, si verificano problemi di interoperabilità significativi di cui è necessario tenere conto se si sceglie di eseguire IIS e [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nello stesso computer. Esaminare la sezione Problemi di interoperabilità con IIS per indicazioni su come risolvere tali problemi.  
  
## <a name="server-certificate-requirements"></a>Requisiti dei certificati server  
 È necessario che nel computer sia installato un certificato server. I certificati client non sono supportati. In Reporting Services non sono disponibili funzionalità per la richiesta, la generazione, il download o l'installazione di un certificato. [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] offre uno snap-in certificati che è possibile usare per richiedere un certificato da un'autorità di certificazione attendibile.  
  
 A scopo di test, è possibile generare un certificato in locale. Se si usano l'utilità **MakeCert** e il comando di esempio come modello, assicurarsi di specificare il nome del server come host e di rimuovere tutte le interruzioni di riga prima di eseguire il comando. Se si esegue il comando in una finestra DOS, può essere necessario aumentare le dimensioni del buffer della finestra per consentire l'inserimento dell'intero comando.  
  
 Se si eseguono IIS e [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nello stesso computer, è possibile usare l'applicazione console IIS Manager per ottenere il certificato installato nel computer. IIS Manager include opzioni per la creazione e l'assemblaggio di un file di richiesta di certificato (con estensione crt) per l'elaborazione successiva da parte di un'autorità di certificazione attendibile. L'autorità di certificazione scelta genererà e restituirà un file di certificato (con estensione cer). È possibile utilizzare la console di gestione IIS per installare il file di certificato nell'archivio locale. Per altre informazioni, vedere [Using SSL to Encrypt Confidential Data](https://go.microsoft.com/fwlink/?LinkId=71123) (Uso di SSL per crittografare dati riservati) nel sito Microsoft Technet.  
  
## <a name="interoperability-issues-with-iis"></a>Problemi di interoperabilità con IIS  
 La presenza di IIS nello stesso computer di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] influirà in modo significativo sulle connessioni SSL a un server di report:  
  
-   Se IIS è installato, è necessario che il servizio World Wide Web (W3SVC) sia sempre in esecuzione. Il servizio SSL HTTP creerà una dipendenza da IIS se rileva che IIS è in esecuzione. Pertanto, il servizio World Wide Web (W3SVC) deve essere in esecuzione ogni volta che IIS e [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] vengono installati nello stesso computer e vengono configurati gli URL del server di report per le connessioni SSL.  
  
-   La disinstallazione di IIS può interrompere temporaneamente il servizio per un URL del server di report associato a SSL. Per questo motivo, si consiglia di riavviare il computer dopo la disinstallazione di IIS.  
  
     Il riavvio del computer è necessario per cancellare tutte le sessioni SSL dalla cache. In alcuni sistemi operativi le sessioni SSL vengono memorizzate nella cache per un massimo di 10 ore. In questo caso, gli URL https:// continuano a funzionare anche dopo la rimozione dell'associazione SSL dalla prenotazione URL in HTTP.SYS. Con il riavvio del computer vengono chiuse tutte le connessioni aperte che utilizzano il canale.  
  
## <a name="bind-ssl-to-a-reporting-services-url-reservation"></a>Associazione di SSL a una prenotazione URL di Reporting Services  
 Nei passaggi seguenti non sono incluse le istruzioni per la richiesta, la generazione, il download o l'installazione di un certificato. È necessario che un certificato sia installato e disponibile per l'uso. Le proprietà del certificato specificate, l'autorità di certificazione da cui lo si ottiene e gli strumenti e le utilità che si utilizzano per richiedere e installare il certificato sono di responsabilità dell'utente.  
  
 Per associare il certificato, è possibile utilizzare lo strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Se il certificato è installato correttamente nell'archivio del computer locale, lo strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] lo rileva e lo visualizza nell'elenco **Certificati SSL** delle pagine **URL servizio Web** e **URL Gestione report** .  
  
### <a name="to-configure-a-report-server-url-for-ssl"></a>Per configurare un URL del server di report per SSL  
  
1.  Avviare lo strumento di configurazione di Reporting Services e connettersi al server di report.  
  
2.  Fare clic su **URL servizio Web**.  
  
3.  Espandere l'elenco di certificati SLL. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] consente di rilevare i certificati di autenticazione server nell'archivio locale. Se è stato installato un certificato che non viene visualizzato nell'elenco, può essere necessario riavviare il servizio. A tale scopo, è possibile usare i pulsanti **Arresta** e **Avvia** nella pagina **Stato server di report** dello strumento di configurazione di Reporting Services.  
  
4.  Selezionare il certificato.  
  
5.  Fare clic su **Applica**.  
  
6.  Fare clic sull'URL per verificarne il funzionamento.  
  
 La configurazione del database del server di report è un requisito per testare l'URL. Se il database del server di report non è ancora stato creato, completare questo passaggio prima di testare l'URL.  
  
 Le prenotazioni URL per Gestione report e per il servizio Web ReportServer vengono configurate in modo indipendente. Se si desidera configurare anche l'accesso a Gestione report tramite un canale crittografato con SSL, continuare con i passaggi seguenti:  
  
1.  Fare clic su **URL Gestione report**.  
  
2.  Fare clic su **Avanzate**.  
  
3.  In **Più identità SSL per Gestione report**fare clic su **Aggiungi**.  
  
4.  Selezionare il certificato desiderato, fare clic su **OK**e quindi su **Applica**.  
  
5.  Fare clic sull'URL per verificarne il funzionamento.  
  
## <a name="how-certificate-bindings-are-stored"></a>Modalità di archiviazione delle associazioni certificato  
 Le associazioni certificato verranno archiviate in HTTP.SYS. Una rappresentazione delle associazioni definite verrà anche archiviata nella sezione `URLReservations` del file RSReportServer.config. Le impostazioni nel file di configurazione sono solo una rappresentazione dei valori effettivi specificati altrove. Non modificare i valori direttamente nel file di configurazione. Le impostazioni di configurazione verranno visualizzate nel file solo dopo che è stato utilizzato lo strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] o il provider WMI (Windows Management Instrumentation, Strumentazione gestione Windows) del server di report per associare un certificato.  
  
> [!NOTE]  
>  Se si configura un'associazione con un certificato SSL in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e successivamente si vuole rimuovere il certificato dal computer, verificare di rimuovere l'associazione da [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] prima di rimuovere il certificato dal computer. In caso contrario, l'associazione non potrà essere rimossa tramite lo strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] o WMI e verrà visualizzato l'errore "Parametro non valido". Se è già stato rimosso il certificato dal computer, è possibile utilizzare lo strumento Httpcfg.exe per rimuovere l'associazione da HTTP.SYS. Per ulteriori informazioni su Httpcfg.exe, vedere la documentazione di Windows.  
  
 Le associazioni SSL sono una risorsa condivisa in Microsoft Windows. Le modifiche apportate da Gestione configurazione [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] o da altri strumenti come Gestione IIS possono influire su altre applicazioni presenti nello stesso computer. Per modificare le associazioni è quindi consigliabile utilizzare lo stesso strumento adoperato per la creazione.  Ad esempio, se le associazioni SSL sono state create mediante Gestione configurazione, è consigliabile utilizzare questo stesso strumento per gestirne il ciclo di vita. Lo stesso concetto vale per la creazione e la gestione delle associazioni mediante Gestione IIS. Se IIS viene installato nel computer prima di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , è consigliabile esaminare la configurazione SSL in IIS prima di configurare [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 Se si rimuovono le associazioni SSL per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] mediante Gestione configurazione Reporting Services, SSL potrebbe non funzionare più per i siti Web di un server in cui è in esecuzione Internet Information Services (IIS) o un altro server HTTP.SYS. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Gestione configurazione rimuove la chiave del Registro di sistema riportata di seguito. Quando si rimuove la chiave del Registro di sistema, viene anche rimossa l'associazione SSL per IIS. Senza questa associazione, SSL non viene fornito per il protocollo HTTPS. Per diagnosticare questo problema, utilizzare Gestione IIS o l'utilità della riga di comando HTTPCFG.exe. Per risolverlo, ripristinare l'associazione SSL per i siti Web in uso mediante Gestione IIS. Per evitare che si verifichi di nuovo, utilizzare Gestione IIS innanzitutto per rimuovere le associazioni SSL e, successivamente, per ripristinare l'associazione per i siti Web desiderati. Per altre informazioni, vedere l'articolo della Knowledge Base [Mancato funzionamento di SSL dopo la rimozione di un'associazione SSL (https://support.microsoft.com/kb/956209/n)](https://support.microsoft.com/kb/956209/n).  
  
## <a name="see-also"></a>Vedi anche  
 [Autenticazione con il server di report](authentication-with-the-report-server.md)   
 [Configurare e amministrare un server di report &#40;modalità nativa SSRS&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)   
 [File di configurazione RSReportServer](../report-server/rsreportserver-config-configuration-file.md)   
 [Reporting Services Configuration Manager &#40;del&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Configurare gli URL del server di report &#40;Gestione configurazione SSRS&#41;](../install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  
