---
title: Creare e gestire una partizione remota (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- partitions [Analysis Services], remote
- remote partitions [Analysis Services]
ms.assetid: 4322b5cb-af07-4e79-8ecb-59e1121a9eb8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fd074e705c5ae135eb8161a0ea5d2919d1c183e1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66076259"
---
# <a name="create-and-manage-a-remote-partition-analysis-services"></a>Creare e gestire una partizione remota (Analysis Services)
  In caso di partizionamento di un gruppo di misure, è possibile configurare un database secondario in un'istanza remota di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] come archiviazione della partizione.  
  
 Le partizioni remote per un cubo, denominato database master, vengono archiviate in un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dedicato nell'istanza remota di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , denominato database secondario.  
  
 Un database secondario dedicato può archiviare partizioni remote per un solo database master, ma il database master può utilizzare più database secondari, purché si trovino tutti nella stessa istanza remota di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Le dimensioni in un database dedicato a partizioni remote vengono create come dimensioni collegate.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Prima di creare una partizione remota, è necessario che siano soddisfatte le condizioni seguenti:  
  
-   È necessario disporre di una seconda istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e di un database dedicato per archiviare partizioni. Il database secondario è finalizzato a un unico scopo: fornire l'archiviazione di partizioni remote per un database master.  
  
-   Entrambe le istanze del server devono essere della stessa versione. Entrambi i database devono essere dello stesso livello funzionale.  
  
-   Entrambe le istanze devono essere configurate per le connessioni TCP. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] non è supportata la creazione di partizioni remote tramite il protocollo HTTP.  
  
-   Le impostazioni del firewall in entrambi i computer devono essere impostate per accettare connessioni esterne. Per altre informazioni sull'impostazione del firewall, vedere [Configurare Windows Firewall per consentire l'accesso ad Analysis Services](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
-   L'account di servizio per l'istanza che esegue il database master deve disporre dei diritti di accesso di amministratore all'istanza remota di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Se l'account di servizio cambia, è necessario aggiornare le autorizzazioni sia nel server che nel database.  
  
-   È necessario essere un amministratore [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in entrambi i computer.  
  
-   È necessario verificare che il piano di ripristino di emergenza preveda il backup e il ripristino delle partizioni remote. L'utilizzo di partizioni remote può complicare le operazioni di backup e ripristino. Controllare approfonditamente il piano in modo da verificare che sia possibile ripristinare i dati necessari.  
  
## <a name="configure-remote-partitions"></a>Configurare partizioni remote  
 Due computer distinti in cui è in esecuzione un' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] istanza di sono necessari per creare una disposizione di partizione remota che designa un computer come server master e l'altro computer come server subordinato.  
  
 Nella procedura indicata di seguito si presuppone che siano presenti due istanze del server, con un database del cubo distribuito nel server master. Ai fini di questa procedura, il database del cubo viene definito come db-master. Il database di archiviazione contenente le partizioni remote viene definito come db-storage.  
  
 Utilizzare sia [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] che [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] per completare questa procedura.  
  
> [!NOTE]  
>  Le partizioni remote possono essere unite solo ad altre partizioni remote. Se si utilizza una combinazione di partizioni remote e locali, un approccio alternativo consiste nel creare nuove partizioni contenenti dati combinati, eliminando quelle non più in uso.  
  
#### <a name="specify-valid-server-names-for-cube-deployment-in-ssdt"></a>Specificare nomi di server validi per la distribuzione del cubo (in SSDT)  
  
1.  Nel server master: in Esplora soluzioni fare clic con il pulsante destro del mouse sul nome della soluzione e scegliere **Proprietà**. Nella finestra di dialogo **Proprietà** fare clic su **Proprietà di configurazione**, **Distribuzione**e **Server** , quindi impostare il nome del server master.  
  
2.  Nel server subordinato: in Esplora soluzioni fare clic con il pulsante destro del mouse sul nome della soluzione e scegliere **Proprietà**. Nella finestra di dialogo **Proprietà** fare clic su **Proprietà di configurazione**, **Distribuzione**e **Server** , quindi impostare il nome del server subordinato.  
  
#### <a name="create-and-deploy-a-secondary-database-in-ssdt"></a>Creare e distribuire un database secondario (in SSDT)  
  
1.  Nel server subordinato: creare un nuovo progetto Analysis Services per il database di archiviazione.  
  
2.  Nel server subordinato: in Esplora soluzioni crea una nuova origine dati che punti al database del cubo, db-master. Usare il provider **OLE DB nativo\Microsoft OLE DB per Analysis Services 11.0**.  
  
3.  Nel server subordinato: distribuire la soluzione.  
  
#### <a name="enable-features-in-ssms"></a>Abilitare funzionalità (in SSMS)  
  
1.  Nel server subordinato: in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]fare clic con il pulsante destro del mouse sull'istanza connessa di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in Esplora oggetti e scegliere **Proprietà**. Impostare entrambe le proprietà **Feature\LinkToOtherInstanceEnabled** e **Feature\LinkFromOtherInstanceEnabled** su **True**.  
  
2.  Nel server subordinato: riavviare il server facendo clic con il pulsante destro del mouse sul nome del server in Esplora oggetti e scegliendo **Riavvia**.  
  
3.  Nel server master: in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]fare clic con il pulsante destro del mouse sull'istanza connessa di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in Esplora oggetti e scegliere **Proprietà**. Impostare entrambe le proprietà **Feature\LinkToOtherInstanceEnabled** e **Feature\LinkFromOtherInstanceEnabled** su **True**.  
  
