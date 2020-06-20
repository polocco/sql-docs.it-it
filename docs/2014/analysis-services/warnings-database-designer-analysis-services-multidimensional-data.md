---
title: Avvisi (Progettazione database) (Analysis Services-Dati multidimensionali) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.databasedesigner.warnings.f1
ms.assetid: 13f58b4d-f345-4fbc-ae2d-b3c8290a797d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 113f644d9f1da48790e7c8d59d34e6b143a1175a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84938122"
---
# <a name="warnings-database-designer-analysis-services---multidimensional-data"></a>Avvisi (Progettazione database) (Analysis Services - Dati multidimensionali)
  Usare la scheda **Avvisi** per visualizzare e ignorare totalmente le regole e per visualizzare e riattivare istanze specifiche di avvisi ignorati. La scheda **Avvisi** visualizza due griglie: **Regole per gli avvisi di progettazione** e **Avvisi ignorati**.  
  
 **Per visualizzare la scheda Avvisi**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aprire un progetto [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
2.  In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , fare clic su **Modifica database**, quindi fare clic sulla scheda **Avvisi** .  
  
## <a name="design-warning-rules-grid"></a>Griglia Regole per gli avvisi di progettazione  
 La griglia **Regole per gli avvisi di progettazione** visualizza tutte le regole dell'avviso di progettazione. Questa griglia controlla anche quali regole sono attivate nel database. Per attivare o disabilitare una regola dell'avviso, selezionare o deselezionare la casella di controllo.  
  
 La griglia **Regole per gli avvisi di progettazione** ha le seguenti colonne:  
  
 **Descrizione**  
 Visualizza il nome della regola. Le regole sono raggruppate per categoria.  
  
 **Importanza**  
 Visualizza la priorità assegnata alla regola.  
  
 **Commenti**  
 (Facoltativo) Consente all'utente di digitare un commento che spieghi perché si sta ignorando l'avviso.  
  
## <a name="dismissed-warnings-grid"></a>Griglia Avvisi ignorati  
 La griglia **Avvisi ignorati** visualizza tutte le occorrenze specifiche dell'avviso ignorate dall' **Elenco errori**. Per riattivare un avviso, selezionarlo nella griglia, quindi fare clic su **Riabilita**.  
  
 La griglia **Avvisi ignorati** ha i seguenti elementi :  
  
 **Object**  
 Visualizza un'icona che rappresenta il tipo di oggetto e il nome dell'oggetto.  
  
 **Tipo**  
 Visualizza il tipo di oggetto.  
  
 **Descrizione**  
 Visualizza il nome della regola.  
  
 **Importanza**  
 Visualizza la priorità assegnata alla regola.  
  
 **Commenti**  
 Visualizza il commento immesso quando l'avviso è stato ignorato. Qui è possibile aggiungere o modificare un commento.  
  
 **Riabilita**  
 Riattiva gli avvisi selezionati.  
  
> [!NOTE]  
>  Se un oggetto ha un avviso, ma è in uno stato non valido o è stato rimosso manualmente dal progetto, verrà visualizzata un'icona Errori nell'elenco accanto all'avviso. Per ignorare l'avviso, selezionarlo, quindi fare clic su **Riabilita**.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestra di dialogo Ignora avviso &#40;Analysis Services-Dati multidimensionali&#41;](dismiss-warning-dialog-box-analysis-services-multidimensional-data.md)   
 [&#40;generale di progettazione database&#41; &#40;Analysis Services Dati multidimensionali&#41;](general-database-designer-analysis-services-multidimensional-data.md)  
  
  
