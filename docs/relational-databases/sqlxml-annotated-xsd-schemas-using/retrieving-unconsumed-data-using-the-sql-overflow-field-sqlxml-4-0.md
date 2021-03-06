---
title: 'Ottenere dati non utilizzati con SQL: overflow-field (SQLXML)'
description: 'Informazioni su come utilizzare SQL: overflow-field in SQLXML 4,0 per recuperare dati non utilizzati dalla funzione OPENXML.'
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- unconsumed data
- storing unconsumed data
- retrieving unconsumed data
- annotated XSD schemas, unconsumed data
- overflow data [SQLXML]
- sql:overflow-field
ms.assetid: 8526998d-b47d-4a32-8dc2-7f50a8d11097
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cb675f7440f0718e2b981992a129bb2b3b97fd41
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85764913"
---
# <a name="retrieving-unconsumed-data-using-the-sqloverflow-field-sqlxml-40"></a>Recupero di dati non utilizzati mediante sql:overflow-field (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Quando i record vengono inseriti in un database da un documento XML tramite la funzione OPENXML [!INCLUDE[tsql](../../includes/tsql-md.md)], tutti i dati non utilizzati dal documento XML di origine possono essere archiviati in una colonna. Quando si recuperano dati da un database di utilizzando schemi con annotazioni, è possibile specificare l'attributo **SQL: overflow-field** per identificare la colonna nella tabella in cui sono archiviati i dati di overflow. L'attributo **SQL: overflow-field** può essere specificato in **\<element>** .  
  
 I dati vengono quindi recuperati nei modi seguenti:  
  
-   Gli attributi archiviati nella colonna di overflow vengono aggiunti all'elemento che contiene l'annotazione **SQL: overflow-field** .  
  
-   Gli elementi figlio e i relativi discendenti, archiviati nella colonna di overflow nel database, vengono aggiunti come elementi figlio dopo il contenuto specificato in modo esplicito nello schema. Non viene rispettato alcun ordine.  
  
## <a name="examples"></a>Esempi  
 Per creare esempi reali utilizzando gli esempi seguenti, è necessario soddisfare alcuni requisiti. Per ulteriori informazioni, vedere [requisiti per l'esecuzione di esempi SQLXML](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqloverflow-field-for-an-element"></a>R. Specifica di sql:overflow-field per un elemento  
 In questo esempio si presuppone che sia stato eseguito lo script seguente per far sì che una tabella denominata Customers2 esista nel database tempdb:  
  
```  
USE tempdb  
CREATE TABLE Customers2 (  
CustomerID       VARCHAR(10),   
ContactName    VARCHAR(30),   
AddressOverflow    NVARCHAR(500))  
  
GO  
INSERT INTO Customers2 VALUES (  
'ALFKI',   
'Joe',  
'<Address>  
  <Address1>Maple St.</Address1>  
  <Address2>Apt. E105</Address2>  
  <City>Seattle</City>  
  <State>WA</State>  
  <Zip>98147</Zip>  
 </Address>')  
GO  
```  
  
 Inoltre, è necessario creare una directory virtuale per il database tempdb e un nome virtuale modello di tipo **modello** denominato "template".  
  
 Nell'esempio seguente lo schema di mapping recupera i dati non utilizzati archiviati nella colonna AddressOverflow della tabella Customers2:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="Customers2" sql:overflow-field="AddressOverflow" >  
    <xsd:complexType>  
      <xsd:attribute name="CustomerID"  type="xsd:integer"/>  
      <xsd:attribute name="ContactName"  type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Per testare una query Xpath di esempio sullo schema  
  
1.  Copiare il codice dello schema precedente e incollarlo in un file di testo. Salvare il file con il nome Overflow.xml.  
  
2.  Copiare il modello seguente e incollarlo in un file di testo. Salvare il file come OverflowT.xml nella stessa directory nella quale è stato salvato Overflow.xml. La query nel modello seleziona tutti i record nella tabella Customer2.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="Overflow.xml">  
            /Customers2  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Il percorso della directory specificato per lo schema di mapping (Overflow.xml) è relativo alla directory nella quale viene salvato il modello. È possibile specificare anche un percorso assoluto, ad esempio:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\Overflow.xml"  
    ```  
  
3.  Creare e utilizzare lo script di test SQLXML 4.0 (Sqlxml4test.vbs) per eseguire il modello.  

     Per ulteriori informazioni, vedere [utilizzo di ADO per eseguire query SQLXML 4,0](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Set di risultati:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customers2 CustomerID="ALFKI" ContactName="Joe">  
    <Address1>Maple St.</Address1>   
    <Address2>Apt. E105</Address2>   
    <City>Seattle</City>   
    <State>WA</State>   
    <Zip>98147</Zip>   
  </Customers2>  
</ROOT>  
```  
  
  
