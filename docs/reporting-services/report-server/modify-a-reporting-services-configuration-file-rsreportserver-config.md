---
title: Modificare un file di configurazione di Reporting Services (RSreportserver.config) | Microsoft Docs
description: Informazioni su come modificare i file di configurazione in Reporting Services per aggiungere o configurare impostazioni avanzate. Alcune impostazioni sono solo per uso interno. Procedere con cautela.
ms.date: 03/15/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
ms.assetid: 958ef51f-2699-4cb2-a92e-3b4322e36a30
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 315f1129f6c83f36de02efebf4eb4ec58cb4c48f
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547949"
---
# <a name="modify-a-reporting-services-configuration-file-rsreportserverconfig"></a>Modify a Reporting Services Configuration File (RSreportserver.config)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] le impostazioni dell'applicazione vengono archiviate in un set di file di configurazione. Durante l'installazione vengono creati i file di configurazione per ogni istanza del server di report installata. All'interno di ogni file, i valori vengono impostati in questa fase o nel momento in cui si utilizzano strumenti e applicazioni per configurare un server per l'esecuzione di operazioni. In alcuni casi, è necessario modificare direttamente un file per aggiungere o configurare impostazioni avanzate. Le impostazioni di configurazione sono specificate come elementi o attributi XML. Se si conoscono il linguaggio XML e i file di configurazione, è possibile utilizzare un editor di testo o di codice per modificare le impostazioni definibili dall'utente.  
  
 Alcune impostazioni di configurazione possono essere impostate solo tramite uno strumento specifico. Impostazioni che contengono valori crittografati devono essere modificate ad esempio tramite lo strumento di configurazione di Reporting Services, il programma di installazione o l'utilità della riga di comando **rsconfig** . Per eseguire questi strumenti, è necessario essere membro del gruppo Administrators locale.  
  
> [!IMPORTANT]
>  Prestare attenzione in caso di modifiche al file di configurazione. Se si modifica un'impostazione riservata per l'uso interno, l'installazione potrebbe essere disabilitata. Non è in genere consigliabile modificare le impostazioni di configurazione, a meno che non sia necessario risolvere un problema specifico. Per altre informazioni sulle impostazioni sicure da modificare, vedere [File di configurazione RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) o [File di configurazione RSReportDesigner](../../reporting-services/report-server/rsreportdesigner-configuration-file.md). Per altre informazioni sui file di configurazione, vedere la documentazione del prodotto [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] .  
  
 In questo argomento  
  
