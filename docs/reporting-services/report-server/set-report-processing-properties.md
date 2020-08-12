---
title: Impostare proprietà di elaborazione dei report | Microsoft Docs
description: Informazioni sulle proprietà di esecuzione dei report che, in un server di report, controllano il modo in cui vengono elaborati i report e su come configurarle per ogni report tramite il portale Web.
ms.date: 06/10/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- on-demand reports
- report processing [Reporting Services], execution properties
- snapshots [Reporting Services], running reports from
- cached reports [Reporting Services]
- report snapshots [Reporting Services], running reports from
- report execution snapshots [Reporting Services]
ms.assetid: b5cbc453-5986-423e-af44-1f243ef3edb1
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 62c38e222ede1678d7fd06089897b3a8435aa687
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547883"
---
# <a name="set-report-processing-properties"></a>Impostare proprietà di elaborazione dei report
  Le proprietà di esecuzione dei report consentono di controllarne le modalità di esecuzione e devono essere impostate singolarmente per ogni report.  
  
 Per impostare le proprietà di esecuzione dei report, passare al report nel portale Web, fare clic con il pulsante destro del mouse sul report e scegliere **Gestisci** dal menu a discesa.
  
## <a name="report-execution-modes"></a>Modalità di esecuzione dei report  
 I report possono essere eseguiti su richiesta o come snapshot. Nella sezione seguente vengono descritte le due diverse modalità.  
  
### <a name="running-reports-on-demand"></a>Esecuzione di report su richiesta 
 È possibile specificare che a ogni esecuzione di un report da parte di un utente venga eseguita una query su un'origine dei dati. I report eseguiti in questo modo vengono definiti report su richiesta e contengono i dati più aggiornati. Per ogni utente che apre o richiede il report viene creata una nuova istanza del report che contiene i risultati di una nuova query. In questo modo se un report viene aperto da dieci utenti contemporaneamente, per l'elaborazione delle istanze del report vengono eseguite dieci query sull'origine dati.  
  
### <a name="running-reports-on-demand-from-cache"></a>Esecuzione di report su richiesta dalla cache 
 Per migliorare le prestazioni, è possibile specificare che quando un utente esegue un report, il report stesso e i relativi dati vengano memorizzati temporaneamente nella cache. La copia nella cache sarà disponibile in seguito per altri utenti che accederanno allo stesso report. In questo modo se dieci utenti aprono il report, questo verrà elaborato solo in seguito alla prima richiesta. Il report viene quindi memorizzato nella cache e gli altri nove utenti visualizzeranno la copia memorizzata nella cache.  
  
 I report memorizzati nella cache vengono rimossi a intervalli di tempo definiti dall'utente. È possibile specificare un valore per gli intervalli in minuti oppure pianificare la data e l'ora in cui cancellare la cache. Per altre informazioni, vedere [Memorizzazione dei report nella cache &#40;SSRS&#41;](../../reporting-services/report-server/caching-reports-ssrs.md).  
  
### <a name="running-reports-from-snapshots"></a>Esecuzione di report da snapshot  
 Il termine snapshot del report indica un report che include informazioni sul layout e dati recuperati in un momento specifico. È possibile eseguire un report come snapshot per evitare che venga eseguito in momenti indesiderati, ad esempio durante un backup pianificato. Uno snapshot di report viene in genere creato e in seguito aggiornato in base a una pianificazione, consentendo all'utente di determinare esattamente quando verrà eseguita l'elaborazione del report e dei dati. Se un report si basa su query la cui esecuzione richiede molto tempo oppure su query che utilizzano dati di un'origine dati che non si desidera venga utilizzata in determinati orari, è consigliabile eseguire il report come snapshot.  
  
 Uno snapshot di report viene archiviato in un database del server di report, da dove viene in seguito recuperato quando un utente o un processo, ad esempio una sottoscrizione, richiede il report. Quando viene aggiornato, lo snapshot del report viene sovrascritto da una nuova istanza. Le versioni precedenti di uno snapshot del report vengono salvate nel server di report solo se si impostano in modo specifico le opzioni per l'aggiunta alla cronologia del report. Per altre informazioni, vedere [Creare, modificare ed eliminare snapshot nella cronologia dei report](../../reporting-services/report-server/create-modify-and-delete-snapshots-in-report-history.md).  
  
 Non tutti i report possono essere configurati per l'esecuzione come snapshot. Non è possibile creare uno snapshot per un report mediante il quale si visualizzano richieste di credenziali agli utenti oppure si utilizza la sicurezza integrata di Windows per recuperare i dati per il report. Se si desidera eseguire come snapshot un report con parametri, sarà necessario specificare i parametri predefiniti da utilizzare per la creazione dello snapshot. A differenza dei report eseguiti su richiesta, non è possibile specificare un valore di parametro diverso per lo snapshot dopo l'apertura del report. La scelta di un valore di parametro diverso comporterebbe una nuova richiesta di elaborazione del report che non è consentita.  
  
 In alcuni casi la configurazione dell'esecuzione di un report su richiesta come snapshot può disattivare le sottoscrizioni. Nella condizione seguente il server di report disattiverà le sottoscrizioni esistenti definite quando il report era configurato per l'esecuzione su richiesta:  
  
-   Per soddisfare i requisiti relativi all'esecuzione del report come snapshot, nel report vengono utilizzati parametri di query e si seleziona un valore specifico come parametro predefinito.  
  
-   Le sottoscrizioni esistenti vengono configurate in modo da utilizzare valori di parametri diversi da quelli predefiniti specificati per lo snapshot.  
  
 Quando si verifica questa condizione, il server di report disabilita la sottoscrizione alla successiva pianificazione di esecuzione. Per riattivare la sottoscrizione, aprire e quindi salvare la sottoscrizione. Quando si apre la sottoscrizione, il server di report aggiorna i valori dei parametri della sottoscrizione in modo che corrispondano a quelli specificati per lo snapshot. Per altre informazioni, vedere [Sottoscrizioni e recapito &#40;Reporting Services&#41;](../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Impostare le opzioni di elaborazione &#40;Reporting Services in modalità integrata SharePoint&#41;](../../reporting-services/report-server-sharepoint/set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)   
 [Concetti relativi a Reporting Services &#40;SSRS&#41;](../../reporting-services/reporting-services-concepts-ssrs.md)   
 [Creare, modificare ed eliminare snapshot nella cronologia dei report](create-modify-and-delete-snapshots-in-report-history.md)   
 [Specificare le credenziali e le informazioni sulla connessione per le origini dati del report](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
  