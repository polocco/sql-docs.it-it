---
title: Creare, modificare ed eliminare snapshot nella cronologia dei report | Microsoft Docs
description: Informazioni su come intervenire sulla cronologia di Reporting Services aggiungendo ed eliminando snapshot oppure modificando le proprietà che specificano le modalità di archiviazione della cronologia.
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- snapshots [Reporting Services]
- report snapshots [Reporting Services]
ms.assetid: 5aebbbfa-a8db-462d-8ab9-746fad9525f0
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 4c686ff203b9a080424fb46e50c42a6edefd7655
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2020
ms.locfileid: "84548033"
---
# <a name="create-modify-and-delete-snapshots-in-report-history"></a>Creare, modificare ed eliminare snapshot nella cronologia dei report
  La cronologia dei report è una raccolta di snapshot dei report. È possibile intervenire sulla cronologia aggiungendo ed eliminando snapshot oppure modificando le proprietà che specificano le modalità di archiviazione della cronologia. È possibile creare la cronologia dei report manualmente o in base a una pianificazione.  
  
 Per creare la cronologia dei report, è necessario che la propria assegnazione di ruolo includa l'attività "Gestione della cronologia dei report". Per visualizzare la cronologia dei report, la propria assegnazione di ruolo deve includere l'attività "Visualizzazione di report". La cronologia di un report è disponibile per tutti gli utenti autorizzati ad accedere al report. Non è possibile consentire o impedire l'accesso alla cronologia solo a utenti specifici.  
  
 Gli snapshot disponibili nella cronologia del report sono identificati dalla data e dall'ora di creazione, che corrispondono al momento di esecuzione della query.  
  
## <a name="creating-snapshots-in-report-history"></a>Creazione di snapshot nella cronologia dei report  
 È possibile creare snapshot manualmente o in base a intervalli pianificati per qualsiasi report che può essere eseguito in modo automatico. Per l'esecuzione automatica, il report deve utilizzare credenziali archiviate oppure non utilizzare credenziali. Inoltre, se il report utilizza parametri, è necessario specificare i valori predefiniti da utilizzare quando il report viene eseguito. È possibile specificare le credenziali archiviate e i valori dei parametri nelle pagine delle proprietà del report. Per altre informazioni, vedere [Pagina delle proprietà Parametri &#40;Gestione report&#41;](https://msdn.microsoft.com/library/ebb53598-2378-46ae-8935-d5192f8ea49a).  
  
 Quando si crea uno snapshot di un report, nel database del server di report vengono archiviati gli elementi seguenti insieme allo snapshot:  
  
-   Il set di risultati, ovvero i dati del report che vengono recuperati tramite le credenziali specificate nella pagina delle proprietà Origini dati del report.  
  
-   La definizione sottostante del report nel momento in cui lo snapshot viene creato. Se la definizione del report viene modificata dopo la generazione dello snapshot, tali modifiche non si rifletteranno nello snapshot.  
  
-   I valori dei parametri utilizzati per ottenere o filtrare il set di risultati.  
  
-   Le risorse incorporate, ad esempio le immagini. Le risorse esterne che sono collegate a un report non vengono archiviate insieme allo snapshot del report.  
  
 Le modalità di creazione della cronologia di un report e il numero di snapshot del report che è possibile archiviare vengono definite mediante le impostazioni appropriate.  
  
 Se durante l'esecuzione di un report si verifica un errore, lo snapshot non viene creato. Se, invece, durante l'esecuzione di un report vengono generati avvisi ma il report viene eseguito ugualmente, lo snapshot può essere generato.  
  
## <a name="modifying-properties-and-deleting-report-history"></a>Modifica di proprietà ed eliminazione della cronologia dei report  
 Gli snapshot dei report non possono essere modificati. È tuttavia possibile modificare le proprietà in modo che la cronologia di un report venga eliminata.  
  
 È possibile eliminare la cronologia di un report mediante le operazioni seguenti:  
  
-   Eliminazione manuale di singoli snapshot o gruppi di snapshot.  
  
     Per eliminare gli snapshot, aprire la pagina Cronologia in Gestione report. Passare al report desiderato, fare clic su Cronologia, selezionare la casella di controllo accanto agli snapshot che si desidera eliminare e quindi fare clic su **Elimina**.  
  
-   Diminuzione del limite di archiviazione della cronologia del report in modo da ridurre il numero di snapshot archiviabili. Il limite di archiviazione della cronologia di un report può essere impostato per il server di report o per report specifici. La riduzione del limite implica l'eliminazione degli snapshot meno recenti dalla cronologia.  
  
 Non è possibile eliminare in blocco tutta la cronologia dei report archiviata in un server di report.  
  
 Quando si elimina un report, viene eliminata anche la relativa cronologia. Se ad esempio si elimina un report sulle vendite mensili per sostituirlo con una nuova versione, viene eliminata anche la cronologia a esso associata. Se invece si sposta un report, la relativa cronologia viene spostata insieme al report.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare la cronologia dei report &#40;Reporting Services in modalità integrata SharePoint&#41;](../../reporting-services/report-server/create-report-history-reporting-services-in-sharepoint-integrated-mode.md)   
 [Gestione report &#40;modalità nativa SSRS&#41;](https://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)   
 [Gestione contenuto del server di report &#40;modalità nativa SSRS&#41;](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)   
 [Aggiungere uno snapshot alla cronologia del report &#40;Gestione report&#41;](../../reporting-services/report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [Limitare la cronologia dei report &#40;Gestione report&#41;](../../reporting-services/reports/limit-report-history-report-manager.md)  
  
  
