---
title: Più vincoli di precedenza | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- multiple precedence constraints
- precedence executables [Integration Services]
- precedence constraints [Integration Services], multiple
- constrained executables [Integration Services]
ms.assetid: 71c53ead-3d19-4bc1-aafd-e5b32595b420
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 61939b09b4a4365c09089df2b52026e96f9427ee
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84965151"
---
# <a name="multiple-precedence-constraints"></a>Più vincoli di precedenza
  Un vincolo di precedenza consente di connettere due eseguibili, ad esempio due attività, due contenitori o un'attività e un contenitore. Gli elementi connessi sono noti come eseguibile con precedenza ed eseguibile soggetto al vincolo. A un eseguibile soggetto a vincolo possono essere applicati più vincoli di precedenza. Per altre informazioni, vedere [Vincoli di precedenza](control-flow/precedence-constraints.md).  
  
 Raggruppando più vincoli è possibile definire scenari complessi, che consentono di implementare flussi di controllo complessi nei pacchetti. Nella figura seguente, ad esempio, l'attività D è collegata all'attività A da un vincolo `Success`, l'attività D è collegata all'attività B da un vincolo `Failure` e l'attività D è collegata all'attività C da un vincolo `Success`. I vincoli di precedenza tra le attività D e A, tra le attività D e B e tra le attività D e C sono legati da una relazione logica *e* . L'attività D viene quindi eseguita solo se l'attività A viene completata, l'attività B non viene eseguita e l'attività C deve essere eseguita correttamente.  
  
 ![Attività collegate in base ai vincoli di precedenza](media/precedenceconstraints.gif "Attività collegate in base ai vincoli di precedenza")  
  
## <a name="logicaland-property"></a>Proprietà LogicalAnd  
 Se a un'attività o contenitore sono applicati più vincoli, la proprietà `LogicalAnd` specificherà se il corrispondente vincolo di precedenza viene valutato singolarmente o insieme ad altri vincoli.  
  
 È possibile impostare la `LogicalAnd` proprietà utilizzando **Editor vincoli di precedenza** in [!INCLUDE[ssIS](../includes/ssis-md.md)] progettazione o nella finestra proprietà [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] fornita da.  
  
## <a name="related-tasks"></a>Attività correlate  
 [Impostazione delle proprietà di un vincolo di precedenza](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)  
  
  