4.  Nel server master: per riavviare il server, fare clic con il pulsante destro del mouse sul nome del server in Esplora oggetti e scegliere **Riavvia**.  
  
#### <a name="set-the-masterdatasourceid-database-property-on-the-remote-server-in-ssms"></a>Impostare la proprietà di database MasterDataSourceID nel server remoto (in SSMS)  
  
1.  Nel server subordinato: fare clic con il pulsante destro del mouse sul database di archiviazione, DB-storage, scegliere Crea **script per database come** | **ALTER in** | **nuova finestra Editor di query**.  
  
2.  Aggiungere **MasterDataSourceID** al codice XMLA e quindi specificare l'ID del database del cubo, db-master, come valore. Il codice XMLA dovrebbe essere simile a quello riportato di seguito.  
  
    ```  
    <Alter ObjectExpansion="ExpandFull" xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
       <DatabaseID>DB-Storage</DatabaseID>  
    </Object>  
    <ObjectDefinition>  
       <Database xmlns:xsd="http://www.w3.org/2001/XMLSchema" 400"   
          <ID>DB-Storage</ID>  
          <Name>DB-StorageB</Name>  
          <ddl200:CompatibilityLevel>1100</ddl200:CompatibilityLevel>  
          <Language>1033</Language>  
          <Collation>Latin1_General_CI_AS</Collation>  
          <DataSourceImpersonationInfo>  
    <ImpersonationMode>ImpersonateAccount</ImpersonationMode>  
             <Account>*********</Account>  
          </DataSourceImpersonationInfo>  
          <MasterDataSourceID>DB-Master</MasterDataSourceID>  
       </Database>  
    </ObjectDefinition>  
    </Alter>  
    ```  
  
3.  Premere F5 per eseguire lo script.  
  
#### <a name="set-up-the-remote-partition-in-ssdt"></a>Configurare la partizione remota (in SSDT)  
  
1.  Nel server master: aprire il cubo in Progettazione cubi e fare clic sulla scheda **partizioni** . espandere il gruppo di misure. Fare clic su **Nuova partizione** se il gruppo di misure è già configurato per più partizioni oppure fare clic sul pulsante Sfoglia (. . ) nella colonna Origine per modificare la partizione esistente.  
  
2.  In **Impostazione informazioni origine**della Creazione guidata partizione selezionare la vista origine dati originale e la tabella dei fatti.  
  
3.  Se si utilizza un'associazione di query, specificare una clausola WHERE che segmenti i dati per la nuova partizione in fase di creazione.  
  
4.  In **Posizioni di elaborazione e archiviazione**, in **Percorso di elaborazione**, selezionare **Origine dati remota di Analysis Services** e fare clic su **Nuovo** per creare una nuova origine dati che punti al database subordinato, db-storage.  
  
    > [!NOTE]  
    >  Se viene visualizzato un errore che indica che l'origine dati non è presente nella raccolta, è necessario aprire il progetto del database di archiviazione, db-storage, e creare un'origine dati che punti al database master, db-master.  
  
5.  Nel server master: fare clic con il pulsante destro del mouse sul nome del cubo in Esplora soluzioni, scegliere **Elabora** ed elaborare completamente il cubo.  
  
## <a name="administering-remote-partitions"></a>Amministrazione di partizioni remote  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sono supportate sia l'elaborazione parallela sia quella sequenziale di partizioni remote. Nel database master, ovvero dove sono state definite le partizioni, vengono coordinate le transazioni fra tutte le istanze che partecipano all'elaborazione delle partizioni di un cubo. I report di elaborazione vengono inviati quindi a tutte le istanze in cui è stata elaborata una partizione.  
  
 Un cubo contenente partizioni remote può essere amministrato insieme alle relative partizioni in una singola istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Tuttavia, i metadati per la partizione remota possono essere visualizzati e aggiornati solo nell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dove la partizione e il relativo cubo padre sono stati definiti. La partizione remota non può essere visualizzata o aggiornata nell'istanza remota di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
> [!NOTE]  
>  Anche se database dedicati all'archiviazione di partizioni remote non sono esposti a set di righe dello schema, le applicazioni in cui viene utilizzata la libreria AMO (Analysis Management Objects) possono ancora individuare un database dedicato utilizzando il comando di individuazione (Discover) di XML for Analysis. Un comando CREATE o DELETE inviato direttamente a un database dedicato tramite un client TCP o HTTP avrà esito positivo, tuttavia verrà restituito un avviso dal server indicante che l'azione può danneggiare notevolmente questo database gestito.  
  
## <a name="see-also"></a>Vedi anche  
 [Partizioni &#40;Analysis Services - Dati multidimensionali&#41;](../multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
