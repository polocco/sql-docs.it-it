---
title: Finestra di dialogo Salva risultati query di data mining (visualizzazione Stima modello di data mining) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dm.savedataminingqueryresult.f1
helpviewer_keywords:
- Save Data Mining Query Result dialog box
ms.assetid: 112fb527-7466-4fd4-9cf1-75596135648f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 97b391e24f98b230dbfe352e0cf1a574c7549984
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66070017"
---
# <a name="save-data-mining-query-result-dialog-box-mining-model-prediction-view"></a>Finestra di dialogo Salva risultati query di data mining (visualizzazione Stima modello di data mining)
  Utilizzare la finestra di dialogo **Salva risultati query di data mining** per salvare i risultati di una query di data mining in una nuova tabella.  
  
 La nuova tabella verrà creata nel database definito dall'origine dati.  
  
## <a name="options"></a>Opzioni  
 **Origine dati**  
 Consente di selezionare un'origine dati nel progetto corrente. Se l'origine dati corretta non esiste, fare clic su **Nuova** per creare una nuova origine dati.  
  
 **Nuova**  
 Consente di avviare la **Creazione guidata origine dati**.  
  
 **Nome tabella**  
 Consente di digitare un nome per la nuova tabella.  
  
 **Sovrascrivi se esistente**  
 Selezionare questa opzione se si desidera sovrascrivere una tabella esistente con lo stesso nome.  
  
 La sovrascrittura della tabella esistente è necessaria se si verificano una o più delle condizioni seguenti:  
  
-   Sono state aggiunte colonne alla query di stima.  
  
-   Sono stati modificati i nomi o i tipi di dati di tutte le colonne nella query di stima.  
  
-   È stata eseguita un'istruzione ALTER nella tabella di destinazione.  
  
 In caso di più colonne con lo stesso nome, ad esempio diverse colonne derivate con il nome di colonna predefinito **Espressione**, è necessario creare un alias per ogni colonna con un nome duplicato. Se i nomi delle colonne non sono univoci, verrà generato un errore quando il progettista tenta di salvare i risultati in SQL Server, in quanto i nomi delle colonne di una tabella devono essere univoci.  
  
 **Aggiungi a vista origine dati**  
 (Facoltativo) Selezionare una vista origine dati inclusa nel progetto per aggiungere la tabella a un'origine dati esistente.  
  
 Questa opzione è utile se si desidera utilizzare tutte le tabelle correlate per un modello, ad esempio i dati di training, i dati di origine della stima e i risultati delle query, nella stessa origine dati.  
  
## <a name="see-also"></a>Vedi anche  
 [Generatore di query di stima &#40;&#41;di data mining](prediction-query-builder-data-mining.md)   
 [Interfacce di query di data mining](data-mining/data-mining-query-tools.md)   
 [Guida di riferimento alle istruzioni DMX &#40;Data Mining Extensions&#41;](/sql/dmx/data-mining-extensions-dmx-statements)  
  
  
