---
title: Alcune repliche di disponibilità sono disconnesse | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.agp7allconnected.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: aea808be-6f0f-40c2-9aa2-a2a435ec6443
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b7393fe6d415f8b68758d75fafba91c9ab0a420c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62788416"
---
# <a name="some-availability-replicas-are-disconnected"></a>Alcune repliche di disponibilità sono disconnesse
    
## <a name="introduction"></a>Introduzione  
  
|||  
|-|-|  
|**Nome criterio**|Stato di connessione delle repliche di disponibilità|  
|**Problema**|Alcune repliche di disponibilità sono disconnesse.|  
|**Categoria**|**Avviso**|  
|**Facet**|gruppo di disponibilità|  
  
## <a name="description"></a>Descrizione  
 Questi criteri consentono di eseguire il rollup dello stato di connessione di tutte le repliche di disponibilità e di verificare tutte le repliche di disponibilità che sono disconnesse. I criteri sono in uno stato non integro quando una replica di disponibilità è disconnessa. Altrimenti, sono in uno stato integro.  
  
> [!NOTE]  
>   Per questa versione di [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], le informazioni sulle possibili cause e le soluzioni sono disponibili nella pagina relativa alla situazione in cui [alcune repliche di disponibilità sono disconnesse](https://go.microsoft.com/fwlink/p/?LinkId=220855) su Wiki di TechNet.  
  
## <a name="possible-causes"></a>Possibili cause  
 In questo gruppo di disponibilità, almeno una replica secondaria non è connessa alla replica primaria. Lo stato è DISCONNESSO.  
  
## <a name="possible-solution"></a>Possibile soluzione  
 Utilizzare lo stato dei criteri della replica di disponibilità per trovare quella disconnessa e risolvere il problema.  
  
## <a name="see-also"></a>Vedi anche  
 [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Usare il Dashboard Always On &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
