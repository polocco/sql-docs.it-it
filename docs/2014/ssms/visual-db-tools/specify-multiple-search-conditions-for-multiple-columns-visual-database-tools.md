---
title: Specificare più condizioni di ricerca per più colonne (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], multiple conditions
- multiple search conditions
- search conditions [SQL Server], multiple
- OR operator
- AND, Criteria pane
ms.assetid: 06617729-0d0b-4da2-9890-b7e2f5cdbc7b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3580f6365866ce752191e285b14f7d793be0cad0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "63204951"
---
# <a name="specify-multiple-search-conditions-for-multiple-columns-visual-database-tools"></a>Definizione di più condizioni di ricerca per più colonne (Visual Database Tools)
  È possibile ampliare o limitare l'ambito della query includendo diverse colonne di dati tra le condizioni di ricerca. Può, ad esempio, essere necessario:  
  
-   Cercare i dipendenti che hanno lavorato più di cinque anni nell'azienda o che hanno determinate mansioni.  
  
-   Cercare un libro pubblicato da un determinato editore e che tratta di cucina.  
  
 Per creare una query per la ricerca di valori in una colonna all'interno di una combinazione di colonne, specificare una condizione OR. Per creare una query che soddisfi tutte le condizioni in più colonne, specificare una condizione AND.  
  
## <a name="specifying-an-or-condition"></a>Specifica di una condizione OR  
 Per creare più condizioni collegate con OR, inserire ciascuna condizione in una colonna diversa del riquadro Criteri.  
  
#### <a name="to-specify-an-or-condition-for-two-different-columns"></a>Per specificare una condizione OR per due colonne diverse  
  
1.  Nel [riquadro Criteri](visual-database-tools.md)aggiungere le colonne da includere nella ricerca.  
  
2.  Nella colonna **Filtro** per la prima colonna da includere nella ricerca, specificare la prima condizione.  
  
3.  Nella colonna **Or...** per la seconda colonna di dati da includere nella ricerca, specificare la seconda condizione lasciando vuota la colonna **Filtro** .  
  
     In Progettazione query e Progettazione viste viene creata una clausola WHERE contenente una condizione OR analoga alla seguente:  
  
    ```  
    SELECT job_lvl, hire_date  
    FROM employee  
    WHERE (job_lvl >= 200) OR   
      (hire_date < '01/01/1998')  
    ```  
  
4.  Ripetere i passaggi 2 e 3 per tutte le altre condizioni da aggiungere. Utilizzare una colonna **Or...** diversa per ogni nuova condizione.  
  
## <a name="specifying-an-and-condition"></a>Specifica di una condizione AND  
 Per estendere la ricerca a più colonne di dati con condizioni collegate con AND, inserire tutte le condizioni nella colonna **Filtro** della griglia.  
  
#### <a name="to-specify-an-and-condition-for-two-different-columns"></a>Per specificare una condizione AND per due colonne diverse  
  
1.  Nel [riquadro Criteri](visual-database-tools.md)aggiungere le colonne da includere nella ricerca.  
  
2.  Nella colonna **Filtro** per la prima colonna di dati da includere nella ricerca specificare la prima condizione.  
  
3.  Nella colonna **Filtro** per la seconda colonna di dati specificare la seconda condizione.  
  
     In Progettazione query e Progettazione viste verrà creata una clausola WHERE contenente una condizione AND analoga alla seguente:  
  
    ```  
    SELECT pub_id, title  
    FROM titles  
    WHERE (pub_id = '0877') AND (title LIKE '%Cook%')  
    ```  
  
4.  Ripetere i passaggi 2 e 3 per tutte le altre condizioni da aggiungere.  
  
## <a name="see-also"></a>Vedere anche  
 [Combinare condizioni quando AND ha la precedenza &#40;Visual Database Tools&#41;](combine-conditions-when-and-has-precedence-visual-database-tools.md)   
 [Combinare condizioni quando OR ha la precedenza &#40;Visual Database Tools&#41;](combine-conditions-when-or-has-precedence-visual-database-tools.md)   
 [Convenzioni per la combinazione di condizioni di ricerca nel riquadro Criteri &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md)   
 [Specifica dei criteri di ricerca &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)  
  
  
