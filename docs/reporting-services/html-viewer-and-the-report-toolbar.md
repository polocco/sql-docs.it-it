---
title: Visualizzatore HTML e barra degli strumenti dei report | Microsoft Docs
description: Informazioni sul Visualizzatore HTML e sulla barra degli strumenti dei report e su come è possibile visualizzare i report su richiesta quando vengono richiesti dal server di report.
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- HTML Viewer [Reporting Services]
- report toolbar [Reporting Services]
ms.assetid: cd86b319-babd-45af-a6a4-f659fdcc40c3
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b413cf8f3fd5b8e85a94e5ed26add2717dcc2376
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87396478"
---
# <a name="html-viewer-and-the-report-toolbar"></a>Visualizzatore HTML e barra degli strumenti dei report
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] fornisce un visualizzatore HTML usato per visualizzare i report quando vengono richiesti dal server di report. Il Visualizzatore HTML è progettato per la visualizzazione di report in formato HTML e include una barra degli strumenti dei report, una sezione dei parametri, una sezione delle credenziali e una mappa documento. Nella barra degli strumenti dei report nel Visualizzatore HTML sono disponibili funzionalità per l'utilizzo del report oltre a opzioni per l'esportazione che consentono di visualizzare il report in formati diversi da HTML. La sezione dei parametri e la mappa documento vengono visualizzate solo se si aprono report configurati per l'utilizzo dei parametri e di un controllo mappa documento.  
  
 Sebbene non sia possibile modificare la barra degli strumenti dei report, è possibile configurare parametri nell'URL di un report affinché nascondano tale barra in un report. Per altre informazioni su come nascondere la barra degli strumenti dei report, vedere [Riferimento ai parametri di accesso con URL](../reporting-services/url-access-parameter-reference.md).  
  
## <a name="report-toolbar"></a>Barra degli strumenti dei report  
 La barra degli strumenti dei report include funzionalità di navigazione tra le pagine, ingrandimento o riduzione, aggiornamento, ricerca, esportazione, stampa e feed di dati per i report gestiti tramite l'estensione per il rendering HTML.  
  
 La funzionalità di stampa è facoltativa. Se disponibile, sulla barra degli strumenti dei report viene visualizzata l'icona di una stampante. Al primo utilizzo, facendo clic sull'icona della stampante viene scaricato un controllo ActiveX da installare. Dopo aver installato il controllo, quando si fa clic sull'icona della stampante viene aperta una finestra di dialogo Stampa che consente di selezionare una delle stampanti configurate per il computer. La disponibilità della funzionalità di stampa è determinata dalle impostazioni del server e del browser. Per altre informazioni, vedere [Stampare report da un browser con il controllo di stampa &#40;Generatore report e SSRS&#41;](../reporting-services/report-builder/print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md) e [Abilitare e disabilitare la stampa sul lato client per Reporting Services](../reporting-services/report-server/enable-and-disable-client-side-printing-for-reporting-services.md).  
  
 La barra degli strumenti dei report è simile a quella illustrata nella figura seguente. La barra degli strumenti dei report effettivamente visualizzata può essere diversa rispetto a questa figura, a seconda delle funzionalità per i report o delle opzioni di rendering disponibili.  
  
 ![Barra degli strumenti dei report](../reporting-services/media/ssrs-htmlviewer-toolbar.png "Barra degli strumenti dei report")  
  
 Nella tabella seguente vengono descritte le funzionalità di utilizzo più comune della barra degli strumenti dei report. Per ogni funzionalità viene inoltre indicato il controllo utilizzato per accedervi.  
  
