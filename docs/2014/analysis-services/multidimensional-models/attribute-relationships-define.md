---
title: Definire relazioni tra attributi | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Analysis Services], relationships
- relationships [Analysis Services], attributes
ms.assetid: 9184d344-e96d-4025-ad6f-3f75129746df
author: minewiskan
ms.author: owend
ms.openlocfilehash: d75bf3ec0aa6e7199b1e6f8d31e2602deb8efeff
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544673"
---
# <a name="define-attribute-relationships"></a>Definire relazioni tra attributi
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] gli attributi rappresentano il blocco predefinito fondamentale di una dimensione. Una dimensione contiene un set di attributi organizzato in base alle relazioni tra attributi.  
  
 Per ogni tabella inclusa in una dimensione, vi è una relazione tra attributi che mette in relazione l'attributo chiave della tabella agli altri attributi di quella tabella. Si crea questa relazione quando si crea la dimensione.  
  
 Una relazione tra attributi fornisce i vantaggi seguenti:  
  
-   Riduce la quantità di memoria necessaria per l'elaborazione della dimensione. Ciò consente di rendere più rapida l’elaborazione di dimensioni, partizioni e query.  
  
-   Aumenta le prestazioni di esecuzione delle query in quanto l'accesso all'archiviazione è più veloce ed i piani di esecuzione sono ottimizzati.  
  
-   Determina la selezione di aggregati più efficaci da parte degli algoritmi di progettazione delle aggregazioni, purché siano presenti gerarchie definite dall'utente nei percorsi delle relazioni.  
  
    > [!NOTE]  
    >  Per ulteriori informazioni sull'importanza e le implicazioni della definizione e della configurazione delle relazioni tra attributi, vedere la sezione relativa all'ottimizzazione delle prestazioni delle query nella [Guida alle prestazioni di SQL Server 2005 Analysis Services](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).  
  
## <a name="attribute-relationship-considerations"></a>Considerazioni sulle relazioni tra attributi  
 Quando i dati sottostanti lo supportano, si devono definire anche relazioni univoche tra attributi. Per definire relazioni tra attributi univoche, usare la scheda **Relazioni tra attributi** di Progettazione dimensioni.  
  
 Qualsiasi attributo che ha una relazione in uscita deve avere una chiave univoca relativa all'attributo correlato. In altre parole, un membro in un attributo di origine deve identificare un solo membro in un attributo correlato. Si consideri, ad esempio, la relazione, Città -> Stato. In questa relazione, l'attributo di origine è Città e l'attributo correlato è Stato. L'attributo di origine è il lato "molti" e il lato correlato è il lato "uno" della relazione molti-a-uno. La chiave per l'attributo di origine sarebbe Città + Stato. Per altre informazioni, vedere [Creare, modificare o eliminare una relazione tra attributi](attribute-relationships-create-modify-or-delete-relationship.md).  
  
 Per altre informazioni sulle proprietà di una relazione tra attributi, vedere [Configurare le proprietà della relazione tra attributi](attribute-relationships-configure-attribute-properties.md).  
  
> [!NOTE]  
>  Definire erroneamente relazioni tra attributi può produrre risultati della query non validi.  
  
## <a name="see-also"></a>Vedere anche  
 [Relazioni tra attributi](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)  
  
  
