---
title: 'Lezione 1: Conversione di una tabella in una struttura gerarchica | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 5ee6f19a-6dd7-4730-a91c-bbed1bd77e0b
author: stevestein
ms.author: sstein
ms.openlocfilehash: cd6f1d123bca9f9f0c10288e0b58dd075c7b0949
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85068055"
---
# <a name="lesson-1-converting-a-table-to-a-hierarchical-structure"></a>Lezione 1: Conversione di una tabella in una struttura gerarchica
  I clienti che hanno tabelle che utilizzano un self-join per esprimere relazioni gerarchiche possono convertire le tabelle in una struttura gerarchica utilizzando questa lezione come guida. È relativamente facile eseguire la migrazione da questa rappresentazione a `hierarchyid`. Dopo la migrazione, gli utenti avranno una rappresentazione gerarchica compatta e facile da capire che può essere indicizzata in molti modi per eseguire query efficienti.  
  
 In questa lezione, verrà esaminata una tabella esistente, verrà creata una nuova tabella contenente una colonna `hierarchyid`, verrà popolata la tabella con i dati della tabella di origine e infine verranno illustrate tre strategie di indicizzazione. In questa lezione sono inclusi gli argomenti seguenti:  
  
-   [Esame della struttura corrente della tabella Employee](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
-   [Popolamento di una tabella con dati gerarchici esistenti](lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
-   [Ottimizzazione della tabella NewOrg](lesson-1-3-optimizing-the-neworg-table.md)  
  
-   [Riepilogo: Conversione di una tabella in una struttura gerarchica](lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
## <a name="prerequisites"></a>Prerequisiti  
 Questa lezione richiede il database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Esame della struttura corrente della tabella Employee](lesson-1-1-examining-the-current-structure-of-the-employee-table.md)  
  
## <a name="next-lesson"></a>Lezione successiva  
 [Lezione 2: Creazione e gestione di dati in una tabella gerarchica](lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
  
  
