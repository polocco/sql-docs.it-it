---
title: Aggiungere nuove righe nel riquadro Risultati (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- View Designer, Results pane
- inserting rows
- Query Designer [SQL Server], Results pane
- Results pane
- adding rows
- row additions [SQL Server], Results pane
ms.assetid: 59891c84-3f54-4ab9-8b86-72c59627b480
author: stevestein
ms.author: sstein
ms.openlocfilehash: d56b0bbf39a083e7deb6d168246f1f0136a482c7
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85067243"
---
# <a name="add-new-rows-in-the-results-pane-visual-database-tools"></a>Aggiunta di nuove righe nel riquadro Risultati (Visual Database Tools)
  Per aggiungere nuovi dati, è possibile digitarli o incollarli da un altro programma, ad esempio il Blocco note o Excel. Per incollare una riga è necessario che presenti esattamente lo stesso numero e tipo di colonne della tabella in cui la si desidera incollare. È possibile incollare nel riquadro Risultati più righe contemporaneamente.  
  
 Per informazioni su come immettere dati, vedere [Regole per l'aggiornamento dei risultati & #40;Visual Database Tools&#41;](visual-database-tools.md).  
  
### <a name="to-add-a-new-data-row"></a>Per aggiungere una nuova riga di dati  
  
1.  Spostarsi nella parte inferiore del riquadro Risultati, dove è disponibile una riga vuota per l'aggiunta di una nuova riga di dati.  
  
     I valori iniziali per tutte le colonne saranno di tipo *NULL*.  
  
    > [!TIP]  
    >  Per spostarsi direttamente sulla prima riga vuota, utilizzare la barra di navigazione nella parte inferiore del riquadro Risultati.  
  
2.  Se si incollano righe dagli Appunti, selezionare la nuova riga facendo clic sul pulsante alla sua sinistra.  
  
    > [!NOTE]  
    >  Qualora non sia possibile eseguire il commit nel database di una o più righe incollate, verrà visualizzato un messaggio che indicherà quali sono le righe di cui non è stato eseguito il commit.  
  
3.  Immettere i dati per la nuova riga. Se si incollano i dati, scegliere **Incolla** dal menu **Modifica** .  
  
4.  Uscire dalla riga in modo che ne venga eseguito il commit nel database.  
  
 Se si verifica un errore quando si salva la riga, in Progettazione query e Progettazione viste verrà visualizzato un messaggio e l'utente verrà posizionato nuovamente sulla riga che stava modificando. Sarà quindi possibile:  
  
-   Risolvere l'errore apportando ulteriori modifiche alla riga.  
  
-   Annullare la modifica premendo ESC. Se si preme ESC mentre si è posizionati in una cella cui sono state apportate modifiche, tali modifiche verranno annullate. Se si preme ESC mentre si è posizionati in una cella cui non è stata apportata alcuna modifica, verranno annullate le modifiche apportate all'intera riga.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzare i dati nel riquadro risultati &#40;Visual Database Tools&#41;](results-pane-visual-database-tools.md)   
 [Eseguire operazioni di base con le query &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
