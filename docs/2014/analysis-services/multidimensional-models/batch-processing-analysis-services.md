---
title: Elaborazione batch (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- batches [Analysis Services]
ms.assetid: ba4dcf72-0667-41d0-816b-ab8ff9a7d9cb
author: minewiskan
ms.author: owend
ms.openlocfilehash: cb5ef5f0f9d662f66b9fb3203e518316d87c21b9
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544623"
---
# <a name="batch-processing-analysis-services"></a>Elaborazione batch (Analysis Services)
  In [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]è possibile utilizzare il comando Batch per inviare al server più comandi di elaborazione in una sola richiesta. Tramite l'elaborazione batch è possibile determinare gli oggetti da elaborare e l'ordine di elaborazione. Un batch può inoltre essere eseguito come una serie di processi autonomi o come una transazione nella quale l'esito negativo di un processo causa il rollback dell'intero batch.  
  
 L'elaborazione batch consente di aumentare al massimo la disponibilità dei dati consolidando e riducendo la quantità di tempo necessaria per eseguire il commit delle modifiche. Quando una dimensione viene elaborata completamente, qualsiasi partizione in cui viene utilizzata tale dimensione viene contrassegnata come non elaborata e, di conseguenza, i cubi contenenti le partizioni non elaborate non sono disponibili per l'esplorazione. È possibile ottenere questo risultato con un processo di elaborazione batch elaborando le dimensioni insieme alle partizioni interessate. L'esecuzione del processo di elaborazione batch come transazione consente di verificare che tutti gli oggetti inclusi nella transazione rimangano disponibili per l'esecuzione di query fino al completamento dell'elaborazione. Durante il commit delle modifiche da parte della transazione, vengono applicati blocchi agli oggetti interessati, rendendoli temporaneamente non disponibili; tuttavia il tempo necessario per eseguire il commit delle modifiche è inferiore rispetto a quello per elaborare singolarmente gli oggetti.  
  
 Nelle procedure di questo argomento vengono illustrati i passaggi per l'elaborazione completa di dimensioni e partizioni. L'elaborazione batch può includere anche altre opzioni di elaborazione, ad esempio l'elaborazione incrementale. Per il corretto funzionamento di queste procedure, è consigliabile utilizzare un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] esistente contenente almeno due dimensioni e una partizione.  
  
 Questo argomento include le sezioni seguenti:  
  
 [Elaborazione batch in SQL Server Data Tools](#bkmk_ssdt)  
  
 [Elaborazione batch con XMLA in Management Studio](#bkmk_xmla)  
  
##  <a name="batch-processing-in-sql-server-data-tools"></a><a name="bkmk_ssdt"></a> Elaborazione batch in SQL Server Data Tools  
 Prima di poter elaborare gli oggetti in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], è necessario distribuire il progetto contenente gli oggetti. Per altre informazioni, vedere [Distribuire progetti di Analysis Services &#40;SSDT&#41;](deploy-analysis-services-projects-ssdt.md).  
  
1.  Aprire [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
2.  Aprire un progetto che è stato distribuito.  
  
3.  In Esplora soluzioni espandere la cartella **Dimensioni** del progetto distribuito.  
  
4.  Tenendo premuto il tasto CTRL, fare clic su ogni dimensione elencata in **Dimensioni** .  
  
5.  Fare clic con il pulsante destro del mouse sulle dimensioni selezionate, quindi scegliere **Elabora**.  
  
6.  Tenendo premuto il tasto CTRL, fare clic su ogni dimensione elencata in **Elenco oggetti**.  
  
7.  Fare clic con il pulsante destro del mouse sulle dimensioni selezionate, quindi scegliere **Elaborazione completa**.  
  
8.  Per personalizzare il processo batch, fare clic su **Cambia impostazioni**.  
  
9. In **Opzioni di elaborazione**contrassegnare le impostazioni seguenti:  
  
    -   **Ordine di elaborazione** è impostato su **Sequenziale**e **Modalità transazione** è impostato su **Una sola transazione**.  
  
    -   **Opzione tabella writeback** è impostato su **Use existing**(Usa esistente).  
  
    -   In **Oggetti interessati**selezionare la casella di controllo **Elabora oggetti interessati** .  
  
10. Fare clic sulla scheda **errori chiave dimensione** . Verificare che l'opzione **Usa configurazione errori predefinita** sia selezionata.  
  
11. Fare clic su **OK** per chiudere la schermata **Cambia impostazioni** .  
  
12. Fare clic su **Esegui** nella schermata **Elabora oggetti** per avviare il processo di elaborazione.  
  
13. Quando nella casella **Stato** viene visualizzato **Elaborazione completata correttamente**, fare clic su **Chiudi**.  
  
14. Fare clic su **Chiudi** nella schermata **Elabora oggetti** .  
  
##  <a name="batch-processing-using-xmla-in-management-studio"></a><a name="bkmk_xmla"></a>Elaborazione batch con XMLA in Management Studio  
 È possibile creare uno script XMLA che esegue l'elaborazione batch. Iniziare generando uno script XMLA in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] per ogni oggetto, quindi combinarli in una sola query XMLA da eseguire in modo interattivo o in un'attività pianificata.  
  
 Per istruzioni dettagliate, vedere l' **esempio 2** in [Pianificare attività amministrative SSAS con SQL Server Agent](../instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Elaborazione di oggetti del modello multidimensionale](processing-a-multidimensional-model-analysis-services.md)  
  
  
