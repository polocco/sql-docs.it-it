---
title: Aggiungere una logica di business ai dati XML | Microsoft Docs
description: Informazioni su come aggiungere la logica di business ai dati XML applicando le trasformazioni XSL, l'uso di vincoli specifici del dominio per i dati o l'attivazione delle regole di convalida.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- business logic [XML]
ms.assetid: 0877fb38-f1a2-43d8-86cf-4754be224dc1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 524be57031368538271d1bde0016121644b9fed4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85729156"
---
# <a name="add-business-logic-to-xml-data"></a>Aggiunta di una logica di business ai dati XML
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Per aggiungere una logica di business ai dati XML è possibile procedere in vari modi:  
  
-   È possibile creare vincoli a livello di riga o colonna per applicare vincoli specifici del dominio durante la modifica e l'inserimento dei dati XML.  
  
-   È possibile creare sulla colonna XML un trigger che viene attivato all'inserimento o all'aggiornamento dei valori nella colonna. Tale trigger può contenere regole di convalida specifiche del dominio o popolare tabelle di proprietà.  
  
-   Il motore di database include la possibilità di eseguire codice gestito. È possibile usare l'integrazione con CLR (Common Language Runtime) per creare funzioni in codice gestito a cui passare valori XML e usare le funzionalità di elaborazione XML offerte dallo spazio dei nomi System.Xml. Ad esempio è possibile applicare la trasformazione XSL ai dati XML. In alternativa è possibile deserializzare il valore XML in una o più classi gestite ed utilizzare il codice gestito per agire su tali classi.  
  
-   È possibile creare funzioni e stored procedure Transact-SQL che avviano l'elaborazione della colonna XML in base alle esigenze aziendali.  
  
## <a name="example-applying-xsl-transformation"></a>Esempio: Applicazione della trasformazione XSL  
 Si consideri una funzione CLR **TransformXml()** che accetta un'istanza del tipo di dati **xml** e una trasformazione XSL archiviata in un file, applica la trasformazione ai dati XML e quindi restituisce il codice XML trasformato come risultato. Di seguito è riportato lo scheletro della funzione scritta in C#:  
  
```  
public static SqlXml TransformXml (SqlXml XmlData, string xslPath) {  
   // Load XSL transformation  
   XslCompiledTransform xform = new XslCompiledTransform();  
   XPathDocument xslDoc = new XPathDocument (xslPath);  
   xform.Load(xslDoc);  
  
   // Load XML data   
   XPathDocument xDoc = new XPathDocument (XmlData.CreateReader());  
  
   // Return the transformed value  
   MemoryStream xsltResult = new MemoryStream();  
   xform.Transform(xDoc, null, xsltResult);  
   SqlXml retSqlXml = new SqlXml(xsltResult);  
   return (retSqlXml);  
}   
```  
  
 Dopo aver registrato l'assembly e creato la funzione [!INCLUDE[tsql](../../includes/tsql-md.md)] definita dall'utente **SqlXslTransform()** corrispondente a **TransformXml()** è possibile chiamare la funzione da Transact-SQL come illustrato nella query seguente:  
  
```  
SELECT SqlXslTransform (xCol, 'C:\MyFile\xsltransform.xsl')  
FROM    T  
WHERE  xCol.exist('/book/title/text()[contains(.,"custom")]') =1;  
```  
  
 Il risultato della query contiene un set di righe con il valore XML trasformato.  
  
 L'integrazione di CLR in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] estende le possibilità di scomporre dati XML in tabelle o di promuovere le proprietà, nonché di eseguire query sui dati XML usando classi gestite nello spazio dei nomi System.Xml. Per altre informazioni, vedere [Dati XML &#40;SQL Server&#41;](../../relational-databases/xml/xml-data-sql-server.md).  
  
  
