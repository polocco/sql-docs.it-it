---
title: Usare operatori booleani in query XPath (SQLXML)
description: Informazioni su come usare gli operatori booleani nelle query XPath 4,0 di SQLXML.
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath operators [SQLXML]
- OR operator
- Boolean operators
- XPath queries [SQLXML], Boolean operators
- operators [SQLXML]
ms.assetid: 9928cff5-62ac-42aa-96bf-2e09a1df0bc3
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 06d56d0537bfda3a2ce44033a30d0f8e429fc0c4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773008"
---
# <a name="specifying-boolean-operators-in-xpath-queries-sqlxml-40"></a>Specifica di operatori booleani in query XPath (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Negli esempi seguenti viene illustrato come specificare operatori booleani in query XPath. Le query XPath di questi esempi vengono specificate sullo schema di mapping contenuto in SampleSchema1.xml. Per informazioni su questo schema di esempio, vedere [schema XSD con annotazioni di esempio per gli esempi XPath &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-specify-the-or-boolean-operator"></a>R. Specificare l'operatore booleano OR  
 Questa query XPath restituisce gli **\<Customer>** elementi figlio del nodo di contesto il cui valore di attributo **CustomerID** è 13 o 31:  
  
```  
/child::Customer[attribute::CustomerID="13" or attribute::CustomerID="31"]  
```  
  
 È possibile specificare un collegamento all'asse degli **attributi** (@) e, poiché l'asse **figlio** è quello predefinito, può essere omesso:  
  
```  
/Customer[@CustomerID="13" or @CustomerID="31"]  
```  
  
 Nel predicato `attribute` è l'asse e `CustomerID` è il test di nodo (true se **CustomerID** è un **\<attribute>** nodo, perché il **\<attribute>** nodo è il nodo primario per l'asse degli **attributi** ). Il predicato filtra gli **\<Customer>** elementi e restituisce solo quelli che soddisfano la condizione specificata nel predicato.  
  
##### <a name="to-test-the-xpath-queries-against-the-mapping-schema"></a>Per testare query Xpath sullo schema di mapping  
  
1.  Copiare il [codice dello schema di esempio](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) e incollarlo in un file di testo. Salvare il file con il nome SampleSchema1.xml.  
  
2.  Creare il modello seguente (BooleanOperatorsA.xml) e salvarlo nella directory in cui è stato salvato il file SampleSchema1.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[@CustomerID="13" or @CustomerID="31"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Il percorso di directory specificato per lo schema di mapping SampleSchema1.xml è relativo alla directory in cui è salvato il modello. È possibile specificare anche un percorso assoluto, ad esempio:  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Creare e utilizzare lo script di test SQLXML 4.0 (Sqlxml4test.vbs) per eseguire il modello.  
  
     Per ulteriori informazioni, vedere [utilizzo di ADO per eseguire query SQLXML 4,0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Di seguito è riportato il set di risultati relativo all'esecuzione del modello:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="13" SalesPersonID="286" TerritoryID="7" AccountNumber="13" CustomerType="S" />   
  <Customer CustomerID="31" SalesPersonID="286" TerritoryID="7" AccountNumber="31" CustomerType="S" Orders="Ord-51803 Ord-69427">  
    <Order SalesOrderID="Ord-51803" SalesPersonID="286" OrderDate="2003-08-01T00:00:00" DueDate="2003-08-13T00:00:00" ShipDate="2003-08-08T00:00:00">  
      <OrderDetail ProductID="Prod-718" UnitPrice="1059.31" OrderQty="1" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-838" UnitPrice="1059.31" OrderQty="1" UnitPriceDiscount="0" />   
    </Order>  
    <Order SalesOrderID="Ord-69427" SalesPersonID="286" OrderDate="2004-05-01T00:00:00" DueDate="2004-05-13T00:00:00" ShipDate="2004-05-08T00:00:00">  
      <OrderDetail ProductID="Prod-835" UnitPrice="440.1742" OrderQty="1" UnitPriceDiscount="0" />   
    </Order>  
  </Customer>  
</ROOT>  
```  
  
  
