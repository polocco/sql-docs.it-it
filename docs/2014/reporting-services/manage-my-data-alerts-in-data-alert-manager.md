---
title: Gestire gli avvisi dati personali in Gestione avvisi dati | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- managing, alerts
- managing, data alerts
ms.assetid: e0e4ffdf-bd4c-4ebd-872b-07486cbb47c2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 07c75779d05d22e09e7823b5d0b3bffc2ca7acc8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108310"
---
# <a name="manage-my-data-alerts-in-data-alert-manager"></a>Gestire gli avvisi dati in Gestione avvisi dati
  Gli utenti di SharePoint possono visualizzare un elenco degli avvisi dati creati e le informazioni sugli avvisi. Possono inoltre eliminare i propri avvisi, aprire definizioni di avviso per la modifica nella finestra di progettazione Avviso dati ed eseguire i propri avvisi. Nella figura seguente sono illustrate le funzionalità disponibili per gli utenti in Gestione avvisi dati.  
  
 ![Funzionalità di Gestione avvisi per gli utenti di SharePoint](media/rs-alertmanageriw.gif "Funzionalità di Gestione avvisi per gli utenti di SharePoint")  
  
### <a name="to-view-a-list-of-your-alerts"></a>Per visualizzare un elenco di avvisi  
  
1.  Passare alla raccolta di SharePoint in cui sono stati salvati i report per i quali sono stati creati avvisi dati.  
  
2.  Fare clic sull'icona per espandere il menu a discesa in un report, quindi fare clic su **Gestisci avvisi dati**. Nella figura seguente è illustrato il menu a discesa.  
  
     ![Aprire Gestione avvisi dal menu di scelta rapida del report](media/rs-openalertmanager.gif "Aprire Gestione avvisi dal menu di scelta rapida del report")  
  
     Verrà aperto Gestione avvisi dati. Per impostazione predefinita, vengono elencati gli avvisi per il report selezionati nella raccolta.  
  
3.  Fare clic sulla freccia GIÙ accanto all'elenco **Visualizza avvisi per il report** e selezionare un report per visualizzare i relativi avvisi oppure fare clic su **Mostra tutto** per elencare tutti gli avvisi.  
  
    > [!NOTE]  
    >  Se il report selezionato non dispone di avvisi, non è necessario tornare alla raccolta di SharePoint per individuare e selezionare un report che disponga di avvisi. È invece possibile fare clic su **Mostra tutto** per visualizzare un elenco di tutti gli avvisi.  
  
     In una tabella vengono elencati il nome dell'avviso, il nome del report, il nome del creatore dell'avviso, il numero di volte in cui l'avviso è stato inviato, l'ultima modifica alla definizione di avviso e lo stato dell'avviso. Se l'avviso non può essere generato o inviato, nella colonna relativa allo stato sono incluse informazioni sull'errore che consentono di risolvere il problema.  
  
### <a name="to-edit-an-alert-definition"></a>Per modificare una definizione di avviso  
  
-   Fare clic con il pulsante destro del mouse sull'avviso dati per il quale si desidera modificare la definizione, quindi scegliere **Modifica**.  
  
     La definizione di avviso viene aperta in Gestione avvisi dati. Per altre informazioni, vedere [Modificare un avviso dati nella finestra di progettazione di avvisi](edit-a-data-alert-in-alert-designer.md) e [Finestra di progettazione Avviso dati](../../2014/reporting-services/data-alert-designer.md).  
  
    > [!NOTE]  
    >  La definizione di avviso dati può essere modificata solo dall'utente che l'ha creata.  
  
    > [!NOTE]  
    >  Se il report è cambiato e i feed di dati generati dal report sono cambiati, la definizione di avviso potrebbe non essere più valida. Questa condizione si verifica quando una colonna, a cui fa riferimento l'avviso nelle regole, viene eliminata dal report, quando il tipo di dati contenuto in tale colonna viene modificato, quando la colonna viene inclusa in un feed di dati diverso oppure quando il report viene eliminato o spostato. È possibile aprire una definizione di avviso che non è valida, ma non è possibile salvarla di nuovo fino a quando non diventa valida in base alla versione corrente del feed di dati del report in base a cui è compilata. Per altre informazioni sulla modalità di generazione di feed di dati dai report, vedere [Generazione di feed di dati dai report &#40;Generatore report e SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).  
  
### <a name="to-delete-an-alert-definition"></a>Per eliminare una definizione di avviso  
  
-   Fare clic con il pulsante destro del mouse sull'avviso dati che si desidera eliminare, quindi scegliere **Elimina**.  
  
     Dopo avere eliminato l'avviso, non verranno inviati ulteriori messaggi di avviso.  
  
### <a name="to-run-an-alert"></a>Per eseguire un avviso  
  
-   Fare clic con il pulsante destro del mouse sull'avviso dati che si desidera eseguire, quindi scegliere **Esegui**.  
  
     L'istanza di avviso viene creata e il messaggio di avviso dati viene inviato immediatamente, indipendentemente dalle opzioni di pianificazione specificate nella finestra di progettazione Avviso dati. Un avviso configurato per essere inviato ogni settimana e solo se i risultati cambiano viene ad esempio inviato.  
  
## <a name="see-also"></a>Vedi anche  
 [Gestione avvisi dati per gli amministratori di avvisi](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md)   
 [Reporting Services Data Alerts](../ssms/agent/alerts.md)  
  
  
