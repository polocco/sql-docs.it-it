---
title: Colonne contenenti un valore NULL per impostazione predefinita | Microsoft Docs
description: Informazioni su come usare le colonne che contengono un valore null per impostazione predefinita usando la frase parola chiave ELEMENTS XSINIL in SQL.
ms.custom: fresh2019may
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- columns [XML in SQL Server], null default value
ms.assetid: 9381c07f-6887-4a62-9730-32661f9aa87c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d6962f6117a857ed5875d503c259b4d54e8dd84d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85775600"
---
# <a name="columns-that-contain-a-null-value-by-default"></a>Colonne contenenti un valore NULL per impostazione predefinita

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Per impostazione predefinita, la presenza di un valore Null in una colonna corrisponde all'assenza dell'attributo, nodo o elemento. È possibile eseguire l'override di questo comportamento predefinito usando la frase parola chiave ELEMENTS XSINIL. Questa frase richiede codice XML incentrato sugli elementi. Ciò significa che i valori Null sono indicati in modo esplicito nei risultati restituiti. Questi elementi non conterranno alcun valore.

La frase ELEMENTS XSINIL è illustrata nell'esempio Transact-SQL SELECT riportato di seguito.

```sql
SELECT EmployeeID as "@EmpID",   
       FirstName  as "EmpName/First",   
       MiddleName as "EmpName/Middle",   
       LastName   as "EmpName/Last"  
FROM   HumanResources.Employee E, Person.Contact C  
WHERE  E.EmployeeID = C.ContactID  
  AND  E.EmployeeID=1
FOR XML PATH, ELEMENTS XSINIL;
```  
  
 Il risultato è illustrato di seguito. Non specificando XSINIL, l'elemento <`Middle`> non sarà presente.  
  
```xml
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" EmpID="1">  
  <EmpName>  
    <First>Gustavo</First>  
    <Middle xsi:nil="true" />  
    <Last>Achong</Last>  
  </EmpName>  
</row>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzare la modalità PATH con FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
