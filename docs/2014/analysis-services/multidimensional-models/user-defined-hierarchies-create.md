---
title: Creare gerarchie definite dall'utente | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- user-defined hierarchies [Analysis Services]
ms.assetid: 16715b85-0630-4a8e-99b0-c0d213cade26
author: minewiskan
ms.author: owend
ms.openlocfilehash: 17e870a2b20125132342db1845689b7c2481d623
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2020
ms.locfileid: "84535789"
---
# <a name="create-user-defined-hierarchies"></a>Creare gerarchie definite dall'utente
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]consente di creare gerarchie definite dall'utente. Una gerarchia è una raccolta di livelli basata su attributi. Ad esempio, la gerarchia temporale potrebbe includere i livelli Anno, Trimestre, Mese, Settimana e Giorno. In alcune gerarchie, ogni attributo del membro comprende in modo univoco l'attributo del membro che si trova ad un livello superiore. A questo talvolta si fa riferimento come gerarchia naturale. Una gerarchia può essere utilizzata dagli utenti finali per esplorare i dati del cubo. Definire gerarchie utilizzando il riquadro Gerarchie di Progettazione Dimensioni in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Quando si crea una gerarchia definita dall'utente, è possibile che la gerarchia sia *incompleta*. In una gerarchia incompleta, il membro padre logico di almeno un membro non si trova nel livello immediatamente superiore rispetto al membro stesso. Se si ha una gerarchia incompleta, ci sono impostazioni che controllano se i membri mancanti sono visibili e come visualizzare i membri mancanti. Per altre informazioni, vedere [Gerarchie incomplete](user-defined-hierarchies-ragged-hierarchies.md).  
  
> [!NOTE]  
>  Per altre informazioni su problemi di prestazioni legati alla progettazione e alla configurazione delle gerarchie definite dall'utente, vedere la [Guida alle prestazioni di SQL Server 2005 Analysis Services](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà gerarchia utente](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)   
 [Proprietà livello &#91;pavimentate su&#93;](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md)   
 [Gerarchia padre-figlio](parent-child-dimension.md)  
  
  
