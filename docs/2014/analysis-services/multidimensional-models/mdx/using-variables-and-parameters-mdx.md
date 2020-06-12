---
title: Utilizzo di variabili e parametri (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- parameters [MDX]
- queries [MDX], variables
- queries [MDX], parameters
- variables [MDX]
ms.assetid: a4754d16-d9c4-49f6-9be0-392180b912e4
author: minewiskan
ms.author: owend
ms.openlocfilehash: fd01cf78ea5e3284aa51cad7dc848176a5dc9298
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546153"
---
# <a name="using-variables-and-parameters-mdx"></a>Utilizzo di variabili e parametri (MDX)
  In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] è possibile parametrizzare un'istruzione MDX (Multidimensional Expressions). Un'istruzione parametrizzata consente di creare istruzioni generiche che possono essere personalizzate in fase di esecuzione.  
  
 Durante la creazione di un'istruzione parametrizzata, il nome del parametro viene identificato aggiungendovi come prefisso il simbolo chiocciola (@). Ad esempio, @Year sarebbe un nome di parametro valido  
  
 MDX supporta i parametri solo per valori letterali o scalari. Per creare un parametro che faccia riferimento a un membro, a un set o a una tupla, è possibile usare una funzione quale [StrToMember](/sql/mdx/strtomember-mdx) o [StrToSet](/sql/mdx/strtoset-mdx).  
  
 Nell'esempio seguente XML for Analysis (XMLA) il parametro conterrà @CountryName il paese per il quale vengono recuperati i dati del cliente:  
  
```  
<Envelope xmlns="http://schemas.xmlsoap.org/soap/envelope/">  
  <Body>  
    <Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
      <Command>  
        <Statement>  
select [Measures].members on 0,   
       Filter(Customer.[Customer Geography].Country.members,   
              Customer.[Customer Geography].CurrentMember.Name =  
              @CountryName) on 1  
from [Adventure Works]  
</Statement>  
      </Command>  
      <Properties />  
      <Parameters>  
        <Parameter>  
          <Name>CountryName</Name>  
          <Value>'United Kingdom'</Value>  
        </Parameter>  
      </Parameters>  
    </Execute>  
  </Body>  
</Envelope>  
```  
  
 Per utilizzare questa funzionalità con OLE DB, è necessario utilizzare l'interfaccia `ICommandWithParameters`. Per usare questa funzionalità con ADOMD.Net, è necessario usare l'interfaccia **AdomdCommand.Parameters** .  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali sullo scripting MDX &#40;Analysis Services&#41;](mdx-scripting-fundamentals-analysis-services.md)  
  
  
