---
title: Aggiungere un ulteriore server di report a una farm (con scalabilità orizzontale SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c1a6b683-15cf-44ae-ac60-ceee63a60aaf
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b90bb5624e5b5cdbf3f1542ad0bef0d2765da248
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108972"
---
# <a name="add-an-additional-report-server-to-a-farm-ssrs-scale-out"></a>Aggiungere un ulteriore server di report a una farm (con scalabilità orizzontale SSRS)
  L'aggiunta di un secondo o altri server di report in modalità SharePoint alla farm di SharePoint può migliorare le prestazioni e il tempo di risposta dell'elaborazione del server di report. Se le prestazioni risultano rallentate dopo aver aggiunto altri utenti, report e applicazioni al server di report, l'aggiunta di ulteriori server di report può migliorare le prestazioni. È inoltre consigliabile aggiungere un secondo server di report per aumentare la disponibilità dei server di report in caso di problemi hardware o di manutenzione generale di singoli server di report nell'ambiente. A partire dalla versione [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , la procedura per la scalabilità orizzontale dell'ambiente [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in modalità SharePoint segue la distribuzione standard della farm di SharePoint e sfrutta le funzionalità di bilanciamento del carico di SharePoint.  
  
> [!IMPORTANT]  
>  La distribuzione con scalabilità orizzontale di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] non è supportata in tutte le edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per ulteriori informazioni, vedere la [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sezione relativa alle [funzionalità supportate dalle edizioni di SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
> [!TIP]  
>  A partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] non si usa Gestione configurazione [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per aggiungere server e per aumentare il numero di istanze dei server di report. Con i prodotti SharePoint è possibile gestire la distribuzione con scalabilità orizzontale di Reporting Services in quanto i server SharePoint con il servizio [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] vengono aggiunti alla farm.  
  
 Per altre informazioni sul ridimensionamento dei server di report in modalità nativa, vedere [Configurare una distribuzione con scalabilità orizzontale di un server di report in modalità nativa &#40;Gestione configurazione SSRS&#41;](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md).  
  
-   [Bilanciamento del carico](#bkmk_loadbalancing)  
  
-   [Prerequisiti](#bkmk_prerequisites)  
  
-   [Passaggi](#bkmk_steps)  
  
-   [Configurazione aggiuntiva](#bkmk_additional)  
  
##  <a name="load-balancing"></a><a name="bkmk_loadbalancing"></a>Bilanciamento del carico  
 Il bilanciamento del carico di applicazioni del servizio [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] viene gestito automaticamente da SharePoint, a meno che nell'ambiente sia presente una soluzione di bilanciamento del carico personalizzata o di terze parti. Secondo il comportamento predefinito del bilanciamento del carico di SharePoint, ogni applicazione del servizio [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] viene bilanciata tra tutti i server applicazioni in cui è stato avviato il servizio [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Per verificare se il servizio [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è installato e avviato, fare clic su **Gestisci servizi nel server** in Amministrazione centrale SharePoint.  
  
##  <a name="prerequisites"></a><a name="bkmk_prerequisites"></a> Prerequisiti  
  
-   Per eseguire il programma di installazione di SQL Server, è necessario essere un amministratore locale.  
  
-   Il computer deve fare parte di un dominio.  
  
-   È inoltre necessario conoscere il nome del server di database esistente che ospita i database di configurazione e del contenuto di SharePoint.  
  
-   Il server di database deve essere configurato in modo da consentire le connessioni ai database remoti.  In caso contrario, non sarà possibile creare un join del nuovo server alla farm, in quanto il nuovo server non sarà in grado di stabilire una connessione ai database di configurazione di SharePoint.  
  
-   Nel nuovo server dovrà essere installata la stessa versione di SharePoint in esecuzione sui server della farm correnti. Se nella farm è già installato, ad esempio, SharePoint 2010 Service Pack 1 (SP1), sarà necessario installare SP1 anche nel nuovo server prima di poterne creare un join alla farm.  
  
-   Esaminare gli argomenti aggiuntivi seguenti per comprendere i requisiti relativi al sistema e alla versione:  
  
     [Guida per l'utilizzo delle funzionalità di Business Intelligence di SQL Server in una farm di SharePoint 2010](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
##  <a name="steps"></a><a name="bkmk_steps"></a>Passaggi  
 Nei passaggi di questo argomento si presuppone che l'installazione e la configurazione del server vengano eseguite da un amministratore della farm di SharePoint. Nel diagramma è illustrato un tipico ambiente a tre livelli e gli elementi numerati nel diagramma sono descritti nell'elenco seguente:  
  
-   (1) Più server front-end Web (WFE). I server front-end Web richiedono il componente aggiuntivo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per SharePoint 2010.  
  
-   (2) Un singolo server applicazioni che esegue [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e siti Web, ad esempio Amministrazione centrale. Nei passaggi seguenti viene aggiunto un secondo server applicazioni a questo livello.  
  
-   (3) Due server di database SQL Server.  
  
-   (4) Rappresenta una soluzione software o hardware di bilanciamento del carico di rete.  
  
 ![Aggiunta di un server applicazioni a Reporting Services](../../../2014/sql-server/install/media/rs-sharepointscale.gif "Aggiunta di un server applicazioni a Reporting Services")  
  
 Nei seguenti passaggi si presuppone che l'installazione e la configurazione del server vengano eseguite da un amministratore. Il server verrà configurato come nuovo server applicazioni nella farm e non verrà utilizzato come un front-end Web.  
  
|Passaggio|Descrizione e collegamento|  
|----------|--------------------------|  
|Eseguire l'Utilità preparazione prodotti SharePoint 2010.|È necessario disporre dei supporti di installazione di SharePoint 2010. L'utilità di preparazione corrisponde al file **PrerequisiteInstaller.exe** disponibile nei supporti di installazione.|  
|Installare un prodotto SharePoint 2010.|1) selezionare il tipo di installazione **server farm** .<br /><br /> 2) selezionare **completa** per il tipo di server.<br /><br /> 3) Una volta completata l'installazione, non eseguire la Configurazione guidata Prodotti SharePoint se nella farm di SharePoint esistente è installato SharePoint 2010 SP1. È necessario installare SharePoint SP1 prima di eseguire la Configurazione guidata Prodotti SharePoint.|  
|Installare SharePoint Server 2010 SP1.|Se nella farm di SharePoint esistente è installato SharePoint 2010 SP1, scaricare e installare SharePoint 2010 SP1[https://support.microsoft.com/kb/2460045](https://go.microsoft.com/fwlink/p/?linkID=219697)da:.<br /><br /> Per ulteriori informazioni su SharePoint 2010 SP1, vedere [Problemi noti durante l'installazione di Office 2010 SP1 e SharePoint 2010 SP1](https://support.microsoft.com/kb/2532126):|  
|Eseguire la Configurazione guidata Prodotti SharePoint per aggiungere il server alla farm.|1) nel gruppo di programmi **prodotti Microsoft sharepoint 2010** fare clic su **Configurazione guidata prodotti Microsoft SharePoint 2010**.<br /><br /> 2) nella pagina **connessione a una server farm** selezionare **Connetti a una farm esistente** e fare clic su **Avanti**.<br /><br /> 3) nella pagina **specifica impostazioni database di configurazione** Digitare il nome del server di database utilizzato per la farm esistente e il nome del database di configurazione. Fare clic su **Avanti**.<br />** \* Importante \* \* ** Se viene visualizzato un messaggio di errore simile al seguente ed è stata verificata l'autorizzazione, verificare che i protocolli siano abilitati per la configurazione di rete SQL Server in **SQL server Configuration Manager**: "Impossibile connettersi al server di database. Verificare che il database esista, che sia un server SQL e di disporre delle autorizzazioni appropriate per accedere al server. "<br />** \* Importante \* \* ** Se viene visualizzata la pagina relativa **allo stato della patch e del prodotto della server farm**, sarà necessario esaminare le informazioni nella pagina e aggiornare il server con i file necessari prima di poter procedere con l'aggiunta del server alla farm.<br /><br /> 4) nella pagina **specifica impostazioni sicurezza farm** Digitare la passphrase della farm e fare clic su **Avanti**. Scegliere **Avanti** nella pagina di configurazione per eseguire la procedura guidata.<br /><br /> 5) fare clic su **Avanti** per eseguire la **Configurazione guidata della farm**.|  
|Verificare che il server sia stato aggiunto alla farm di SharePoint.|1) Nel gruppo **Impostazioni di sistema** di Amministrazione centrale SharePoint fare clic su **Gestisci server della farm** .<br /><br /> 2) Verificare che il nuovo server sia stato aggiunto e che lo stato sia corretto.<br /><br /> 3) si noti che il servizio **SQL Server Reporting Services** di servizio non è in esecuzione. Verrà installato nel passaggio successivo.<br /><br /> 4) per rimuovere questo server dal ruolo WFE, fare clic su **Gestisci servizi nel server** e arrestare il servizio **applicazione Web Microsoft SharePoint Foundation**.|  
|Installare e configurare la modalità SharePoint di Reporting Services|Eseguire il programma di installazione di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Per ulteriori informazioni sull'installazione della modalità [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint di, vedere [Install Reporting Services modalità sharepoint per SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md) se il server verrà utilizzato solo come server applicazioni e il server non verrà utilizzato come WFE, non è necessario selezionare **Reporting Services componente aggiuntivo per prodotti SharePoint** in:<br /><br /> nella pagina **impostazione ruolo** selezionare **Installazione funzionalità SQL Server**<br /><br /> la pagina **Selezione funzionalità** selezionare **Reporting Services-SharePoint**<br /><br /> -OPPURE-<br /><br /> la pagina **configurazione Reporting Services** verificare che sia selezionata l'opzione **solo installazione** per **Reporting Services modalità SharePoint**.|  
|Verificare che Reporting Services sia operativo.|1) Nel gruppo **Impostazioni di sistema** di Amministrazione centrale SharePoint fare clic su **Gestisci server della farm** .<br /><br /> 2) Verificare il **Servizio SQL Server Reporting Services**.<br /><br /> Per altre informazioni, vedere [verificare un'installazione di Reporting Services](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)|  
  
##  <a name="additional-configuration"></a><a name="bkmk_additional"></a>Configurazione aggiuntiva  
 È possibile ottimizzare singoli server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in una distribuzione con scalabilità orizzontale solo per eseguire l'elaborazione in background, in modo da non condividere le risorse con esecuzione interattiva del report. Nell'elaborazione in background sono incluse pianificazioni, sottoscrizioni e avvisi dati.  
  
 Per modificare il comportamento dei singoli server di report, impostare ** \<IsWebServiceEnable>** su false nel file di configurazione **RSReportServer. config** .  
  
 Per impostazione predefinita, i server di report vengono configurati con \<IsWebServiceEnable> impostato su TRUE. Quando tutti i server sono configurati per TRUE, l'elaborazione interattiva e in background sarà con carico bilanciato in tutti i nodi nella farm.  
  
 Se si configurano tutti i server di report con \<IsWebServiceEnable> impostato su False, verrà visualizzato un messaggio di errore simile al seguente quando si tenterà di usare le funzionalità di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]:  
  
 Il servizio Web Reporting Services non è abilitato. Configurare almeno un'istanza del servizio Reporting Services SharePoint affinché \<IsWebServiceEnable> impostato su true. Per ulteriori informazioni, vedere la pagina relativa alla [modifica di un file di configurazione Reporting Services &#40;RSReportServer. config&#41;](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)  
  
## <a name="see-also"></a>Vedi anche  
 [Aggiungere server Web o applicazioni alle farm in SharePoint 2013](https://technet.microsoft.com/library/cc261752.aspx)   
 [Configurare i servizi (SharePoint Server 2010)](https://technet.microsoft.com/library/ee794878.aspx)  
  
  
