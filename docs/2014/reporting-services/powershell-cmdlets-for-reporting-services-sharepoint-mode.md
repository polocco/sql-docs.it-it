---
title: Cmdlet di PowerShell per Reporting Services modalità SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7835bc97-2827-4215-b0dd-52f692ce5e02
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 79fe1380a38ab9b2d309f0fc6419261e4f13ef8b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "75253259"
---
# <a name="powershell-cmdlets-for-reporting-services-sharepoint-mode"></a>Cmdlet di PowerShell per la modalità SharePoint di Reporting Services
  Quando si installa [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] la modalità SharePoint di, i cmdlet di PowerShell vengono installati per supportare i server di report in modalità SharePoint. I cmdlets riguardano tre categorie di funzionalità.  
  
-   Installazione del proxy e del servizio SharePoint Shared di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
-   Provisioning e gestione delle applicazioni di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] e dei proxy associati.  
  
-   Gestione delle funzionalità di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , ad esempio estensioni e chiavi di crittografia.  
  
||  
|-|  
|[!INCLUDE[applies](../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Modalità SharePoint|  
  
 **In questo argomento sono contenute le sezioni seguenti:**  
  
-   [Riepilogo cmdlet](#bkmk_cmdlet_sum)  
  
-   [Cmdlet del servizio condiviso e del proxy](#bkmk_sharedservice_cmdlets)  
  
-   [Cmdlet dell'applicazione di servizio e del proxy](#bkmk_serviceapp_cmdlets)  
  
-   [Cmdlet di Reporting Services funzionalità personalizzata](#bkmk_ssrsfeatures_cmdlets)  
  
-   [Esempi di base](#bkmk_basic_samples)  
  
-   [Esempi dettagliati](#bkmk_detailedsamples)  
  
    -   [Creare un proxy e un'applicazione di servizio Reporting Services](#bkmk_example_create_service_application)  
  
    -   [Rivedere e aggiornare un'estensione per il recapito di Reporting Services](#bkmk_example_delivery_extension)  
  
    -   [Ottenere e impostare le proprietà del database dell'applicazione Reporting Service, ad esempio timeout database](#bkmk_example_db_properties)  
  
    -   [Elencare le estensioni per i dati di Reporting Services-modalità SharePoint](#bkmk_example_list_data_extensions)  
  
    -   [Modificare ed elencare i proprietari di sottoscrizioni](#bkmk_change_subscription_owner)  
  
##  <a name="cmdlet-summary"></a><a name="bkmk_cmdlet_sum"></a>Riepilogo cmdlet  

 Per eseguire i cmdlet è necessario aprire la shell di gestione SharePoint. È anche possibile usare l'editor dell'interfaccia utente grafica incluso in Microsoft Windows, **Windows PowerShell Integrated Scripting Environment (ISE)**. Per altre informazioni, vedere [Starting Windows PowerShell on Windows Server (Avvio di Windows PowerShell su Windows Server)](https://docs.microsoft.com/powershell/scripting/getting-started/starting-windows-powershell). Nei riepiloghi dei cmdlet seguenti, i riferimenti ai database dell'applicazione di servizio, fanno riferimento a tutti i database creati e usati da [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] un'applicazione di servizio. Sono inclusi i database di configurazione, di avvisi e temporaneo.  

  
 Se quando si digitano gli esempi di PowerShell si visualizza un messaggio di errore simile al seguente:  
  
-   Install-SPRSService: Termine 'Install-SPRSService' non riconosciuto come  
    nome di cmdlet, funzione, programma eseguibile o file script. Verificare l'ortografia del nome, che il percorso sia incluso e corretto, quindi riprovare.  
  
 Si è verificato uno dei problemi seguenti:  
  
-   [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , pertanto non sono presenti i cmdlet di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
-   Il comando di PowerShell è stato eseguito in Windows PowerShell o Windows PowerShell ISE anziché nella shell di gestione di SharePoint. Utilizzare la shell di gestione di SharePoint o aggiungere lo snap-in SharePoint alla finestra di Windows PowerShell con il comando seguente:  
  
    ```powershell
    Add-PSSnapin Microsoft.SharePoint.PowerShell  
    ```  
  
 Per ulteriori informazioni, vedere [utilizzare Windows PowerShell per amministrare SharePoint 2013](https://technet.microsoft.com/library/ee806878.aspx) (https://technet.microsoft.com/library/ee806878.aspx).  
  
#### <a name="to-open-the-sharepoint-management-shell-and-run-cmdlets"></a>Per aprire la shell di gestione di SharePoint ed eseguire i cmdlet  
  
1.  Fare clic sul menu **Start** .  
  
2.  Fare clic sul gruppo **Prodotti Microsoft SharePoint** .  
  
3.  Fare clic su **Shell di gestione SharePoint**.  
  
 Per visualizzare le informazioni della Guida relative alla riga di comando per un cmdlet, usare il comando PowerShell "Get-Help" al prompt dei comandi di PowerShell. Ad esempio:  
  
 `Get-Help Get-SPRSServiceApplicationServers`  
  
###  <a name="shared-service-and-proxy-cmdlets"></a><a name="bkmk_sharedservice_cmdlets"></a> Cmdlet del servizio condiviso e del proxy  
 Nella tabella seguente sono elencati i cmdlet di PowerShell per il servizio SharePoint Shared di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
|Cmdlet|Descrizione|  
|------------|-----------------|  
|Install-SPRSService|Installa e registra, o disinstalla, il servizio SharePoint Shared di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Queste operazioni possono essere eseguite solo nel computer in cui è installato SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in modalità SharePoint. Per l'installazione, vengono eseguite due operazioni:<br /><br /> 1) il [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] servizio viene installato nella farm.<br /><br /> 2) l' [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] istanza del servizio viene installata nel computer corrente.<br /><br /> Per la disinstallazione, vengono eseguite due operazioni:<br />1) il [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] servizio viene disinstallato dal computer corrente.<br />2) il [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] servizio viene disinstallato dalla farm.<br /><br /> <br /><br /> NOTA: se nella farm sono presenti altri computer in cui è installato il servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] oppure se nella farm sono ancora in esecuzione applicazioni di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , viene visualizzato un messaggio di avviso.|  
|Install-SPRSServiceProxy|Installa e registra, o disinstalla, il proxy del servizio Reporting Services nella farm di SharePoint.|  
|Get-SPRSProxyUrl|Ottiene gli URL per l'accesso al servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
|Get-SPRSServiceApplicationServers|Ottiene tutti i server nella farm di SharePoint locale contenenti un'installazione del servizio SharePoint Shared di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Questo cmdlet è utile per gli aggiornamenti di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , per determinare i server in cui viene eseguito il servizio condiviso e pertanto devono essere aggiornati.|  
  
###  <a name="service-application-and-proxy-cmdlets"></a><a name="bkmk_serviceapp_cmdlets"></a> Cmdlet dell'applicazione di servizio e del proxy  
 Nella tabella seguente sono elencati i cmdlet di PowerShell per le applicazioni di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] e i proxy associati.  
  
|Cmdlet|Descrizione|  
|------------|-----------------|  
|Get-SPRSServiceApplication|Ottiene uno o più oggetti dell'applicazione di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
|New-SPRSServiceApplication|Crea una nuova applicazione di servizio Reporting Services e i database associati.<br /><br /> Parametro LogonType: consente di specificare se nel server di report viene utilizzato un account del pool di applicazioni SSRS o un account di accesso di SQL Server per accedere al database del server di report. I possibili valori sono i seguenti:<br /><br /> 0 Autenticazione di Windows<br /><br /> 1 SQL Server<br /><br /> 2 Account pool applicazioni (impostazione predefinita)|  
|Remove-SPRSServiceApplication|Rimuove l'applicazione di servizio Reporting Services specificata. Vengono rimossi anche i database associati.|  
|Set-SPRSServiceApplication|Modifica le proprietà di un'applicazione di servizio Reporting Services esistente.|  
|New-SPRSServiceApplicationProxy|Crea un nuovo proxy dell'applicazione di servizio Reporting Services.|  
|Get-SPRSServiceApplicationProxy|Ottiene uno o più proxy dell'applicazione di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
|Dismount-SPRSDatabase|Smonta i database dell'applicazione di servizio per un'applicazione di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
|Remove-SPRSDatabase|Rimuove i database dell'applicazione di servizio per un'applicazione di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
|Set-SPRSDatabase|Imposta le proprietà dei database associati a un'applicazione di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
|Mount-SPRSDatabase|Monta i database per un'applicazione di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|  
|New-SPRSDatabase|Crea nuovi database dell'applicazione di servizio per l'applicazione di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] specificata.|  
|Get-SPRSDatabaseCreationScript|Visualizza lo script di creazione del database per un'applicazione di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . È quindi possibile eseguire lo script in SQL Server Management Studio.|  
|Get-SPRSDatabase|Ottiene uno o più database dell'applicazione di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Usare il comando per ottenere l'ID del database dell'applicazione di servizio in modo da potere usare il cmdlet Set-SPRSDatabase per modificare le proprietà, ad esempio `querytimeout`. Vedere l'esempio nell'argomento [Ottenere e impostare le proprietà del database dell'applicazione Reporting Service, ad esempio timeout database](#bkmk_example_db_properties).|  
|Get-SPRSDatabaseRightsScript|Visualizza lo script diritti del database per un'applicazione di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Vengono richiesti l'utente desiderato e il database, quindi viene restituita l'istruzione Transact-SQL che è possibile eseguire per modificare le autorizzazioni. È quindi possibile eseguire lo script in SQL Server Management Studio.|  
|Get-SPRSDatabaseUpgradeScript|Visualizza uno script di aggiornamento del database. Lo script consente di aggiornare i database dell'applicazione di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] alla versione del database dell'installazione di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] corrente.|  
  
###  <a name="reporting-services-custom-functionality-cmdlets"></a><a name="bkmk_ssrsfeatures_cmdlets"></a>Cmdlet di Reporting Services funzionalità personalizzata  
  
|Cmdlet|Descrizione|  
|------------|-----------------|  
|Update-SPRSEncryptionKey|Aggiorna la chiave di crittografia per l'applicazione di servizio Reporting Services specificata ed esegue di nuovo la crittografia dei dati.|  
|Restore-SPRSEncryptionKey|Ripristina una chiave di crittografia di cui in precedenza è stato eseguito il backup per un'applicazione di servizio Reporting Services.|  
|Remove-SPRSEncryptedData|Elimina i dati crittografati per l'applicazione di servizio Reporting Services specificata.|  
|Backup-SPRSEncryptionKey|Esegue il backup della chiave di crittografia per l'applicazione di servizio Reporting Services specificata.|  
|New-SPRSExtension|Registra una nuova estensione con un'applicazione di servizio Reporting Services.|  
|Set-SPRSExtension|Imposta le proprietà di un'estensione di Reporting Services esistente.|  
|Remove-SPRSExtension|Rimuove un'estensione da un'applicazione di servizio Reporting Services.|  
|Get-SPRSExtension|Ottiene una o più estensioni di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] per un'applicazione di servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .<br /><br /> I valori validi sono:<br /><br /> **Recapito**<br /><br /> **DeliveryUI**<br /><br /> **Rendering**<br /><br /> **Dati**<br /><br /> **Sicurezza**<br /><br /> **autenticazione**<br /><br /> **EventProcessing**<br /><br /> **ReportItems**<br /><br /> **Progettazione**<br /><br /> **ReportItemDesigner**<br /><br /> **ReportItemConverter**<br /><br /> **ReportDefinitionCustomization**|  
|Get-SPRSSite|Ottiene i siti di SharePoint in base all'eventuale abilitazione della funzionalità "ReportingService". Per impostazione predefinita, vengono restituiti i siti in cui la funzionalità "ReportingService" è abilitata.|  
  
##  <a name="basic-samples"></a><a name="bkmk_basic_samples"></a>Esempi di base  
 Restituire un elenco di cmdlet contenenti "SPRS" nel nome. Si tratta dell'elenco completo dei cmdlet di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
```powershell
Get-command -noun *SPRS*  
```  
  
 In alternativa, con un livello leggermente maggiore di dettaglio, inoltrare tramite pipe in un file di testo denominato commandlist.txt.  
  
```powershell
Get-Command -Noun *SPRS* | Select name, definition | Format-List | Out-File c:\commandlist.txt  
```  
  
 Installare il proxy del servizio e il servizio SharePoint di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
```powershell
Install-SPRSService  
```  
  
```powershell
Install-SPRSServiceProxy  
```  
  
 Avviare il servizio [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
```powershell
Get-SPServiceInstance -all | where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
```  
  
 Digitare il comando seguente dalla Shell di gestione di SharePoint per ottenere un elenco filtrato di righe del file di log. Con il comando verranno filtrate le righe contenenti "ssrscustomactionerror". In questo esempio viene analizzato il file di log creato al momento dell'installazione di rssharepoint.msi.  
  
```powershell
Get-Content -Path C:\Users\testuser\AppData\Local\Temp\rs_sp_0.log | Select-String "ssrscustomactionerror"  
```  
  
##  <a name="detailed-samples"></a><a name="bkmk_detailedsamples"></a>Esempi dettagliati  
 Oltre agli esempi seguenti, vedere la sezione "script di Windows PowerShell" nell'argomento [script di Windows PowerShell per i passaggi 1-4](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md#bkmk_full_script).  
  
###  <a name="create-a-reporting-services-service-application-and-proxy"></a><a name="bkmk_example_create_service_application"></a>Creare un'applicazione di servizio Reporting Services e un proxy  
 Questo script di esempio consente di completare le attività seguenti:  
  
1.  Creare un proxy e un'applicazione di servizio Reporting Services. Per lo script si presuppone che il pool di applicazioni "My App Pool" esista già.  
  
2.  Aggiungere il proxy al gruppo di proxy predefiniti.  
  
3.  Concedere all'applicazione di servizio l'accesso al database del contenuto dell'applicazione Web sulla porta 80. Lo script presuppone che ilhttp://sitenamesito "" esista già.  
  
```powershell
# Create service application and service application proxy  
$appPool = Get-SPServiceApplicationPool "My App Pool"  
$serviceApp = New-SPRSServiceApplication "My RS Service App" -ApplicationPool $appPool  
$serviceAppProxy = New-SPRSServiceApplicationProxy -Name "My RS Service App Proxy" -ServiceApplication $serviceApp  
  
# Add service application proxy to default proxy group.  Any web application that uses the default proxy group will now be able to use this service application.  
Get-SPServiceApplicationProxyGroup -default | Add-SPServiceApplicationProxyGroupMember -Member $serviceAppProxy  
  
# Grant application pool account access to the port 80 web application's content database.  
$webApp = Get-SPWebApplication "http://sitename"  
$appPoolAccountName = $appPool.ProcessAccount.LookupName()  
$webApp.GrantAccessToProcessIdentity($appPoolAccountName)
```  
  
###  <a name="review-and-update-a-reporting-services-delivery-extension"></a><a name="bkmk_example_delivery_extension"></a>Esaminare e aggiornare un'estensione per il recapito Reporting Services  
 Nell'esempio di script di PowerShell seguente viene aggiornata la configurazione dell'estensione per il recapito tramite posta elettronica del server di report per l'applicazione di servizio denominata `My RS Service App`. Aggiornare i valori per il server SMTP (`<email server name>`) e l'alias di posta elettronica FROM (`<your FROM email address>`).  
  
```powershell
$app = Get-SPRSServiceApplication -Name "My RS Service App"  
$emailCfg = Get-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml
$emailXml = [xml]$emailCfg
$emailXml.SelectSingleNode("//SMTPServer").InnerText = "<email server name>"  
$emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
$emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
$emailXml.SelectSingleNode("//From").InnerText = '<your FROM email address>'  
Set-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
```  
  
 Nell'esempio precedente, se non si conosce il nome esatto dell'applicazione di servizio, è possibile riscrivere la prima istruzione per ottenere l'applicazione di servizio in base a una ricerca del nome parziale. Ad esempio:  
  
```powershell
$app = Get-SPRSServiceApplication | Where {$_.name -like " ssrs_testapp *"}  
```  
  
 Lo script seguente restituisce i valori di configurazione correnti per l'estensione per il recapito via posta elettronica del server di report per l'applicazione di servizio denominata "Reporting Services Application". Il primo passaggio consente di impostare il valore della variabile $app sull'oggetto applicazione di servizio denominato "My RS Service App"  
  
 La seconda istruzione consente di ottenere l'estensione per il recapito "Report Server Email" per l'oggetto applicazione di servizio nella variabile $app e di selezionare configurationXML  
  
```powershell
$app = Get-SPRSServiceapplication -Name "Reporting Services Application"  
Get-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml  
```  
  
 È inoltre possibile riscrivere le due istruzioni sopra riportate come un'unica istruzione:  
  
```powershell
Get-SPRSServiceApplication -Name "Reporting Services Application" | Get-SPRSExtension -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml  
```  
  
###  <a name="get-and-set-properties-of-the-reporting-servicea-application-database-for-example-database-timeout"></a><a name="bkmk_example_db_properties"></a>Ottenere e impostare le proprietà del database dell'applicazione Reporting Service, ad esempio timeout database  
 L'esempio seguente restituisce innanzitutto un elenco dei database e delle proprietà in modo da potere determinare il GUID del database da fornire al comando set. Per un elenco completo delle proprietà, usare `Get-SPRSDatabase | format-list`.  
  
```powershell
Get-SPRSDatabase | Select id, querytimeout,connectiontimeout, status, server, ServiceInstance
```  
  
 Di seguito è riportato un esempio dell'output. Determinare l'ID del database da modificare e usare l'ID nel cmdlet SET.  
  
-   `Id                : 56f8d1bc-cb04-44cf-bd41-a873643c5a14`  
  
     `QueryTimeout      : 120`  
  
     `ConnectionTimeout : 15`  
  
     `Status            : Online`  
  
     `Server            : SPServer Name=uetestb01`  
  
     `ServiceInstance   : SPDatabaseServiceInstance`  
  
```powershell
Set-SPRSDatabase -Identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 -QueryTimeout 300  
```  
  
 Per verificare il valore impostato, eseguire di nuovo il cmdlet GET.  
  
```powershell
Get-SPRSDatabase -Identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 | Select id, querytimeout,connectiontimeout, status, server, ServiceInstance  
```  
  
###  <a name="list-reporting-services-data-extensions---sharepoint-mode"></a><a name="bkmk_example_list_data_extensions"></a>Elencare le estensioni per i dati di Reporting Services-modalità SharePoint  
 L'esempio seguente esegue il ciclo di ogni applicazione di servizio di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ed elenca le estensioni per i dati per ogni applicazione.  
  
```powershell
$apps = Get-SPRSServiceApplication  
foreach ($app in $apps)
{  
Write-host -ForegroundColor "yellow" Service App Name $app.Name  
Get-SPRSExtension -identity $app -ExtensionType "Data" | select name, extensiontype | Format-Table -AutoSize  
}  
```  
  
 **Output di esempio:**  
  
-   `Name           ExtensionType`  
  
     `----           -------------`  
  
     `SQL                     Data`  
  
     `SQLAZURE                Data`  
  
     `SQLPDW                  Data`  
  
     `OLEDB                   Data`  
  
     `OLEDB-MD                Data`  
  
     `ORACLE                  Data`  
  
     `ODBC                    Data`  
  
     `XML                     Data`  
  
     `SHAREPOINTLIST          Data`  
  
###  <a name="change-and-list-subscription-owners"></a><a name="bkmk_change_subscription_owner"></a>Modificare ed elencare i proprietari delle sottoscrizioni  
 Vedere [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Usare PowerShell per modificare ed elencare i proprietari delle sottoscrizioni Reporting Services ed eseguire una sottoscrizione](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md)   
 [Elenco di controllo: usare PowerShell per verificare PowerPivot per SharePoint](https://docs.microsoft.com/analysis-services/instances/install-windows/checklist-use-powershell-to-verify-power-pivot-for-sharepoint)   
 [Script di PowerShell di gestione di SharePoint nel sito CodePlex](https://sharepointpsscripts.codeplex.com/)   
