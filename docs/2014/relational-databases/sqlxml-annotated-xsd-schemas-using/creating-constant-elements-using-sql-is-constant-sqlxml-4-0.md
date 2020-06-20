---
title: 'Creazione di elementi costanti tramite SQL: is-constant (SQLXML 4,0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- element does not map [SQLXML]
- sql:is-constant
- XSD schemas [SQLXML], constant elements
- element mapping [SQLXML], constant elements
- is-constant annotation
- constant elements [SQLXML]
- annotated XSD schemas, constant elements
ms.assetid: 940eea1b-54f5-445f-b844-c894d9f3941b
author: rothja
ms.author: jroth
ms.openlocfilehash: 6a0b31c68f7ebbb956c2d539dee4bc4dca2eb5ce
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85060133"
---
# <a name="creating-constant-elements-using-sqlis-constant-sqlxml-40"></a>Creazione di elementi costanti tramite sql:is-constant (SQLXML 4.0)
  Per specificare un elemento costante, ovvero un elemento nello schema XSD che non esegue il mapping ad alcuna tabella o colonna di database, è possibile utilizzare l' `sql:is-constant` annotazione. Questa annotazione accetta un valore booleano (0=false, 1=true). I valori possibili sono 0, 1, true e false. L'annotazione `sql:is-constant` può essere specificata in un elemento che non include alcun attributo. Se viene specificata in un elemento con valore true (o 1), l'elemento non viene mappato al database ma viene comunque visualizzato nel documento XML.  
  
 È possibile utilizzare l'annotazione `sql:is-constant` per le operazioni seguenti:  
  
-   Aggiunta di un elemento di livello principale al documento XML. XML richiede un singolo elemento di livello principale (elemento radice) per il documento.  
  
-   Creazione di elementi contenitore, ad esempio un **\<Orders>** elemento che esegue il wrapping di tutti gli ordini.  
  
 L' `sql:is-constant` annotazione può essere aggiunta a un **\<complexType>** elemento.  
  
## <a name="examples"></a>Esempi  
 Per creare esempi reali utilizzando gli esempi seguenti, è necessario soddisfare alcuni requisiti. Per ulteriori informazioni, vedere [requisiti per l'esecuzione di esempi SQLXML](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqlis-constant-to-add-a-container-element"></a>R. Definizione di sql:is-constant per aggiungere un elemento contenitore  
 In questo schema XSD con annotazioni, **\<CustomerOrders>** viene definito come elemento costante specificando l' `sql:is-constant` attributo con un valore pari a 1. Pertanto, **\<CustomerOrders>** non è mappato ad alcuna tabella o colonna di database. Questo elemento costante è costituito dagli **\<Order>** elementi figlio.  
  
 Sebbene non sia **\<CustomerOrders>** mappato ad alcuna tabella o colonna di database, viene comunque visualizzato nel codice XML risultante come elemento contenitore contenente gli **\<Order>** elementi figlio.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
        parent="Sales.Customer"  
        parent-key="CustomerID"  
        child="Sales.SalesOrderHeader"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="CustomerOrders" sql:is-constant="1" >  
          <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"  
                           sql:relationship="CustOrders"   
                           maxOccurs="unbounded" >  
                <xsd:complexType>  
                   <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                   <xsd:attribute name="OrderDate" type="xsd:date" />  
                   <xsd:attribute name="CustomerID" type="xsd:string" />  
                </xsd:complexType>  
              </xsd:element>  
            </xsd:sequence>  
           </xsd:complexType>  
          </xsd:element>  
         </xsd:sequence>  
          <xsd:attribute name="CustomerID" type="xsd:string" />  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Per testare una query Xpath di esempio sullo schema  
  
1.  Copiare il codice dello schema precedente e incollarlo in un file di testo. Salvare il file con il nome isConstant.xml.  
  
2.  Copiare il modello seguente e incollarlo in un file di testo. Salvare il file con il nome isConstantT.xml nella stessa directory in cui è stato salvato il file isConstant.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="isConstant.xml">  
            Customer[@CustomerID=1]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Il percorso di directory specificato per lo schema di mapping (isConstant.xml) è relativo alla directory in cui è salvato il modello. È possibile specificare anche un percorso assoluto, ad esempio:  
  
    ```  
    mapping-schema="C:\MyDir\isConstant.xml"  
    ```  
  
3.  Creare e utilizzare lo script di test SQLXML 4.0 (Sqlxml4test.vbs) per eseguire il modello.  
  
     Per ulteriori informazioni, vedere [utilizzo di ADO per eseguire query SQLXML](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Di seguito è riportato il set di risultati parziale:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
<Customer CustomerID="1">   
  <CustomerOrders>   
    <Order SalesOrderID="43860" OrderDate="2001-08-01" CustomerID="1" />   
    <Order SalesOrderID="44501" OrderDate="2001-11-01" CustomerID="1" />   
    <Order SalesOrderID="45283" OrderDate="2002-02-01" CustomerID="1" />   
    <Order SalesOrderID="46042" OrderDate="2002-05-01" CustomerID="1" />   
    ...  
  </CustomerOrders>   
</Customer>   
</ROOT>  
```  
  
  