|Icona o controllo|Nome|Descrizione|  
|------------------------------|-|--------|  
|![Controlli per la navigazione tra le pagine](../reporting-services/media/htmlviewer-pagenav.gif "Controlli per la navigazione tra le pagine")|**Controlli per la navigazione tra le pagine**|Aprire la prima o l'ultima pagina di un report, scorrere un report una pagina alla volta, aprire una pagina specifica di un report. Per visualizzare una pagina specifica, digitare il numero di pagina e premere INVIO.|  
|![Controlli per la visualizzazione delle pagine](../reporting-services/media/htmlviewer-pagesize.gif "Controlli per la visualizzazione delle pagine")|**Controlli per la visualizzazione delle pagine**|Ingrandire o ridurre le dimensioni della pagina del report. Oltre a modificare il valore percentuale, è possibile selezionare **Larghezza pagina** per adeguare la larghezza della pagina del report alle dimensioni della finestra del browser oppure **Pagina intera** per visualizzare l'intero report nella finestra del browser. In **Internet Explorer 5.5 e versioni successive è supportata l'opzione** Zoom [!INCLUDE[msCoName](../includes/msconame-md.md)] .|  
|![Campo di ricerca](../reporting-services/media/htmlviewer-search.gif "Campo di ricerca")|**Campo di ricerca**|Eseguire una ricerca di contenuto nel report digitando la parola o la frase che si desidera trovare (con una lunghezza massima di 256 caratteri). La ricerca viene eseguita senza distinzione tra maiuscole e minuscole a partire dalla pagina o dalla sezione selezionata. Nell'operazione di ricerca viene incluso solo il contenuto visibile. Per cercare le occorrenze successive dello stesso valore, fare clic su **Avanti**.|  
|![Formati di esportazione](../reporting-services/media/htmlviewer-export.GIF "Formati di esportazione")|**Formati di esportazione**|Aprire una nuova finestra del browser ed eseguire il rendering del report nel formato selezionato. I formati disponibili dipendono dalle estensioni per il rendering installate nel server di report. Per la stampa è consigliato il formato TIFF. Fare clic su **Esporta** per visualizzare il report nel formato selezionato.|  
|![Icona della mappa documento](../reporting-services/media/htmlviewer-docmap.GIF "Icona della mappa documento")|**Icona della mappa documento**|Visualizzare o nascondere il riquadro della mappa documento in un report che include una mappa documento. Una mappa documento è un controllo per la navigazione all'interno del report simile al riquadro di navigazione in un sito Web. È possibile fare clic sugli elementi nella mappa documento per passare a un gruppo, a una pagina o a un sottoreport specifico.|  
|![Icona della stampante](../reporting-services/media/printer-icon.gif "Icona della stampante")|**Icona della stampante**|Aprire una finestra di dialogo Stampa per specificare le opzioni di stampa e stampare un report. La prima volta che si seleziona questa icona viene richiesto di scaricare il controllo di stampa.|  
||**Visualizzare e nascondere le icone**|Visualizzare o nascondere i campi dei valori di parametro e il pulsante **Visualizza report** in un report con parametri.|  
|![Pulsante di aggiornamento del browser sulla barra degli strumenti dei report](../reporting-services/media/htmlviewer-refresh.GIF "Pulsante di aggiornamento del browser sulla barra degli strumenti dei report")|**Icona per l'aggiornamento del report**|Aggiornare il report. I dati dei report live verranno aggiornati. I report memorizzati nella cache verranno ricaricati dalla posizione di archiviazione.|  
|![htmlviewer_datafeed](../reporting-services/media/htmlviewer-datafeed.gif "htmlviewer_datafeed")|**Icona Feed di dati**|Feed di dati generati dai report.|  
|![ssrs_powerbi_button_reportwviewer](../reporting-services/media/ssrs-powerbi-button-reportwviewer.png "ssrs_powerbi_button_reportwviewer")|**Aggiungi al dashboard di Power BI**|Aggiungere elementi dei report di supporto a [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]. Se il pulsante non è visibile, il server di report non è stato integrato con [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)].  Per altre informazioni, vedere [Integrazione del server di report e di Power BI &#40;Gestione configurazione&#41;](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md).|  
  
### <a name="about-export-formats"></a>Informazioni sui formati di esportazione  
 Tramite la barra degli strumenti dei report è possibile scegliere vari formati di visualizzazione del report. I formati disponibili dipendono dalle estensioni per il rendering installate nel server di report. Quando si seleziona un formato diverso, il report viene visualizzato in una seconda finestra del browser utilizzando il visualizzatore associato al formato di esportazione selezionato. Se per il formato selezionato non è disponibile un visualizzatore, è possibile selezionare un formato diverso.  
  
 Nell'installazione predefinita del server di report sono inclusi i formati di esportazione seguenti. L'elenco dei formati di esportazione effettivamente disponibili può essere diverso da quello qui indicato.  
  
|Formato di esportazione|Descrizione|  
|-------------------|-----------------|  
|XML|Consente di visualizzare un report con la sintassi XML. I report visualizzati in XML vengono aperti un una nuova finestra del browser.|  
|CSV|Consente di visualizzare un report in formato delimitato da virgole. Il report viene aperto in un'applicazione associata al tipo di file CSV.|  
|PDF|Consente di visualizzare un report con un visualizzatore PDF sul lato client. Per utilizzare questo formato è necessario disporre di un visualizzatore PDF di terze parti, ad esempio, Adobe Acrobat Reader.|  
|MHTML|Consente di visualizzare il report in un formato HTML con codifica MIME e quindi di mantenere le immagini e il contenuto collegato insieme al report.|  
|Excel|Consente di visualizzare il report in [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel come file con estensione xlsx.|  
|PowerPoint|Consente di visualizzare il report in [!INCLUDE[msCoName](../includes/msconame-md.md)] PowerPoint come file con estensione pptx.|  
|File TIFF|Consente di visualizzare il report nel visualizzatore TIFF predefinito. Per alcuni client [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows viene utilizzato Visualizzatore immagini e fax per Windows. Selezionare questo formato per visualizzare un report in un layout orientato alla pagina.|  
|Word|Consente di visualizzare il report in [!INCLUDE[msCoName](../includes/msconame-md.md)] Word come file con estensione docx.|  
  
## <a name="parameters"></a>Parametri  
 I parametri sono i valori utilizzati per la selezione di dati specifici, ovvero i valori utilizzati per eseguire una query che selezioni i dati del report o filtri il set di risultati. Le date, i nomi e gli ID sono tra i parametri più comunemente utilizzati nei report. Se si specifica un valore per un parametro, nel report verranno visualizzati solo i dati corrispondenti a tale valore. Ad esempio, se si seleziona un parametro ID dipendente verranno visualizzati solo i dati relativi al dipendente specifico selezionato. I parametri corrispondono a campi nel report. Dopo aver specificato un parametro, fare clic su **Visualizza report** per recuperare i dati.  
  
 I valori di parametri validi per ogni report vengono stabiliti dall'autore del report. Anche l'amministratore del report può impostare valori per i parametri. Per informazioni sui valori validi per un report, rivolgersi all'autore o all'amministratore.  
  
## <a name="credentials"></a>Credenziali  
 Le credenziali sono i valori relativi a nome utente e password utilizzati per ottenere l'accesso a un'origine dei dati. Dopo aver specificato le credenziali, fare clic su **Visualizza report** per recuperare i dati. Se per un report è richiesta la procedura di accesso, è possibile che le autorizzazioni di un utente consentano di visualizzare dati diversi rispetto a quelli visibili per un altro utente. Ne consegue che due utenti possono eseguire lo stesso report e ottenere risultati diversi. Alcuni report, inoltre, contengono aree nascoste che vengono visualizzate o meno in base alle credenziali di accesso o alle selezioni effettuate nel report stesso. Le aree nascoste del report vengono escluse dalle operazioni di ricerca e si ottengono pertanto risultati diversi rispetto a una ricerca eseguita nello stesso report visibile in tutte le sue parti.  
  
## <a name="see-also"></a>Vedere anche  
 [Specificare le credenziali e le informazioni sulla connessione per le origini dati del report](../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Ricerca, visualizzazione e gestione dei report &#40;Generatore report e SSRS&#41;](../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Esportare report &#40;Generatore Report e SSRS&#41;](../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)  
  
  
