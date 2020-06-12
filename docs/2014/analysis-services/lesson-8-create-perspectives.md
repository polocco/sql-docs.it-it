---
title: 'Lezione 9: creare prospettive | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 55b0f0d0-1cdf-4876-9c3d-d0c848be3f5d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 20601a1ece7707e8f798907f21ee5ee7110fe2fe
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2020
ms.locfileid: "84542223"
---
# <a name="lesson-9-create-perspectives"></a>Lezione 9: Creare prospettive
  In questa lezione verrà creata una prospettiva Internet Sales. Una prospettiva definisce un subset visualizzabile di un modello che offre punti di vista mirati, specifici di un'azienda o specifici di un'applicazione. Quando un utente si connette a un modello tramite una prospettiva, vengono visualizzati solo gli oggetti del modello (tabelle, colonne, misure, gerarchie e KPI) come campi definiti in tale prospettiva.  
  
 La prospettiva Internet Sales creata in questa lezione escluderà l'oggetto Customer table. Quando si crea una prospettiva che esclude determinati oggetti dalla visualizzazione, tali oggetti sono ancora presenti nel modello; tuttavia non sono visibili in un elenco di campi di un client di creazione di report. Le colonne e le misure calcolate incluse o meno in una prospettiva consentono ancora eseguire calcoli da dati di oggetto esclusi.  
  
 Lo scopo di questa lezione è quello di descrivere come creare prospettive e di consentire di acquisire familiarità con gli strumenti di creazione di modelli tabulari. Se successivamente si espande questo modello per includere tabelle aggiuntive, è possibile creare ulteriori prospettive per definire punti di vista diversi del modello, ad esempio relativi a inventario e forza vendita.  
  
 Per altre informazioni, vedere [Prospettive &#40;SSAS tabulare&#41;](tabular-models/perspectives-ssas-tabular.md).  
  
 Tempo stimato per il completamento della lezione: **5 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  
 Questo argomento fa parte di un'esercitazione sulla creazione di modelli tabulari, con lezioni che è consigliabile completare nell'ordine indicato. Prima di eseguire le attività in questa lezione, è necessario aver completato la lezione precedente: [Lezione 8: Creare indicatori di prestazioni chiave](lesson-7-create-key-performance-indicators.md).  
  
## <a name="create-perspectives"></a>Creare prospettive  
  
#### <a name="to-create-an-internet-sales-perspective"></a>Per creare una prospettiva Internet Sales  
  
1.  In Progettazione modelli fare clic sul menu **modello** , quindi fare clic su **prospettive**.  
  
2.  Nella finestra di dialogo **Prospettive** fare clic su **Nuova prospettiva**.  
  
3.  Per rinominare la prospettiva, fare doppio clic sull'intestazione di colonna **nuova prospettiva 1** , quindi digitare `Internet Sales` .  
  
4.  In **campi**selezionare le seguenti tabelle **date**, **geography**, **Product**, Product **Category**, **Product Subcategory**e `Internet Sales` .  
  
     Si noti che sono state escluse la tabella Customer e tutte le colonne relative da questa prospettiva. In un secondo momento, nella Lezione 12 si utilizzerà la funzionalità Analizza in Excel per testare questa prospettiva. L'elenco campi tabella pivot di Excel includerà ogni tabella a eccezione di Customer.  
  
5.  Verificare le selezioni, assicurandosi che la tabella **Customer** non sia selezionata e fare clic su **OK**.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Per continuare questa esercitazione, passare alla lezione successiva: [Lezione 10: Creare gerarchie](lesson-9-create-hierarchies.md).  
  
  
