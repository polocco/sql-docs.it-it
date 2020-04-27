---
title: 'Lezione 13: analizzare in Excel | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ce717071-193b-4c99-9654-c7a613e16327
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6a1564a2b190703e011624162ad4bc25fd5de794
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66079185"
---
# <a name="lesson-13-analyze-in-excel"></a>Lezione 13: Analizza in Excel
  In questa lezione verrà utilizzata la funzionalità Analizza in Excel di [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] per aprire Microsoft Excel, creare automaticamente una connessione all'origine dati nell'area di lavoro del modello e aggiungere automaticamente una tabella pivot al foglio di lavoro. La funzionalità Analizza in Excel è progettata per offrire un modo rapido e semplice per testare l'efficacia della progettazione del modello prima di distribuirlo. Non si eseguirà alcuna analisi dei dati in questa lezione. Lo scopo è invece quello di permettere agli autori di modelli di acquisire familiarità con gli strumenti disponibili per testare la progettazione del modello. A differenza dell'utilizzo della funzionalità Analizza in Excel, destinata agli autori di modelli, gli utenti finali utilizzeranno applicazioni di creazione report client quali Excel o [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] per connettersi e sfogliare i dati del modello distribuito.  
  
 Per completare questa lezione, è necessario che Excel sia installato nello stesso computer di [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Per i dettagli, vedere [Analizzare in Excel &#40;SSAS tabulare&#41;](tabular-models/analyze-in-excel-ssas-tabular.md).  
  
 Tempo previsto per il completamento della lezione: **20 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  
 Questo argomento fa parte di un'esercitazione sulla creazione di modelli tabulari, con lezioni che è consigliabile completare nell'ordine indicato. Prima di eseguire le attività in questa lezione è necessario aver completato la lezione precedente: [Lezione 11: Creare partizioni](lesson-10-create-partitions.md).  
  
## <a name="browse-using-the-default-and-internet-sales-perspectives"></a>Esplorare il modello usando la prospettiva predefinita e la prospettiva Internet Sales  
 In queste prime attività, si sfoglierà il modello tramite la prospettiva predefinita che include tutti gli oggetti modello e tramite la prospettiva Internet Sales creata nella Lezione 8: Creare prospettive. La prospettiva Internet Sales esclude l'oggetto Customer table.  
  
#### <a name="to-browse-by-using-the-default-perspective"></a>Per esplorare il modello con la prospettiva predefinita  
  
1.  In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]fare clic sul menu **Modello** e quindi scegliere **Analizza in Excel**.  
  
2.  Nella finestra di dialogo **Analizza in Excel** fare clic su **OK**.  
  
     Excel verrà aperto con una nuova cartella di lavoro. Viene creata una connessione all'origine dati utilizzando l'account utente corrente e la prospettiva predefinita viene utilizzata per definire campi visualizzabili. Una tabella pivot viene aggiunta automaticamente al foglio di lavoro.  
  
3.  Nell'elenco di campi della **tabella pivot**in Excel si notino le misure **date** e **Internet Sales** , nonché le tabelle **Customer**, **date**, **geography**, **Product**, Product **Category**, **Product Subcategory**e **Internet Sales** con tutte le rispettive colonne.  
  
4.  Chiudere Excel senza salvare la cartella di lavoro.  
  
#### <a name="to-browse-by-using-the-internet-sales-perspective"></a>Per esplorare il modello con la prospettiva Internet Sales  
  
1.  In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]fare clic sul menu **Modello** e quindi scegliere **Analizza in Excel**.  
  
2.  Nella finestra di dialogo **Analizza in Excel** lasciare selezionata l'opzione **Utente di Windows corrente** , quindi nell'elenco a discesa **Prospettiva** selezionare **Internet Sales**e fare clic su **OK**. Verrà aperto Excel.  
  
3.  In **Elenco campi tabella pivot**di Excel notare che la tabella Customer è esclusa dall'elenco dei campi.  
  
## <a name="browse-using-roles"></a>Sfogliare il modello utilizzando i ruoli  
 I ruoli sono una parte integrante di qualsiasi modello tabulare. Senza almeno un ruolo, a cui gli utenti vengono aggiunti come membri, gli utenti non saranno in grado di accedere e analizzare i dati utilizzando il modello. La funzionalità Analizza in Excel consente di testare i ruoli che sono stati definiti dall'utente.  
  
#### <a name="to-browse-by-using-the-internet-sales-manager-user-role"></a>Per sfogliare il modello tramite il ruolo utente Internet Sales Manager  
  
1.  In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]fare clic sul menu **Modello** e quindi scegliere **Analizza in Excel**.  
  
2.  Nella finestra di dialogo **Analizza in Excel** , in **Specificare il nome utente o il ruolo da utilizzare per connettersi al modello**, selezionare **Ruolo**, quindi nell'elenco a discesa selezionare **Internet Sales Manager**e fare clic su **OK**.  
  
     Excel verrà aperto con una nuova cartella di lavoro. Verrà creata automaticamente una tabella pivot. L'elenco di campi tabella pivot include tutti i campi dati disponibili nel nuovo modello.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Per continuare questa esercitazione, passare alla lezione successiva: [Lezione 14: Distribuire](lesson-13-deploy.md).  
  
  
