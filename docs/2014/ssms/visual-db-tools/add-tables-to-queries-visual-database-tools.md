---
title: Aggiungere tabelle a query (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- inserting tables
- adding tables
- queries [SQL Server], tables
ms.assetid: 6551aa7e-31a1-4636-852a-819bc53d658b
author: stevestein
ms.author: sstein
ms.openlocfilehash: db979203f45897644fa22f011000b6d4d7e3b712
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85044523"
---
# <a name="add-tables-to-queries-visual-database-tools"></a>Aggiunta di tabelle a query (Visual Database Tools)
  Quando si crea una query, si recuperano dati da una tabella o da altri oggetti strutturati come tabelle, come viste e alcune funzioni definite dall'utente. Per usare uno qualsiasi di questi oggetti nelle query, è necessario aggiungerlo nel **riquadro Diagramma**.  
  
### <a name="to-add-a-table-or-table-valued-object-to-a-query"></a>Per aggiungere una tabella o un oggetto con valori di tabella a una query  
  
1.  Nel **riquadro Diagramma** di Progettazione query e Progettazione viste fare clic col pulsante destro sullo sfondo e scegliere **Aggiungi tabella** dal menu di scelta rapida.  
  
2.  Nella finestra di dialogo **Aggiungi tabella** selezionare la scheda relativa al tipo di oggetto da aggiungere alla query.  
  
3.  Fare doppio clic sulle voci dell'elenco che si desidera aggiungere.  
  
4.  Dopo aver aggiunto tutte le voci appropriate, fare clic su **Chiudi**.  
  
     Progettazione query e Progettazione viste aggiornano di conseguenza il **riquadro Diagramma**, il **riquadro Criteri**e il **riquadro SQL** .  
  
 Le tabelle e le viste vengono aggiunte automaticamente alla query quando si fa riferimento ad esse nell'istruzione nel riquadro SQL.  
  
 Se non si dispone di diritti di accesso sufficienti o se il provider non è in grado di restituire le informazioni necessarie, in Progettazione query e Progettazione viste non verrà visualizzata alcuna colonna di dati per una tabella o un oggetto con valori di tabella. In questi casi, verranno visualizzati solo una barra del titolo e la casella di controllo * (tutte le colonne) per la tabella o l'oggetto con valori di tabella.  
  
### <a name="to-add-an-existing-query-to-a-new-query"></a>Per aggiungere una query esistente a una nuova query  
  
1.  Assicurarsi che nella nuova query che si sta creando sia visibile il **riquadro SQL** .  
  
2.  Nel **riquadro SQL**digitare una parentesi sinistra e una destra () dopo la parola FROM.  
  
3.  Aprire Progettazione query dalla query esistente. A questo punto saranno aperte due istanze di Progettazione query.  
  
4.  Visualizzare il **riquadro SQL** per la query interna, ossia la query esistente da includere nella nuova query esterna.  
  
5.  Selezionare tutto il testo presente nel **riquadro SQL**e copiarlo negli Appunti.  
  
6.  Fare clic nel **riquadro SQL** della nuova query, posizionare il cursore tra le parentesi aggiunte e incollare il contenuto degli Appunti.  
  
7.  Sempre nel **riquadro SQL**aggiungere un alias dopo la parentesi destra.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di alias di tabella &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Rimuovere tabelle da query &#40;Visual Database Tools&#41;](remove-tables-from-queries-visual-database-tools.md)   
 [Specificare i criteri di ricerca &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)   
 [Riepilogare i risultati delle query &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)   
 [Eseguire operazioni di base con le query &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