-   [Lettura e utilizzo di valori di configurazione](#bkmk_read_values)  
  
-   [Informazioni sui valori predefiniti](#bkmk_default_values)  
  
-   [Eliminazione delle impostazioni di configurazione](#bkmk_delete_config_settings)  
  
-   [Per modificare un file di configurazione di Reporting Services](#bkmk_edit_configuation_file)  
  
##  <a name="reading-and-using-configuration-values"></a><a name="bkmk_read_values"></a> Lettura e utilizzo di valori di configurazione  
 In un server di report i file di configurazione vengono letti all'avvio del servizio e tutte le volte in cui il file di configurazione viene salvato. I valori nuovi e quelli modificati diventano effettivi in un nuovo dominio applicazione dopo che quello precedente è scaduto. Tutte le volte in cui è possibile, le richieste attualmente in corso nel dominio applicazione corrente vengono completate. Per alcune impostazioni è necessario tuttavia che venga eseguita immediatamente un'operazione di riciclo del dominio applicazione. In questo caso tutte le richieste attualmente in corso vengono riavviate in un nuovo dominio applicazione.  
  
 Se il server di report rileva un valore non valido, nel registro applicazioni di Windows viene inserito un errore a seconda del quale il server di report non si avvia o utilizza un valore predefinito:  
  
-   Se l'errore è causato da XML con formato non valido, il server di report non verrà avviato. Se il server di report è in esecuzione quando si verifica l'errore, il file di configurazione non valido verrà ignorato finché il server di report non verrà riavviato o fino a quando il dominio applicazione non verrà riciclato. Dopo aver rilevato l'errore, il server di report non verrà avviato.  
  
-   Se l'errore è un valore di configurazione non valido, il server utilizzerà valori predefiniti interni e registrerà un errore nei file di log di traccia. In un numero ridotto di casi non sono disponibili valori predefiniti interni e di conseguenza il server restituirà l'errore rsServerConfigurationError se l'impostazione di configurazione non valida è critica per le operazioni del server. Gli errori relativi a impostazioni mancanti o non valide vengono restituiti all'applicazione client in una pagina degli errori HTML e inseriti nel registro eventi.  
  
 Tutte le modifiche apportate al file di configurazione, incluse quelle con esito positivo, vengono registrate nel file di log di traccia del server di report. Nel registro eventi applicazioni vengono inseriti solo gli errori.  
  
##  <a name="about-default-values"></a><a name="bkmk_default_values"></a> Informazioni sui valori predefiniti  
 La maggior parte delle impostazioni di configurazione dispone di valori predefiniti specificati internamente nel server di report che li utilizzerà se un valore definito dall'utente non è valido o non è stato specificato. Se è necessario utilizzare un valore predefinito a causa di un'impostazione non valida, nel file di log di traccia verrà registrato un errore.  
  
##  <a name="deleting-configuration-settings"></a><a name="bkmk_delete_config_settings"></a> Eliminazione delle impostazioni di configurazione  
 Per impostazioni di configurazione cui sono associati valori predefiniti, la rimozione dell'impostazione dal file di configurazione non ha alcun effetto. La maggior parte delle impostazioni di configurazione viene effettivamente definita e configurata internamente. Se si elimina un elemento dal file di configurazione, la copia interna è ancora disponibile e utilizza il valore predefinito specificato.  
  
##  <a name="to-edit-a-reporting-services-configuration-file"></a><a name="bkmk_edit_configuation_file"></a> Per modificare un file di configurazione di Reporting Services  
  
1.  Individuare il file di configurazione da modificare:  
  
    -   **RSReportServer.config** si trova nella cartella seguente:  
  
        ```  
        C:\Program Files\Microsoft SQL Server\MSRS13.MSSQLSERVER\Reporting Services\ReportServer  
        ```  
        
        ||  
        |-|  
        |**[!INCLUDE[applies](../../includes/applies-md.md)]**  Technical Preview di gennaio 2017 dei report di Power BI in SQL Server Reporting Services|
        
        ```  
        C:\Program Files\Microsoft SQL Server Reporting Services\RSServer\ReportServer
        ```
  
    -   **RSReportServerServices.exe.config** si trova nella cartella seguente:  
    
        > [!NOTE] 
        > Non è disponibile con la Technical Preview di gennaio 2017 dei report di Power BI in SQL Server Reporting Services.
  
        ```  
        C:\Program Files\Microsoft SQL Server\MSRS13.MSSQLSERVER\Reporting Services\ReportServer\bin  
        ```  
  
    -   **RSReportDesigner.config** si trova nella cartella seguente:  
  
        ```  
        C:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies  
        ```  
  
2.  Salvare una copia del file nel caso in cui sia necessario eseguire il rollback delle modifiche.  
  
3.  Aprire il file originale in Blocco note o un editor del codice. Non utilizzare Textpad poiché imposta la lunghezza del file prima del salvataggio, provocando la registrazione nel file di log di traccia di un errore dovuto a un carattere non valido.  
  
4.  Digitare l'elemento o il valore da aggiungere o utilizzare. Poiché gli elementi rispettano la distinzione tra maiuscole e minuscole, quando si aggiunge un elemento verificare di utilizzare le lettere nella forma corretta. Istruzioni specifiche per la modifica di file di configurazione sono disponibili se si personalizzano l'estensione per il rendering, le estensioni di autenticazione o quelle per l'elaborazione dei dati:  
  
    -   [Autenticazione con il server di report](../../reporting-services/security/authentication-with-the-report-server.md)  
  
    -   [Configurare il portale Web per il passaggio di cookie di autenticazione personalizzati](../../reporting-services/security/configure-the-web-portal-to-pass-custom-authentication-cookies.md)
  
    -   [Personalizzare i parametri di estensione per il rendering in RSReportServer.config.](../../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)  
  
5.  Salvare il file.  
  
6.  Esaminare i file di log di traccia per controllare che non si siano verificati errori. Se sono presenti condizioni di errore, un'impostazione o il relativo valore è stato specificato in modo non corretto. Rivedere il [File di configurazione RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md) per i valori validi per qualsiasi impostazione che provoca un errore. Per altre informazioni su come visualizzare i log di traccia, vedere [Log di traccia del servizio del server di report](../../reporting-services/report-server/report-server-service-trace-log.md).  
  
## <a name="see-also"></a>Vedere anche  
 [File di configurazione RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [File di configurazione ReportingServicesService](../../reporting-services/report-server/reportingservicesservice-configuration-file.md)   
 [RSReportDesigner - file di configurazione](../../reporting-services/report-server/rsreportdesigner-configuration-file.md)   
 [Distribuzione di un'estensione per l'elaborazione dati](../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)   
 [Distribuzione di un'estensione per il recapito](../../reporting-services/extensions/delivery-extension/deploying-a-delivery-extension.md)   
 [Distribuzione di un'estensione per il rendering](../../reporting-services/extensions/rendering-extension/deploying-a-rendering-extension.md)   
 [File di configurazione di Reporting Services](../../reporting-services/report-server/reporting-services-configuration-files.md)  
  
  
