---
title: Log richieste | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 165d3833-0493-490c-9f63-8a134a7fafb8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9c0a129bd8985180a9094b8846e685c0d4025313
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2020
ms.locfileid: "86922750"
---
# <a name="request-log"></a>Log richieste

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Usare la finestra di dialogo **Log richieste** per visualizzare gli eventi registrati durante la richiesta fatta al sistema SAP Netweaver BW per i dati di esempio. Queste informazioni possono essere utili se è necessario risolvere i problemi relativi alla configurazione dell'origine SAP BW.  
  
 Per altre informazioni sul componente di origine SAP BW di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW, vedere [Origine SAP BW](../../integration-services/data-flow/sap-bw-source.md).  
  
> [!IMPORTANT]  
>  La documentazione per Microsoft Connector 1.1 for SAP BW presuppone la conoscenza dell'ambiente SAP Netweaver BW. Per ulteriori informazioni su SAP Netweaver BW o per informazioni su come configurare oggetti e processi di SAP Netweaver BW, vedere la documentazione SAP.  
  
> [!IMPORTANT]  
>  L'estrazione di dati da SAP Netweaver BW richiede licenze SAP aggiuntive. Contattare SAP per verificare questi requisiti.  
  
 **Per aprire la finestra di dialogo Log richieste**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il pacchetto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene l'origine SAP BW.  
  
2.  Nella scheda **Flusso di dati** fare doppio clic sull'origine SAP BW.  
  
3.  Nell' **Editor origine SAP BW**fare clic su **Gestione connessione** per aprire la pagina **Gestione connessione** dell'editor.  
  
4.  Dopo aver configurato l'origine SAP BW, fare clic su **Anteprima** per visualizzare gli eventi in anteprima nella finestra di dialogo **Log richieste** .  
  
    > [!NOTE]  
    >  Quando si fa clic su **Anteprima** , inoltre, viene aperta la finestra di dialogo **Anteprima** . Per altre informazioni su questa finestra di dialogo, vedere [Anteprima](../../integration-services/data-flow/preview.md).  
  
## <a name="options"></a>Opzioni  
 **Time**  
 Visualizza l'ora di registrazione dell'evento.  
  
 **Tipo**  
 Visualizza il tipo dell'evento registrato. Nella tabella seguente sono elencati i tipi di eventi possibili.  
  
|valore|Descrizione|  
|-----------|-----------------|  
|S|Messaggio di operazione completata.|  
|E|Messaggio di errore|  
|W|Messaggio di avviso.|  
|I|Messaggio informativo.|  
|Una|L'operazione è stata interrotta.|  
  
 **Messaggio**  
 Visualizza il testo del messaggio associato all'evento registrato.  
  
## <a name="see-also"></a>Vedere anche  
 [Editor origine SAP BW &#40;pagina Gestione connessione&#41;](../../integration-services/data-flow/sap-bw-source-editor-connection-manager-page.md)   
 [Guida sensibile al contesto di Microsoft Connector per SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  
