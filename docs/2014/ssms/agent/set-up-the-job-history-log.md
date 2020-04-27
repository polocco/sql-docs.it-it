---
title: Impostare il log di cronologia processi | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 018e5c49-d3a0-4504-851a-f70996a34bb7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 613c0ccae7be912bd3bec63905b838b7f07b59b0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "63033579"
---
# <a name="set-up-the-job-history-log"></a>Impostare il log di cronologia processi
  In questo argomento viene descritto come configurare il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log cronologia processi di Agent.  
  
-   **Prima di iniziare**  [Sicurezza](#Security)  
  
-   **Per impostare il log di cronologia processi usando:**  [SQL Server Management Studio](#SSMS)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="security"></a><a name="Security"></a> Sicurezza  
 Per informazioni dettagliate, vedere [Implementazione della sicurezza di SQL Server Agent](implement-sql-server-agent-security.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMS"></a> Utilizzo di SQL Server Management Studio  
 **Per impostare il log di cronologia processo**  
  
1.  In **Esplora oggetti** connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], quindi espandere questa istanza.  
  
2.  Fare clic con il pulsante destro del mouse su **SQL Server Agent**, quindi scegliere **Proprietà**.  
  
3.  Nella finestra di dialogo **Proprietà SQL Server Agent** selezionare la pagina **Cronologia** .  
  
4.  È possibile scegliere tra le opzioni seguenti:  
  
    1.  Selezionare **Limita dimensioni log cronologia processo**e quindi immettere il numero massimo di righe consentito per il log di cronologia processo e il numero massimo di righe per processo.  
  
    2.  Selezionare **Rimuovi automaticamente cronologia dell'agente**e quindi specificare un periodo di tempo, in modo che la cronologia precedente a tale periodo venga eliminata dal log.  
  
## <a name="see-also"></a>Vedi anche  
 [Implementare processi](implement-jobs.md)   
 [Monitorare l'attività del processo](monitor-job-activity.md)   
 [Creazione di processi](create-jobs.md)  
  
  
