---
title: Tipo misto e contenuto semplice | Microsoft Docs
description: Viene visualizzato un esempio che mostra che SQL Server non supporta la creazione di un XML Schema che limita un tipo misto a un contenuto semplice.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- mixed types [SQL Server]
ms.assetid: 6ea1f11d-e64b-4ebb-ab68-4eb6e4027665
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 990ead43919e80a910860ee15a3758a36e2a1f93
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715127"
---
# <a name="mixed-type-and-simple-content"></a>Tipo misto e contenuto semplice
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non supporta la restrizione di un tipo misto in un contenuto semplice.  
  
## <a name="example"></a>Esempio  
 Nella raccolta di XML Schema seguente, `myComplexTypeA` è un tipo complesso che è possibile svuotare. Ovvero, entrambi gli elementi hanno `minOccurs` impostato su 0. Il tentativo di limitare ciò a un semplice contenuto, come nella dichiarazione `myComplexTypeB` , non è supportato. La creazione della raccolta di XML Schema seguente avrà esito negativo:  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://ns" xmlns:ns="http://ns"  
xmlns:ns1="http://ns1">  
  
    <complexType name="myComplexTypeA" mixed="true">  
        <sequence>  
            <element name="a" type="string" minOccurs="0"/>  
            <element name="b" type="string" minOccurs="0" maxOccurs="23"/>  
        </sequence>  
    </complexType>  
  
    <complexType name="myComplexTypeB">  
        <simpleContent>  
            <restriction base="ns:myComplexTypeA">  
                <simpleType>  
                    <restriction base="int">  
                        <minExclusive value="25"/>  
                    </restriction>  
                </simpleType>  
            </restriction>  
        </simpleContent>  
    </complexType>  
</schema>  
'  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Requisiti e limitazioni per le raccolte di XML Schema nel server](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
