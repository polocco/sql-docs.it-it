---
description: Combinazione di condizioni quando AND ha la precedenza (Visual Database Tools)
title: Combinare condizioni quando AND ha la precedenza
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search conditions [SQL Server], combining
- precedence [SQL Server], Criteria pane
- search criteria [SQL Server], combining conditions
- combining search conditions
- AND, Criteria pane
ms.assetid: 450eb2eb-6ea3-405b-8dd2-1ff926c016e7
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.openlocfilehash: 6ad323d3efdbb760b315c16d94752d8c658fdab5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88468479"
---
# <a name="combine-conditions-when-and-has-precedence-visual-database-tools"></a>Combinazione di condizioni quando AND ha la precedenza (Visual Database Tools)

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Per combinare condizioni con AND, aggiungere due volte la colonna alla query, una volta per ogni condizione. Per combinare più condizioni con OR, inserire la prima condizione nella colonna Filtro e le altre in una colonna **Or...** .  
  
Ad esempio, per trovare i dipendenti che hanno lavorato nell'azienda per più di cinque anni con mansioni di basso livello oppure i dipendenti con mansioni di livello medio indipendentemente dalla data di assunzione, occorre creare una query con tre condizioni, due delle quali collegate con AND:  
  
-   I dipendenti assunti da più di cinque anni e con livello pari a 100  
  
    -oppure-  
  
-   I dipendenti con livello pari a 200  
  
## <a name="to-combine-conditions-when-and-has-precedence"></a>Per combinare condizioni quando AND ha la precedenza  
  
1.  Nel [riquadro Criteri](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)aggiungere le colonne di dati da includere nella ricerca. Per eseguire la ricerca sulla stessa colonna utilizzando due o più condizioni collegate con AND, è necessario aggiungere alla griglia il nome della colonna di dati per ciascun valore da includere nella ricerca.  
  
2.  Nella colonna **Filtro** immettere tutte le condizioni da collegare con AND. Ad esempio, per collegare con AND condizioni per l'esecuzione della ricerca nelle colonne `hire_date` e `job_lvl` , immettere rispettivamente i valori `< '1/1/91'` e `= 100`nella colonna Filtro.  
  
    Queste voci della griglia producono la seguente clausola WHERE nell'istruzione nel [riquadro SQL](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md):  
  
    ```  
    WHERE (hire_date < '01/01/91') AND  
      (job_lvl = 100)  
    ```  
  
3.  Nella colonna **Or...** della griglia immettere le condizioni da collegare con OR. Ad esempio, per aggiungere una condizione per l'esecuzione della ricerca di un altro valore nella colonna `job_lvl` , immettere nella colonna **Or...** un altro valore, ad esempio `= 200`.  
  
    Aggiungendo un valore nella colonna **Or...** si aggiunge un'altra condizione alla clausola WHERE nell'istruzione nel riquadro SQL:  
  
    ```  
    WHERE (hire_date < '01/01/91' ) AND  
      (job_lvl = 100) OR   
      (job_lvl = 200)  
    ```  
  
## <a name="see-also"></a>Vedere anche

[Combinare condizioni quando OR ha la precedenza](../../ssms/visual-db-tools/combine-conditions-when-or-has-precedence-visual-database-tools.md)  
[Convenzioni per la combinazione delle condizioni di ricerca nel riquadro Criteri](../../ssms/visual-db-tools/conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md)  
[Regole per l'immissione di valori di ricerca](../../ssms/visual-db-tools/rules-for-entering-search-values-visual-database-tools.md)  
[Specificare criteri di ricerca](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)
