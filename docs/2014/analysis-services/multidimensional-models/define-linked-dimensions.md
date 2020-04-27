---
title: Definire le dimensioni collegate | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], linked
- linked dimensions [Analysis Services]
ms.assetid: d5ad5eae-5dde-46a6-91c3-c8766d016dec
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ca4b3c0b2f2a6c63e62a44499d6e33e651ca9bae
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66075582"
---
# <a name="define-linked-dimensions"></a>Definizione delle dimensioni collegate
  Una dimensione collegata è basata su una dimensione creata e archiviata in un altro database di Analysis Services con la stessa versione e lo stesso livello di compatibilità. Utilizzando una dimensione collegata è possibile creare, archiviare e mantenere una dimensione in un database facendo in modo che tale dimensione sia disponibile per gli utenti di più database. Per gli utenti una dimensione collegata ha lo stesso aspetto di qualsiasi altra dimensione.  
  
 Le dimensioni collegate sono di sola lettura. Se si desidera modificare la dimensione o creare nuove relazioni, è necessario modificare la dimensione di origine, quindi eliminare e ricreare la dimensione collegata e le sue relazioni. Non è possibile aggiornare una dimensione collegata per visualizzare le modifiche dell'oggetto di origine.  
  
 Tutte le dimensioni e i gruppi di misure correlati devono provenire dallo stesso database di origine. Non è possibile creare nuove relazioni tra i gruppi di misure locali e le dimensioni collegate che si aggiungono al cubo. In seguito all'aggiunta di dimensioni collegate e gruppi di misure al cubo attuale, è necessario conservare le relazioni tra essi nel corrispondente database di origine.  
  
> [!NOTE]  
>  Poiché l'aggiornamento non è disponibile, molti sviluppatori di Analysis Services copiano le dimensioni anziché collegarle. È possibile copiare dimensioni tra i diversi progetti della stessa soluzione. Per altre informazioni, vedere la pagina [Refresh of a linked dimension in SSAS](http://sqlblog.com/blogs/marco_russo/archive/2006/09/12/refresh-of-a-linked-dimension-in-ssas.aspx)(Aggiornamento di una dimensione collegata in SSAS).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Il database di origine che fornisce la dimensione e il database corrente che la utilizza devono essere della stessa versione e dello stesso livello di compatibilità. Per ulteriori informazioni, vedere [impostare il livello di compatibilità di un database multidimensionale &#40;Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md).  
  
 Il database di origine deve essere distribuito e online. È necessario configurare i server che pubblicano o utilizzano oggetti collegati per consentire l'operazione (vedere sotto).  
  
 La dimensione che si desidera utilizzare non può essere una dimensione collegata.  
  
## <a name="configure-server-to-allow-linked-objects"></a>Configurare il server per consentire oggetti collegati  
  
1.  In SQL Server Management Studio, connettersi a un server Analysis Services. In Esplora oggetti fare clic con il pulsante destro del mouse sul nome del server e selezionare **Facet**.  
  
2.  Impostare **LinkedObjectsLinksFromOtherInstancesEnabled** su **True** per consentire che il server generi richieste per oggetti collegati che si trovano in database in esecuzione su altre istanze.  
  
3.  Impostare **LinkedObjectsLinksToOtherInstances** su **True** per consentire al server di richiedere i dati per i database collegati in esecuzione in altre istanze.  
  
## <a name="create-a-linked-dimension-in-sql-server-data-tools"></a>Creare una dimensione collegata in SQL Server Data Tools  
  
1.  Avviare la procedura guidata. In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]fare clic con il pulsante destro del mouse sulla cartella **Dimensioni** in un database o un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , quindi scegliere **Nuova dimensione collegata**.  
  
2.  Connettersi al database di Analysis Services che fornisce la dimensione. Nella pagina **Selezione origine dati** del Collegamento guidato oggetti scegliere l'origine dei dati di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oppure crearne una nuova.  
  
3.  Nella pagina **Seleziona oggetti** della procedura guidata scegliere le dimensioni a cui collegarsi nel database remoto.  
  
4.  Nella pagina **Completamento procedura guidata** è possibile visualizzare l'anteprima degli oggetti collegati. In caso di collegamento a una dimensione con lo stesso nome di una dimensione esistente, al nome verrà associato un numero ordinale a partire da '1' per il primo nome duplicato. Dopo il completamento della procedura guidata la dimensione viene aggiunta alla cartella **Dimensioni** .  
  
##  <a name="create-a-new-data-source-connection-to-an-analysis-services-database"></a><a name="bkmk_CreateNew"></a> Creare una nuova connessione di origine dati a un database di Analysis Services  
 Utilizzare la procedura guidata Nuova origine dati per aggiungere informazioni sul database di Analysis Services che fornisce la dimensione alla connessione del progetto. È possibile avviare la procedura guidata facendo clic su **Nuova origine dati** nella pagina Selezione origine dati del Collegamento guidato oggetti.  
  
1.  Nella pagina Selezione metodo di definizione connessione della Creazione guidata origine dati fare clic su **Nuovo**.  
  
2.  In Gestione connessione, verificare che il provider sia impostato su **Provider OLE DB\Microsoft OLE DB nativo per Analysis Services 11.0**.  
  
3.  Immettere il nome del server (utilizzare *ServerName*\\*NomeIstanza* per un'istanza denominata)<sup>1</sup> o digitare **localhost** per connettersi a un Analysis Services server in esecuzione nello stesso computer.  
  
4.  Utilizzare l'autenticazione di Windows per la connessione.  
  
5.  In **Catalogo iniziale**, fare clic sulla freccia GIÙ per selezionare un database in questo server.  
  
6.  Nella Creazione guidata origine dati fare clic su **Avanti** per continuare.  
  
7.  Nella pagina Impostazioni di rappresentazione, fare clic su **Usa account del servizio**. Fare clic su **Avanti**e terminare la procedura guidata. La connessione appena definita verrà selezionata nel Collegamento guidato oggetti.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Non è possibile modificare la struttura di una dimensione collegata e per questo motivo non è possibile visualizzarla nella scheda **Struttura dimensione** di Progettazione dimensioni. Dopo l'elaborazione della dimensione collegata, è possibile visualizzarla nella scheda **esplorazione** . È anche possibile modificare il nome e creare una traduzione per il nome.  
  
## <a name="see-also"></a>Vedi anche  
 [Impostazione del livello di compatibilità di un database multidimensionale &#40;Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md)   
 [Gruppi di misure collegati](linked-measure-groups.md)   
 [Relazioni tra dimensioni](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)  
  
  
