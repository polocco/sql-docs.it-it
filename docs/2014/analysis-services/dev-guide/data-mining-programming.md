---
title: Programmazione di data mining | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- data mining [Analysis Services], developer's guide
ms.assetid: 9fd77b16-0b89-44ce-bcf1-7c04b62499da
author: minewiskan
ms.author: owend
ms.openlocfilehash: fd4bd48b5914d5fda89f94c0a959e670ffec3321
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528677"
---
# <a name="data-mining-programming"></a>Programmazione di data mining
  Se gli strumenti e i visualizzatori predefiniti disponibili in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] non soddisfano i propri requisiti, è possibile estendere le funzionalità di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] mediante la codifica di estensioni personalizzate. Questo approccio rende disponibili due opzioni:  
  
-   **XMLA**  
  
     [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]supporta XML for Analysis (XMLA) come protocollo per la comunicazione con le applicazioni client. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supporta comandi aggiuntivi che estendono la specifica XML for Analysis.  
  
     Poiché [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilizza XMLA per la definizione dei dati, la manipolazione dei dati e il supporto del controllo dei dati, è possibile creare strutture di data mining e modelli di data mining tramite gli strumenti visivi forniti da [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], quindi estendere gli oggetti di data mining creati tramite script DMX (Data Mining Extensions) e ASSL (Analysis Services Scripting Language).  
  
     È possibile creare e modificare completamente oggetti di data mining negli script XMLA ed eseguire query di stima sui modelli a livello di codice dalle applicazioni personalizzate.  
  
-   **AMO (Analysis Management Objects)**  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] include inoltre un framework completo che consente ai provider di data mining di terze parti di integrare gli oggetti di data mining in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
     È possibile creare le strutture e i modelli di data mining tramite AMO. Vedere gli esempi seguenti in CodePlex:  
  
    -   Visualizzatore AMO  
  
         Si connette all'istanza di SSAS specificata e restituisce un elenco di tutti gli oggetti server e delle relative proprietà, inclusa la struttura di data mining e i modelli di data mining.  
  
    -   AMO Simple Sample  
  
         AS Simple Sample illustra l'accesso a livello di codice alla maggior parte degli oggetti principali e dimostra la visualizzazione dei metadati e l'accesso ai valori negli oggetti.  
  
         L'esempio illustra inoltre come creare ed elaborare una struttura e un modello di data mining, nonché sfogliare un modello di data mining esistente.  
  
-   **DMX**  
  
     È possibile utilizzare DMX per incapsulare istruzioni di comando, query di stima e query sui metadati e per restituire i risultati in un formato tabulare, presupponendo che sia stata creata una connessione a un server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [OLE DB for Data Mining](../../../2014/analysis-services/dev-guide/ole-db-for-data-mining.md)  
 Vengono descritte le aggiunte alla specifica per il supporto di data mining e dati multidimensionali, ovvero nuovi set di righe e colonne dello schema e linguaggio DMX (Data Mining Extensions) per la creazione e la gestione di strutture di data mining.  
  
## <a name="related-reference"></a>Riferimenti correlati  
 [Sviluppo con ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/developing-with-adomd-net)  
 Viene fornita un'introduzione agli oggetti di programmazione client e server ADOMD.NET.  
  
 [Sviluppo con AMO &#40;Analysis Management Objects&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)  
 Viene fornita un'introduzione alla libreria di programmazione AMO.  
  
 [Sviluppo con Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
 Viene fornita un'introduzione a XML for Analysis (XMLA) e alle relative estensioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida per gli sviluppatori &#40;Analysis Services&#41;](../analysis-services-developer-documentation.md)   
 [Guida di riferimento a DMX &#40;Data Mining Extensions&#41;](/sql/dmx/data-mining-extensions-dmx-reference)  
  
  
