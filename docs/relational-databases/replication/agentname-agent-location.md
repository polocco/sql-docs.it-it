---
description: Posizione in cui eseguire l'agente &lt;NomeAgente&gt;
title: Posizione in cui eseguire l'agente &lt;NomeAgente&gt; | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newsubwizard.agentlocation.f1
ms.assetid: dc664d80-fbe3-4586-aba8-a71fa62d14f0
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: b60c997ccd244be75c8946fb7465e2bdd98def66
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88470303"
---
# <a name="ltagentnamegt-agent-location"></a>Posizione in cui eseguire l'agente &lt;NomeAgente&gt;
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  L'agente di merge (per le sottoscrizioni di tipo merge) e l'agente di distribuzione (per le sottoscrizioni transazionali e snapshot) vengono eseguiti nel server di distribuzione o nel Sottoscrittore. Se l'agente viene eseguito nel server di distribuzione, la sottoscrizione viene denominata sottoscrizione push; mentre se l'agente viene eseguito nel Sottoscrittore, viene definita sottoscrizione pull. Per altre informazioni sulle sottoscrizioni push e pull, vedere [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md). Tutte le sottoscrizioni create in questo passaggio della procedura guidata risulteranno del tipo selezionato. Per creare sottoscrizioni di entrambi i tipi, è necessario eseguire due volte la procedura guidata.  
  
> [!NOTE]  
>  Dopo aver creato la sottoscrizione non è possibile modificarne il tipo.  
  
## <a name="see-also"></a>Vedere anche  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Panoramica degli agenti di replica](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
