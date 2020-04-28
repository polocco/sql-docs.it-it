---
title: Specificare più condizioni di ricerca per una sola colonna (Visual Database Tools) | Microsoft Docs
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
ms.assetid: 2c006e36-56b1-4992-89b4-c6c0b19808f3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 176d5a6586008d49ece1430ec03e2c54278eebce
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62695402"
---
# <a name="specify-multiple-search-conditions-for-one-column-visual-database-tools"></a>Definizione di più condizioni di ricerca per una sola colonna (Visual Database Tools)
  In alcuni casi può essere necessario applicare diverse condizioni di ricerca a una stessa colonna di dati. Può, ad esempio, essere necessario:  
  
-   Cercare diversi nomi o dipendenti con diverse fasce di stipendio in una tabella `employee` . Questo tipo di ricerca richiede una condizione OR.  
  
-   Cercare il titolo di un libro che inizi con la parola "Il" e contenga la parola "cuoco". Questo tipo di ricerca richiede una condizione AND.  
  
> [!NOTE]  
>  Le informazioni contenute in questo argomento sono valide per le condizioni di ricerca nelle clausole WHERE e HAVING di una query. Gli esempi sono incentrati sulla creazione di clausole WHERE, ma i principi sono validi per entrambi i tipi di condizione di ricerca.  
  
 Per cercare valori alternativi nella stessa colonna di dati, specificare una condizione OR. Per cercare valori che soddisfino più condizioni, specificare una condizione AND.  
  
## <a name="specifying-an-or-condition"></a>Specifica di una condizione OR  
 La condizione OR consente di specificare diversi valori alternativi da cercare in una colonna. Questa opzione amplia l'ambito della ricerca e può restituire più righe rispetto alla ricerca di un valore singolo.  
  
> [!TIP]  
>  In alternativa, è spesso possibile utilizzare l'operatore IN per cercare più valori in una stessa colonna di dati.  
  
#### <a name="to-specify-an-or-condition"></a>Per specificare una condizione OR  
  
1.  Nel [riquadro Criteri](visual-database-tools.md)aggiungere la colonna da includere nella ricerca.  
  
2.  Nella colonna **Filtro** per la colonna di dati appena aggiunta specificare la prima condizione.  
  
3.  Nella colonna **Or...** per la stessa colonna di dati specificare la seconda condizione.  
  
 In Progettazione query e Progettazione viste viene creata una clausola WHERE contenente una condizione OR analoga alla seguente:  
  
```  
SELECT fname, lname  
FROM employees  
WHERE (salary < 30000) OR (salary > 100000)  
```  
  
## <a name="specifying-an-and-condition"></a>Specifica di una condizione AND  
 La condizione AND consente di specificare che i valori in una colonna devono soddisfare due o più condizioni affinché la riga venga inclusa nel set di risultati. Questa opzione restringe l'ambito della ricerca e in genere restituisce meno righe rispetto alla ricerca di un valore singolo.  
  
> [!TIP]  
>  Se si cerca un intervallo di valori, sarà possibile utilizzare l'operatore BETWEEN anziché collegare due condizioni con AND.  
  
#### <a name="to-specify-an-and-condition"></a>Per specificare una condizione AND  
  
1.  Nel riquadro Criteri aggiungere la colonna da includere nella ricerca.  
  
2.  Nella colonna **Filtro** per la colonna di dati appena aggiunta specificare la prima condizione.  
  
3.  Aggiungere nuovamente la stessa colonna di dati al riquadro Criteri, collocandola in una riga vuota della griglia.  
  
4.  Nella colonna **Filtro** per la seconda istanza della colonna di dati specificare la seconda condizione.  
  
 In Progettazione query viene creata una clausola WHERE contenente una condizione AND analoga alla seguente:  
  
```  
SELECT title_id, title  
FROM titles  
WHERE (title LIKE '%Cook%') AND   
  (title LIKE '%Recipe%')  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Convenzioni per la combinazione di condizioni di ricerca nel riquadro Criteri &#40;Visual Database Tools&#41;](conventions-combine-search-conditions-in-criteria-pane-visual-db-tools.md)   
 [Specifica dei criteri di ricerca &#40;Visual Database Tools&#41;](specify-search-criteria-visual-database-tools.md)  
  
  
