---
title: Stampare i report da un browser con il controllo di stampa (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 10054250-d915-4bcb-8a1d-26837db4e932
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d80d59759befa0a6d7b601509a99c7cc6e22fbf0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66107761"
---
# <a name="print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs"></a>Stampare i report da un browser con il controllo di stampa (Generatore report e SSRS)
  Benché un browser sia l'applicazione client più comune per visualizzare un report, le funzionalità di stampa dei browser non sono tra le più adatte per la stampa dei report, in quanto sono state progettate per la stampa di pagine Web. Le pagine stampate da un browser includono in genere tutti gli elementi visivi presenti nella pagina Web, più le informazioni dell'intestazione e del piè di pagina che identificano la pagina o il sito Web. Se si avvia la stampa dal browser, viene stampato il contenuto della finestra corrente. Per i report a più pagine, il browser stampa al massimo la prima pagina e, se la pagina del report è più grande delle dimensioni di una pagina stampata, il risultato non risulta completo.  
  
 Per migliorare la qualità della stampa dei report visualizzati in un browser e per la stampa di più pagine, è possibile utilizzare la funzionalità di stampa sul lato client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]disponibile in. Questa funzionalità consente di visualizzare una finestra di dialogo **Stampa** standard che può essere usata per selezionare una stampante, specificare le pagine e i margini e visualizzare un'anteprima del report prima della stampa. La funzionalità di stampa sul lato client può essere usata in sostituzione del comando **Stampa** del menu **File** del browser. Quando si utilizza la stampa sul lato client, il report viene stampato come è stato progettato, senza gli elementi aggiuntivi presenti nella stampa delle pagine Web.  
  
 Per utilizzare la funzionalità di stampa sul lato client, è necessario installare un controllo [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX. Per altre informazioni, vedere [Abilitare e disabilitare la stampa sul lato client per Reporting Services](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="print-options"></a>Opzioni di stampa  
 Per configurare le proprietà di stampa del report, fare clic sul pulsante **Proprietà** nella finestra di dialogo **Stampa** . Il**Formato carta** è determinato dall'altezza e dalla larghezza predefinite delle pagine del report specificate nella definizione del report. I valori disponibili dipendono dal tipo e dalle funzionalità della stampante. Per la larghezza e l'altezza vengono utilizzati i valori predefiniti determinati dai driver della stampante configurati nel computer. La modifica di questi valori provoca la stampa del report con le nuove dimensioni. La larghezza e l'altezza della pagina sono determinate dall'opzione **Orientamento**, impostata su **Verticale** o **Orizzontale**. L'orientamento predefinito dipende dalla larghezza e dall'altezza delle pagine del report.  
  
> [!NOTE]  
>  La finestra di dialogo **Stampa** e le impostazioni predefinite della stampante per la larghezza, l'altezza e l'orientamento della pagina sono determinate dalla definizione del report.  
  
### <a name="print-preview"></a>Anteprima di stampa  
 Per visualizzare un'anteprima di un report, fare clic sul pulsante **Anteprima** nella finestra di dialogo **Stampa** . Verrà aperta la prima pagina del report in una finestra di anteprima distinta. Se il rendering del report viene eseguito sul server di report, saranno disponibili alcune pagine aggiuntive. Il rendering dell'anteprima di un report viene eseguito in formato EMF. È possibile passare alla pagina precedente o successiva fino ad arrivare all'ultima pagina, in cui il pulsante **Successiva** risulta disabilitato.  
  
### <a name="adjusting-print-margins"></a>Impostazione dei margini di stampa  
 È possibile modificare i margini di stampa del report EMF visualizzato prima di avviare la stampa. Per eseguire questa operazione, fare clic sul pulsante **Anteprima** nella finestra di dialogo **Stampa** . Nella parte superiore della pagina di anteprima fare clic sul pulsante **Margini** . Verrà visualizzata la finestra di dialogo Margini. Impostare i margini superiore, inferiore, destro e sinistro nel modo desiderato. [!INCLUDE[clickOK](../../includes/clickok-md.md)] La finestra di dialogo verrà chiusa e le impostazioni verranno archiviate per l'anteprima del rendering e la stampa.  
  
## <a name="see-also"></a>Vedi anche  
 [Stampare report &#40;Generatore report e SSRS&#41;](print-reports-report-builder-and-ssrs.md)   
 [Stampare un report &#40;Generatore report e SSRS&#41;](print-a-report-report-builder-and-ssrs.md)  
  
  
