---
title: 'Esempio: specifica della direttiva ELEMENT e della codifica di entità | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- ELEMENT directive
- entity encoding [XML]
ms.assetid: 50cda5c1-7293-4080-93b3-872e3b8d484e
author: rothja
ms.author: jroth
ms.openlocfilehash: cadbc9e06530706f0b1e1406af7b38b72246303f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85067826"
---
# <a name="example-specifying-the-element-directive-and-entity-encoding"></a>Esempio: specifica della direttiva ELEMENT e della codifica di entità
  In questo esempio viene illustrata la differenza fra le direttive **ELEMENT** e **XML** . La direttiva **ELEMENT** sostituisce i dati con entità, mentre la direttiva **XML** non esegue questa operazione. All' \<Summary> elemento viene assegnato XML, `<Summary>This is summary description</Summary>` , nella query.  
  
 Considerare la query seguente:  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        NULL            as [Summary!2!SummaryDescription!ELEMENT]  
FROM    Production.ProductModel  
WHERE   ProductModelID=19  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        NULL,  
       '<Summary>This is summary description</Summary>'  
FROM   Production.ProductModel  
WHERE  ProductModelID=19  
FOR XML EXPLICIT  
```  
  
 Di seguito è riportato il risultato. Nel risultato la descrizione di riepilogo viene sostituita con entità.  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription><Summary>This is summary description</Summary></SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 Se nel nome della colonna **si specifica la direttiva** XML `Summary!2!SummaryDescription!XML`invece della direttiva **ELEMENT** , si otterrà la descrizione di riepilogo senza sostituzione con entità.  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription>  
      <Summary>This is summary description</Summary>  
    </SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 Invece di assegnare un valore XML statico, la query seguente usa il metodo **query()** del tipo **xml** per recuperare la descrizione di riepilogo del modello di prodotto dalla colonna CatalogDescription di tipo **xml** . Poiché è noto che il risultato sarà di tipo **xml** , non viene applicata la sostituzione con entità.  
  
```  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        NULL            as [Summary!2!SummaryDescription]  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not null  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        Name,  
       (SELECT CatalogDescription.query('  
            declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
          /pd:ProductDescription/pd:Summary'))  
FROM     Production.ProductModel  
WHERE    CatalogDescription is not null  
ORDER BY [ProductModel!1!ProdModelID],Tag  
FOR XML EXPLICIT  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Usare la modalità EXPLICIT con FOR XML](use-explicit-mode-with-for-xml.md)  
  
  
