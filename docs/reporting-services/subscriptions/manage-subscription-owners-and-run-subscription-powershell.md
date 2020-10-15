---
title: Gestire i proprietari di sottoscrizioni ed eseguire la sottoscrizione - PowerShell | Microsoft Docs
description: Informazioni su come trasferire a livello di programmazione la proprietà di una sottoscrizione di Reporting Services da un utente a un altro.
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: subscriptions
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.custom: ''
ms.date: 01/16/2020
ms.openlocfilehash: b0174f0b7705c9a7c7c678782a4b17fb4a1a74af
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/13/2020
ms.locfileid: "91985887"
---
# <a name="manage-subscription-owners-and-run-subscription---powershell"></a>Gestire i proprietari di sottoscrizioni ed eseguire la sottoscrizione - PowerShell

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)]

A partire da [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è possibile trasferire a livello di programmazione la proprietà di una sottoscrizione [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] da un utente a un altro. In questo argomento sono disponibili alcuni script di Windows PowerShell che possono essere usati per modificare o semplicemente elencare la proprietà delle sottoscrizioni. Ogni esempio include sintassi di esempio per la modalità nativa e la modalità SharePoint. Dopo la modifica del proprietario, la sottoscrizione sarà eseguita nel contesto di protezione del nuovo proprietario e nel campo User!UserID nel report sarà visualizzato il valore relativo al nuovo proprietario. Per altre informazioni sul modello a oggetti chiamato dagli esempi di PowerShell, vedere <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A>  

![Contenuto correlato di PowerShell](/analysis-services/analysis-services/instances/install-windows/media/rs-powershellicon.jpg "Contenuto correlato di PowerShell")

##  <a name="in-this-topic"></a><a name="bkmk_top"></a> Contenuto dell'argomento:
  
- [Come usare gli script](#bkmk_how_to)  
  
- [Script: elencare la proprietà di tutte le sottoscrizioni](#bkmk_list_ownership_all)  
  
- [Script: elencare tutte le sottoscrizioni di proprietà di un utente specifico](#bkmk_list_all_one_user)  
  
- [Script: modificare la proprietà per tutte le sottoscrizioni appartenenti a un utente specifico](#bkmk_change_all)  
  
- [Script: elencare tutte le sottoscrizioni associate a un report specifico](#bkmk_list_for_1_report)  
  
- [Script: cambiare la proprietà di una sottoscrizione specifica](#bkmk_change_all_1_subscription)  
  
- [Script: eseguire (attivare) una singola sottoscrizione](#bkmk_run_1_subscription)  
  
## <a name="how-to-use-the-scripts"></a><a name="bkmk_how_to"></a> Come usare gli script
  
### <a name="permissions"></a>Autorizzazioni

In questa sezione sono riepilogati i livelli di autorizzazione necessari per usare ogni metodo della modalità nativa e della modalità SharePoint di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Gli script in questo argomento usano i metodi seguenti di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] :  
  
- [Metodo ReportingService2010.ListSubscriptions](/dotnet/api/reportservice2010.reportingservice2010.listsubscriptions)  
  
- [Metodo ReportingService2010.ChangeSubscriptionOwner](/dotnet/api/reportservice2010.reportingservice2010.changesubscriptionowner)  
  
- [ReportingService2010.ListChildren](/dotnet/api/reportservice2010.reportingservice2010.listchildren)  
  
- Il metodo [ReportingService2010.FireEvent](/dotnet/api/reportservice2010.reportingservice2010.fireevent) è usato solo nell'ultimo script per attivare l'esecuzione di una sottoscrizione specifica. Se non si prevede di usare tale sottoscrizione, è possibile ignorare i requisiti relativi alle autorizzazioni per il metodo FireEvent.  
  
**Modalità nativa:**
  
- Elenco sottoscrizioni: [Enumerazione ReportOperation](/dotnet/api/microsoft.reportingservices.interfaces.reportoperation) sul report E (l'utente è proprietario della sottoscrizione) O ReadAnySubscription.  
  
- Modifica sottoscrizioni: l'utente deve essere membro del gruppo BUILTIN\Administrators  
  
- Elenco figli: ReadProperties su Item  
  
- Evento di attivazione: GenerateEvents (System)  
  
 **Modalità SharePoint:**
  
- Elenco sottoscrizioni: ManageAlerts O [CreateAlerts](/previous-versions/office/sharepoint-server/ms412690(v=office.15)) sul report E l'utente è proprietario della sottoscrizione e la sottoscrizione è a tempo determinato.  
  
- Modifica sottoscrizioni: ManageWeb  
  
- Elenco figli: ViewListItems  
  
- Evento di attivazione: ManageWeb  
  
 Per altre informazioni, vedere [Confrontare ruoli e attività di Reporting Services con autorizzazioni e gruppi di SharePoint](../../reporting-services/security/reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md).  
  
### <a name="script-usage"></a>Uso degli script

**Creare file script (con estensione ps1)**
  
1. Creare una cartella con nome **c:\scripts**. Se si sceglie una cartella diversa, modificare il nome della cartella usato nelle istruzioni di esempio della sintassi da riga di comando.  
  
2. Creare un file di testo per ogni script e salvare i file nella cartella c:\scripts. Quando si creano i file con estensione ps1, usare il nome di ogni esempio di sintassi da riga di comando.  
  
3. Aprire un prompt dei comandi con privilegi di amministratore.  
  
4. Eseguire ogni file script, usando l'esempio di sintassi da riga di comando disponibile in ogni esempio.  
  
**Ambienti testati**
  
 Gli script in questo argomento sono stati testati in PowerShell versione 3 e con le versioni seguenti di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]:  
  
- [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
- [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
- [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
## <a name="script-list-the-ownership-of-all-subscriptions"></a><a name="bkmk_list_ownership_all"></a> Script: elencare la proprietà di tutte le sottoscrizioni

Questo script permette di elencare tutte le sottoscrizioni in un sito. È possibile usare questo script per testare la connessione o verificare il percorso del report e l'ID di sottoscrizione da usare in altri script. Questo script è utile anche per la semplice verifica delle sottoscrizioni esistenti e dei relativi proprietari.  
  
 **Sintassi in modalità nativa:**
  
```powershell
powershell c:\scripts\ListAll_SSRS_Subscriptions.ps1 "[server]/reportserver" "/"  
```  
  
 **Sintassi in modalità SharePoint:**
  
```powershell
powershell c:\scripts\ListAll_SSRS_Subscriptions.ps1 "[server]/_vti_bin/reportserver" "https://[server]"  
```  
  
 **Script:**
  
```
# Parameters  
#    server   - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)  
  
Param(  
    [string]$server,  
    [string]$site  
   )  
  
$rs2010 += New-WebServiceProxy -Uri "https://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
$subscriptions += $rs2010.ListSubscriptions($site); # use "/" for default native mode site  
  
Write-Host " "  
Write-Host "----- $server's Subscriptions: "  
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted, Status  
```  
  
> [!TIP]  
> Per verificare gli URL del sito in modalità SharePoint, usare il cmdlet **Get-SPSite**di SharePoint. Per altre informazioni, vedere [Get-SPSite](https://msdn.microsoft.com/library/ff607950\(v=office.15\).aspx).  
  
##  <a name="script-list-all-subscriptions-owned-by-a-specific-user"></a><a name="bkmk_list_all_one_user"></a> Script: elencare tutte le sottoscrizioni di proprietà di un utente specifico

Questo script permette di elencare tutte le sottoscrizioni di proprietà di un utente specifico. È possibile usare questo script per testare la connessione o verificare il percorso del report e l'ID di sottoscrizione da usare in altri script. Questo script è utile se un utente abbandona l'organizzazione e si vuole verificare le sottoscrizioni appartenenti a tale utente, in modo da potere modificare il proprietario o eliminare la sottoscrizione.  
  
 **Sintassi in modalità nativa:**
  
```powershell
powershell c:\scripts\ListAll_SSRS_Subscriptions4User.ps1 "[Domain]\[user]" "[server]/reportserver" "/"  
```  
  
**Sintassi in modalità SharePoint:**
  
```powershell
powershell c:\scripts\ListAll_SSRS_Subscriptions4User.ps1 "[Domain]\[user]"  "[server]/_vti_bin/reportserver" "https://[server]"  
```  
  
**Script:**
  
```
# Parameters:  
#    currentOwner - DOMAIN\USER that owns the subscriptions you wish to change  
#    server        - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)  
#    site        - use "/" for default native mode site  
Param(  
    [string]$currentOwner,  
    [string]$server,  
    [string]$site  
)  
  
$rs2010 = New-WebServiceProxy -Uri "https://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
$subscriptions += $rs2010.ListSubscriptions($site);  
  
Write-Host " "  
Write-Host " "  
Write-Host "----- $currentOwner's Subscriptions: "  
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status | where {$_.owner -eq $currentOwner}  
```  
  
## <a name="script-change-ownership-for-all-subscriptions-owned-by-a-specific-user"></a><a name="bkmk_change_all"></a> Script: modificare la proprietà per tutte le sottoscrizioni appartenenti a un utente specifico

Questo script permette di cambiare la proprietà per tutte le sottoscrizioni appartenenti a un utente specifico, impostando il parametro relativo al nuovo proprietario.  
  
**Sintassi in modalità nativa:**  
  
```powershell
powershell c:\scripts\ChangeALL_SSRS_SubscriptionOwner.ps1 "[Domain]\current owner]" "[Domain]\[new owner]" "[server]/reportserver"  
```  
  
**Sintassi in modalità SharePoint:**  
  
```powershell
powershell c:\scripts\ChangeALL_SSRS_SubscriptionOwner.ps1 "[Domain]\{current owner]" "[Domain]\[new owner]" "[server]/_vti_bin/reportserver"  
```  
  
**Script:**  
  
```
# Parameters:  
#    currentOwner - DOMAIN\USER that owns the subscriptions you wish to change  
#    newOwner      - DOMAIN\USER that will own the subscriptions you wish to change  
#    server        - server and instance name (e.g. myserver/reportserver, myserver/reportserver_db2, myserver/_vti_bin/reportserver)
  
Param(  
    [string]$currentOwner,  
    [string]$newOwner,  
    [string]$server  
)  
  
$rs2010 = New-WebServiceProxy -Uri "https://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
$items = $rs2010.ListChildren("/", $true);  
  
$subscriptions = @();  
  
ForEach ($item in $items)  
{  
    if ($item.TypeName -eq "Report")  
    {  
        $curRepSubs = $rs2010.ListSubscriptions($item.Path);  
        ForEach ($curRepSub in $curRepSubs)  
        {  
            if ($curRepSub.Owner -eq $currentOwner)  
            {  
                $subscriptions += $curRepSub;  
            }  
        }  
    }  
}  
  
Write-Host " "  
Write-Host " "  
Write-Host -foregroundcolor "green" "-----  $currentOwner's Subscriptions changing ownership to $newOwner : "  
$subscriptions | select SubscriptionID, Owner, Path, Description,  Status  | format-table -AutoSize  
  
ForEach ($sub in $subscriptions)  
{  
    $rs2010.ChangeSubscriptionOwner($sub.SubscriptionID, $newOwner);  
}  
  
$subs2 = @();  
  
ForEach ($item in $items)  
{  
    if ($item.TypeName -eq "Report")  
    {  
        $subs2 += $rs2010.ListSubscriptions($item.Path);  
    }  
}  
```  
  
## <a name="script-list-all-subscriptions-associated-with-a-specific-report"></a><a name="bkmk_list_for_1_report"></a> Script: elencare tutte le sottoscrizioni associate a un report specifico  

Questo script permette di elencare tutte le sottoscrizioni associate a un report specifico. La sintassi del percorso del report è diversa in modalità SharePoint, che necessita di un URL completo. Nell'esempio di sintassi il nome usato per il report è "title only", che include uno spazio e quindi deve essere racchiuso da virgolette semplici.  
  
**Sintassi in modalità nativa:**  
  
```powershell
powershell c:\scripts\List_SSRS_One_Reports_Subscriptions.ps1 "[server]/reportserver" "'/reports/title only'" "/"  
```  
  
**Sintassi in modalità SharePoint:**  
  
```powershell
powershell c:\scripts\List_SSRS_One_Reports_Subscriptions.ps1 "[server]/_vti_bin/reportserver"  "'https://[server]/shared documents/title only.rdl'" "https://[server]"  
```  
  
**Script:**  
  
```
# Parameters:  
#    server      - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)  
#    reportpath  - path to report in the report server, including report name e.g. /reports/test report >> pass in  "'/reports/title only'"  
#    site        - use "/" for default native mode site  
Param  
(  
      [string]$server,  
      [string]$reportpath,  
      [string]$site  
)  
  
$rs2010 = New-WebServiceProxy -Uri "https://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
$subscriptions += $rs2010.ListSubscriptions($site);  
  
Write-Host " "  
Write-Host " "  
Write-Host "----- $reportpath 's Subscriptions: "  
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status | where {$_.path -eq $reportpath}  
```  
  
## <a name="script-change-ownership-of-a-specific-subscription"></a><a name="bkmk_change_all_1_subscription"></a> Script: cambiare la proprietà di una sottoscrizione specifica  
 Questo script permette di cambiare la proprietà di una sottoscrizione specifica. La sottoscrizione è identificata dal valore SubscriptionID passato nello script. È possibile usare uno degli script per elencare le sottoscrizioni per determinare il valore SubscriptionID corretto.  
  
 **Sintassi in modalità nativa:**  
  
```powershell
powershell c:\scripts\Change_SSRS_Owner_One_Subscription.ps1 "[Domain]\[new owner]" "[server]/reportserver" "/" "ac5637a1-9982-4d89-9d69-a72a9c3b3150"  
```  
  
 **Sintassi in modalità SharePoint:**  
  
```powershell
powershell c:\scripts\Change_SSRS_Owner_One_Subscription.ps1 "[Domain]\[new owner]" "[server]/_vti_bin/reportserver" "https://[server]" "9660674b-f020-453f-b1e3-d9ba37624519"  
```  
  
 **Script:**  
  
```
# Parameters:  
#    newOwner       - DOMAIN\USER that will own the subscriptions you wish to change  
#    server         - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)  
#    site        - use "/" for default native mode site  
#    subscriptionID - guid for the single subscription to change  
  
Param(  
    [string]$newOwner,  
    [string]$server,  
    [string]$site,  
    [string]$subscriptionid  
   )  
$rs2010 = New-WebServiceProxy -Uri "https://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential;  
  
$subscription += $rs2010.ListSubscriptions($site) | where {$_.SubscriptionID -eq $subscriptionid};  
  
Write-Host " "  
Write-Host "----- $subscriptionid's Subscription properties: "  
$subscription | select Path, report, Description, SubscriptionID, Owner, Status  
  
$rs2010.ChangeSubscriptionOwner($subscription.SubscriptionID, $newOwner)  
  
#refresh the list  
$subscription = $rs2010.ListSubscriptions($site) | where {$_.SubscriptionID -eq $subscriptionid}; # use "/" for default native mode site  
Write-Host "----- $subscriptionid's Subscription properties: "  
$subscription | select Path, report, Description, SubscriptionID, Owner, Status  
```  
  
## <a name="script-run-fire-a-single-subscription"></a><a name="bkmk_run_1_subscription"></a> Script: eseguire (attivare) una singola sottoscrizione  

Questo script eseguirà una sottoscrizione specifica usando il metodo FireEvent. Lo script eseguirà immediatamente la sottoscrizione, indipendentemente dalla pianificazione configurata per la sottoscrizione. EventType è verificato rispetto al set noto degli eventi definiti nel file di configurazione del server di report **rsreportserver.config** . Lo script usa il tipo di evento seguente per le sottoscrizioni standard:  
  
 `<Event>`  
  
 `<Type>TimedSubscription</Type>`  
  
 `</Event>`  
  
 Per altre informazioni sul file di configurazione, vedere [RsReportServer.config Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md).  
  
 Lo script include logica di ritardo di tipo "`Start-Sleep -s 6`". Dopo l'attivazione dell'evento è quindi disponibile tempo per rendere disponibile lo stato aggiornato con il metodo ListSubscription.  
  
 **Sintassi in modalità nativa:**  
  
```powershell
powershell c:\scripts\FireSubscription.ps1 "[server]/reportserver" $null "70366e82-2d3c-4edd-a216-b97e51e26de9"  
```  
  
 **Sintassi in modalità SharePoint:**  
  
```powershell
powershell c:\scripts\FireSubscription.ps1 "[server]/_vti_bin/reportserver" "https://[server]" "c3425c72-580d-423e-805a-41cf9799fd25"  
```  
  
 **Script:**  
  
```
  
# Parameters  
#    server         - server and instance name (e.g. myserver/reportserver or myserver/reportserver_db2)  
#    site           - use $null for a native mode server  
#    subscriptionid - subscription guid  
  
Param(  
  [string]$server,  
  [string]$site,  
  [string]$subscriptionid  
  )  
  
$rs2010 = New-WebServiceProxy -Uri "https://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
#event type is case sensative to what is in the rsreportserver.config  
$rs2010.FireEvent("TimedSubscription",$subscriptionid,$site)  
  
Write-Host " "  
Write-Host "----- Subscription ($subscriptionid) status: "  
#get list of subscriptions and filter to the specific ID to see the Status and LastExecuted  
Start-Sleep -s 6 # slight delay in processing so ListSubscription returns the updated Status and LastExecuted  
$subscriptions = $rs2010.ListSubscriptions($site);   
$subscriptions | select Status, Path, report, Description, Owner, SubscriptionID, EventType, lastexecuted | where {$_.SubscriptionID -eq $subscriptionid}  
  
```  

## <a name="see-also"></a>Vedere anche  

- [Metodo ReportingService2010.ListSubscriptions](/dotnet/api/reportservice2010.reportingservice2010.listsubscriptions)  

- [Metodo ReportingService2010.ChangeSubscriptionOwner](/dotnet/api/reportservice2010.reportingservice2010.changesubscriptionowner)   

- [ReportingService2010.ListChildren](/dotnet/api/reportservice2010.reportingservice2010.listchildren)  

- [ReportingService2010.FireEvent](/dotnet/api/reportservice2010.reportingservice2010.fireevent)