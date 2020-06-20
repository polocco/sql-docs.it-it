---
title: Usare la modalità AUTO con FOR XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, AUTO mode
- ELEMENTS option
- FOR XML AUTO mode
- AUTO FOR XML mode
ms.assetid: 7140d656-1d42-4f01-a533-5251429f4450
author: rothja
ms.author: jroth
ms.openlocfilehash: 232cc046667c6d31cb9657a7abdc862204507d23
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059412"
---
# <a name="use-auto-mode-with-for-xml"></a>Utilizzo della modalità AUTO con FOR XML
  Come descritto in [FOR XML &#40;SQL Server&#41;](for-xml-sql-server.md), la modalità AUTO restituisce i risultati della query come elementi XML annidati. ma non consente di controllare in modo preciso la struttura del valore XML generato. È consigliabile utilizzare query in modalità AUTO solo se si desidera generare gerarchie semplici. Tuttavia, l' [uso della modalità EXPLICIT con FOR XML](use-explicit-mode-with-for-xml.md) e l' [uso della modalità PATH con FOR XML](use-path-mode-with-for-xml.md) assicurano maggiore controllo e flessibilità nella definizione della forma di elementi XML dal risultato di una query.  
  
 Ogni tabella nella clausola FROM, della quale almeno una colonna viene elencata nella clausola SELECT, viene rappresentata come un elemento XML. Se per la clausola FOR XML è specificata l'opzione facoltativa ELEMENTS, verrà eseguito il mapping delle colonne elencate nella clausola SELECT ad attributi o sottoelementi.  
  
 La gerarchia XML (nidificazione degli elementi) del valore XML risultante è basata sull'ordine delle tabelle identificate dalle colonne specificate nella clausola SELECT. L'ordine in cui sono specificati i nomi delle colonne nella clausola SELECT è pertanto significativo. La prima tabella da sinistra identificata costituisce l'elemento di livello principale nel documento XML risultante. La seconda tabella da sinistra, identificata dalle colonne nell'istruzione SELECT, costituisce un sottoelemento all'interno dell'elemento di livello principale e così via.  
  
 Se un nome di colonna elencato nella clausola SELECT appartiene a una tabella già identificata da una colonna specificata in precedenza nella clausola SELECT, tale colonna verrà aggiunta come attributo dell'elemento già creato, anziché aggiungere un nuovo livello alla gerarchia. Se si specifica l'opzione ELEMENTS, la colonna verrà aggiunta come attributo.  
  
 Si esegua ad esempio la query seguente:  
  
```  
SELECT Cust.CustomerID,   
       OrderHeader.CustomerID,  
       OrderHeader.SalesOrderID,   
       OrderHeader.Status,  
       Cust.CustomerType  
FROM Sales.Customer Cust, Sales.SalesOrderHeader OrderHeader  
WHERE Cust.CustomerID = OrderHeader.CustomerID  
ORDER BY Cust.CustomerID  
FOR XML AUTO  
```  
  
 Risultato parziale:  
  
```  
<Cust CustomerID="1" CustomerType="S">  
  <OrderHeader CustomerID="1" SalesOrderID="43860" Status="5" />  
  <OrderHeader CustomerID="1" SalesOrderID="44501" Status="5" />  
  <OrderHeader CustomerID="1" SalesOrderID="45283" Status="5" />  
  <OrderHeader CustomerID="1" SalesOrderID="46042" Status="5" />  
</Cust>  
...  
```  
  
 Nella clausola SELECT si noti quanto segue:  
  
-   CustomerID fa riferimento alla tabella Cust. Verrà pertanto creato un elemento <`Cust`> al quale verrà aggiunto CustomerID come attributo.  
  
-   Poiché inoltre le tre colonne OrderHeader.CustomerID, OrderHeader.SaleOrderID e OrderHeader.Status fanno riferimento alla tabella OrderHeader, viene aggiunto un elemento <`OrderHeader`> come sottoelemento dell'elemento <`Cust`> e le tre colonne vengono aggiunte come attributi di <`OrderHeader`>.  
  
-   Anche la colonna Cust.CustomerType fa riferimento alla tabella Cust, che era già stata identificata dalla colonna Cust.CustomerID. Non verranno pertanto creati nuovi elementi, ma all'elemento <`Cust`> creato in precedenza verrà aggiunto l'attributo CustomerType.  
  
-   Nella query sono specificati alias per i nomi delle tabelle. Tali alias sono i nomi degli elementi corrispondenti.  
  
-   La clausola ORDER BY è necessaria per raggruppare tutti gli elementi figlio sotto un unico elemento padre.  
  
 Questa query è simile alla precedente, con la differenza che nella clausola SELECT le colonne della tabella OrderHeader sono specificate prima di quelle della tabella Cust. Viene pertanto creato prima l'elemento <`OrderHeader`>, a cui viene aggiunto l'elemento figlio <`Cust`>.  
  
```  
select OrderHeader.CustomerID,  
       OrderHeader.SalesOrderID,   
       OrderHeader.Status,  
       Cust.CustomerID,   
       Cust.CustomerType  
from Sales.Customer Cust, Sales.SalesOrderHeader OrderHeader  
where Cust.CustomerID = OrderHeader.CustomerID  
for xml auto  
```  
  
 Risultato parziale:  
  
```  
<OrderHeader CustomerID="1" SalesOrderID="43860" Status="5">  
  <Cust CustomerID="1" CustomerType="S" />  
</OrderHeader>  
...  
```  
  
 Se alla clausola FOR XML viene aggiunta l'opzione ELEMENTS, verrà restituito un valore XML incentrato sugli elementi.  
  
```  
SELECT Cust.CustomerID,   
       OrderHeader.CustomerID,  
       OrderHeader.SalesOrderID,   
       OrderHeader.Status,  
       Cust.CustomerType  
FROM Sales.Customer Cust, Sales.SalesOrderHeader OrderHeader  
WHERE Cust.CustomerID = OrderHeader.CustomerID  
ORDER BY Cust.CustomerID  
FOR XML AUTO, ELEMENTS  
```  
  
 Risultato parziale:  
  
```  
<Cust>  
  <CustomerID>1</CustomerID>  
  <CustomerType>S</CustomerType>  
  <OrderHeader>  
    <CustomerID>1</CustomerID>  
    <SalesOrderID>43860</SalesOrderID>  
    <Status>5</Status>  
  </OrderHeader>  
   ...  
</Cust>  
...  
```  
  
 In questa query, i valori CustomerID vengono confrontati tra una riga e l'altra per la creazione degli \<Cust> elementi, perché CustomerID è la chiave primaria della tabella. Se CustomerID non viene identificata come chiave primaria della tabella, tutti i valori delle colonne (in questa query, CustomerID e CustomerType) di ogni riga verranno confrontati con quelli della riga successiva. Se i valori sono diversi, \<Cust> al codice XML viene aggiunto un nuovo elemento.  
  
 Durante il confronto di questi valori di colonna, se una qualsiasi delle colonne da confrontare è di tipo **text**, **ntext**, **image**o **xml**, FOR XML presupporrà che i valori siano diversi e non eseguirà il confronto, anche se potrebbero essere uguali. Questo avviene perché il confronto di oggetti di grandi dimensioni non è supportato. Vengono aggiunti elementi al risultato per ogni riga selezionata. Si noti che le colonne di tipo **(n)varchar(max)** e **varbinary(max)** vengono confrontate.  
  
 Quando una colonna nella clausola SELECT non può essere associata a una qualsiasi delle tabelle identificate nella clausola FROM, ad esempio nel caso di una colonna aggregata o calcolata, la colonna viene aggiunta al documento XML al livello di nidificazione più basso quando viene rilevata nell'elenco. Se tale colonna viene elencata per prima nella clausola SELECT, verrà aggiunta come elemento di livello principale.  
  
 Se nella clausola SELECT è specificato il carattere jolly asterisco (*), il livello di nidificazione verrà determinato come descritto in precedenza, ovvero in base all'ordine in cui le righe vengono restituite dal motore query.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 Per ulteriori informazioni sulla modalità AUTO, vedere gli argomenti seguenti:  
  
-   [Usare l'opzione BINARY BASE64](use-the-binary-base64-option.md)  
  
-   [Approccio euristico della modalità AUTO per la determinazione della struttura dei valori XML restituiti](auto-mode-heuristics-in-shaping-returned-xml.md)  
  
-   [Esempi d'uso della modalità AUTO](examples-using-auto-mode.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql)   
 [FOR XML &#40;SQL Server&#41;](for-xml-sql-server.md)  
  
  
