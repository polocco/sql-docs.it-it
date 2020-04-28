---
title: Gestione avvisi dati per gli amministratori di avvisi | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- managing, alerts
- managing, data alerts
ms.assetid: 32fd968f-1c0c-4ba8-851c-8a3b5e1fbbf2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6dff332a686371db290a5ff16a929e5bed596b9b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "78173890"
---
# <a name="data-alert-manager-for-alerting-administrators"></a>Gestione avvisi dati per gli amministratori di avvisi
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] include Gestione avvisi dati per consentire agli amministratori di avvisi di SharePoint di gestire gli avvisi dati. Gli amministratori di avvisi possono visualizzare le informazioni relative a tutti gli avvisi salvati nel sito, nonché eliminare avvisi. Nella figura seguente sono illustrate le funzionalità disponibili per i responsabili di avvisi di SharePoint tramite Gestione avvisi dati.

 ![Gestione avvisi per gli amministratori del sito di SharePoint](media/rs-alertmanagersite.gif "Gestione avvisi per gli amministratori del sito di SharePoint")

 Quando il sito è abilitato per gli avvisi dati, vengono create e aggiunte al sito di SharePoint due pagine, ovvero MyDataAlerts.aspx e SiteDataAlerts.aspx. SiteDataAlerts.aspx rappresenta Gestione avvisi dati per gli amministratori di avvisi. Gli amministratori di avvisi possono aprire Gestione avvisi dati dalla pagina Impostazioni sito di SharePoint. Per aprire Gestione avvisi dati, gli amministratori di avvisi devono disporre dell'autorizzazione Gestione avvisi di SharePoint.

 È inoltre possibile aprire Gestione avvisi dati direttamente utilizzando un URL. Di seguito è illustrata la sintassi dell'URL:

 `http: //<site name>/_layouts/ReportServer/ SiteDataAlerts.aspx`

> [!NOTE]
>  Un amministratore di avvisi può concedere agli Information Worker l'autorizzazione per accedere alle funzionalità di avviso dati di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Per informazioni sulle autorizzazioni richieste, vedere [Avvisi dati di Reporting Services](../ssms/agent/alerts.md).

##  <a name="viewing-data-alert-information"></a><a name="ViewingAlerts"></a> Visualizzazione delle informazioni sugli avvisi dati
 Se Reporting Services viene installato e configurato in SharePoint, nella pagina Impostazioni sito di SharePoint sono incluse le opzioni di **Reporting Services** . Per aprire Gestione avvisi dati, gli amministratori di avvisi possono fare clic sull'opzione **Gestisci avvisi dati** disponibile in Reporting Services. Nella figura seguente viene illustrata la posizione nella pagina Impostazioni sito da cui è possibile aprire Gestione avvisi dati.

 ![Sezione Reporting Services della pagina Impostazioni sito](media/rs-sitesettings.gif "Sezione Reporting Services della pagina Impostazioni sito")

 In Gestione avvisi dati è inclusa una tabella in cui sono elencati il nome dell'avviso, il nome del report, il nome del proprietario dell'avviso, il numero di volte in cui il messaggio di avviso è stato inviato, l'ultima esecuzione dell'avviso, l'ultima modifica alla definizione di avviso e lo stato del messaggio di avviso. Se l'avviso non può essere generato o inviato, nella colonna relativa allo stato sono incluse informazioni sull'errore che consentono di risolvere i problemi relativi all'avviso. Per ulteriori informazioni, vedere [gestire tutti gli avvisi dati in un sito di SharePoint in Gestione avvisi dati](manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager.md).

 Nella tabella seguente sono illustrati i dati di esempio di una tabella di Gestione avvisi dati. Quando si verifica un errore, il messaggio di errore e l'identificatore della voce nel log (un GUID) vengono inclusi nel campo **Stato** nella tabella.

|Nome avviso|Nome del report|Created By (Creato da)|Avvisi inviati|Ultima esecuzione|Data ultima modifica|Stato|
|----------------|-----------------|----------------|-----------------|--------------|-------------------|------------|
|SalesQTR|SalesByTerritoryAndQTR|Lauren Johnson|4|6/12/2011|6/1/2011|L'ultimo avviso è stato eseguito correttamente e l'avviso è stato inviato.|
|UnitsSold|ProductsSalesByQTR|Michael Blythe|2|7/1/2011|6/28/2011|L'ultimo avviso è stato eseguito correttamente, tuttavia i dati non sono stati modificati e non è stato inviato alcun avviso.|
|InventoryCount|StockStatusByQTR|Lauren Johnson|7|7/10/2011|7/2/2011|\<messaggio di errore>Il file di log contiene informazioni dettagliate sull'errore. Fare riferimento alla voce del log con l'identificatore: \<GUID>.|
|TopPromotion|PromotionTracking|Cristian Petculescu|0||5/23/2011|Avviso creato.|

 Per ulteriori informazioni, vedere [gestire tutti gli avvisi dati in un sito di SharePoint in Gestione avvisi dati](manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager.md).

 È possibile visualizzare tutti gli avvisi creati dagli utenti del sito. È necessario scegliere un utente, quindi scegliere se visualizzare tutti i relativi avvisi o solo quelli per un report specifico.


##  <a name="delete-data-alerts"></a><a name="DeleteAlerts"></a>Elimina avvisi dati
 Le definizioni di avviso dati vengono eliminate da Gestione avvisi dati. Ogni definizione di avviso dati dispone di un proprietario, ovvero l'utente di SharePoint da cui è stata creata. I proprietari possono eliminare solo le definizioni di avviso che hanno creato. Per altre informazioni, vedere [Gestire gli avvisi dati in Gestione avvisi dati](manage-my-data-alerts-in-data-alert-manager.md).

 Gli amministratori di avvisi di SharePoint possono elencare e quindi eliminare le definizioni di avviso create da tutti gli utenti del sito. Per altre informazioni, vedere [Gestire tutti gli avvisi dati in un sito di SharePoint con Gestione avvisi dati](manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager.md).

 Dopo aver eliminato la definizione di avviso, non verranno inviati ulteriori avvisi. Se tuttavia si esegue una query sul database di avvisi, è possibile trovare ancora la definizione di avviso. Il servizio avvisi consente di eseguire la pulizia in base a una pianificazione e la definizione di avviso verrà eliminata definitivamente alla successiva operazione di pulizia. L'intervallo di pulizia predefinito è impostato su 20 minuti. Questo e altri intervalli di pulizia sono configurabili. Per altre informazioni, vedere [Avvisi dati di Reporting Services](../ssms/agent/alerts.md).


##  <a name="related-tasks"></a><a name="HowTo"></a> Attività correlate
 In questa sezione è elencata una procedura tramite cui viene illustrata la modalità di gestione degli avvisi.

-   [Gestire tutti gli avvisi dati in un sito di SharePoint con Gestione avvisi dati](manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager.md)


## <a name="see-also"></a>Vedere anche
 [Reporting Services Data Alerts](../ssms/agent/alerts.md)


