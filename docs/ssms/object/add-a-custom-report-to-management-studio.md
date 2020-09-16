---
description: Aggiunta di un report personalizzato a Management Studio
title: Aggiunta di un report personalizzato a Management Studio
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 3cf8d726-0a90-4f80-98d0-352a2a59be0f
author: markingmyname
ms.author: maghan
ms.openlocfilehash: aa920b620cfa0045228fcdb5675c1e88bc7ab035
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88480167"
---
# <a name="add-a-custom-report-to-management-studio"></a>Aggiunta di un report personalizzato a Management Studio
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
In questo argomento viene descritto come creare un report semplice di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] salvato come file con estensione rdl e quindi aggiungere tale file a [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] come report personalizzato. [!INCLUDE[ssRS](../../includes/ssrs.md)] consente di creare una vasta gamma di sofisticati report. Per creare un report in base a questo argomento, è necessario che nel computer sia installato [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull_md.md)] . Per eseguire un report personalizzato mediante [!INCLUDE[ssRS](../../includes/ssrs.md)] non è necessario installare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
 
### <a name="to-create-a-simple-report-saved-as-an-rdl-file"></a>Per creare un report semplice salvato come file con estensione rdl  
  
1.  Fare clic su **Start**, scegliere **Tutti i programmi**, **Microsoft SQL Server**e fare clic su **SQL Server Data Tools**.  
  
2.  Scegliere **Nuovo** dal menu **File**e quindi fare clic su **Progetto**.  
  
3.  Nell'elenco **Tipi progetto** fare clic su **Progetti Business Intelligence**.  
  
4.  Nell'elenco **Modelli** fare clic su **Creazione guidata progetto server di report**.  
  
5.  In **Nome**digitare **ReportConnessioni**e fare clic su **OK**.  
  
6.  Nella pagina introduttiva di **Creazione guidata report** fare clic su **Avanti**.  
  
7.  Nella casella Nome della pagina **Selezione origine dati** digitare un nome per la connessione a [!INCLUDE[ssDE](../../includes/ssde_md.md)]e fare clic su **Modifica**.  
  
8.  Nella casella **Nome server** della finestra di dialogo **Proprietà connessione** digitare il nome dell'istanza di [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
9. Nella casella **Selezionare o immettere un nome di database** digitare il nome di uno dei database presenti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], e fare clic su **OK**.  
  
10. Nella pagina **Selezione origine dati** fare clic su **Avanti**.  
  
11. Nella casella **Stringa query** della pagina **Progettazione query** digitare l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente, che elenca le connessioni correnti a [!INCLUDE[ssDE](../../includes/ssde_md.md)]e fare clic su **Avanti**. Nella casella Stringa query della Creazione guidata report non è possibile immettere parametri di report. La creazione di report personalizzati più complessi dovrà essere eseguita manualmente.  
  
    **SELECT session_id, net_transport FROM sys.dm_exec_connections;**  
  
12. Nella pagina **Selezione tipo di report** selezionare **Tabulare**e fare clic su **Fine**.  
  
13. Nella pagina **Completamento procedura guidata** digitare **ReportConnessioni** nella casella **Nome report**e fare clic su **Fine** per creare e salvare il report.  
  
14. Chiudere [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
15. Copiare **ReportConnessioni.rdl** in una cartella creata nel server di database per i report personalizzati.  
  
### <a name="to-add-a-report-to-management-studio"></a>Per aggiungere un report a Management Studio  
  
-   In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]fare clic con il pulsante destro del mouse su un nodo in Esplora oggetti, scegliere **Report**e fare clic su **Report personalizzati**. Nella finestra di dialogo **Apri file** individuare la cartella dei report personalizzati, selezionare il file **ReportConnessioni.rdl** e fare clic su **Apri**.  
  
    Alla prima apertura di un nuovo report personalizzato da un nodo Esplora oggetti, tale report verrà aggiunto all'elenco degli ultimi elementi usati in **Report personalizzati** nel menu di scelta rapida del nodo. Analogamente, alla prima apertura, anche un report standard verrà aggiunto all'elenco degli ultimi elementi usati in **Report personalizzati**. Se viene eliminato un file di un report personalizzato, alla successiva selezione dell'elemento verrà visualizzato un messaggio che chiederà di eliminare la relativa voce dall'elenco degli ultimi elementi utilizzati.  
  
    1.  Per modificare il numero dei file visualizzati nell'elenco degli ultimi elementi usati, scegliere **Opzioni** dal menu **Strumenti** , espandere la cartella **Ambiente** e fare clic su **Generale**.  
  
    2.  Modificare il numero in **Display files in recently used list**(Visualizza file nell'elenco degli ultimi file usati).  
  
## <a name="see-also"></a>Vedere anche  
[Report personalizzati in Management Studio](../../ssms/object/custom-reports-in-management-studio.md)  
[Usare report personalizzati con proprietà dei nodi di Esplora oggetti](../../ssms/object/use-custom-reports-with-object-explorer-node-properties.md)  
[Visualizzazione di avvisi relativi all'esecuzione di report personalizzati](../../ssms/object/unsuppress-run-custom-report-warnings.md)  
[SQL Server Reporting Services](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
