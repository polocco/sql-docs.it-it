---
title: Proprietà processo - Nuovo processo (pagina Generale)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.general.f1
ms.assetid: b6832840-1c18-4db8-94fc-080db880ae9f
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: eeb3b97ab94c9510ae66b3ebf6c018799dcf07a1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85764132"
---
# <a name="job-properties---new-job-general-page"></a>Proprietà processo - Nuovo processo (pagina Generale)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Usare questa pagina per visualizzare e modificare le proprietà generali di un processo di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="options"></a>Opzioni  
**Nome**  
Consente di modificare il nome del processo.  
  
**Proprietario**  
Consente di selezionare un proprietario per il processo.  
  
**Categoria**  
Consente di selezionare una categoria di processi per il processo.  
  
**...**  
Consente di visualizzare i processi della categoria selezionata.  
  
**Descrizione**  
Consente di modificare la descrizione del processo.  
  
**Enabled**  
Consente di abilitare il processo. Quando non è abilitato, il processo non viene eseguito in risposta a una pianificazione o a un avviso, sebbene sia comunque possibile avviare il processo usando la stored procedure **sp_start_job** .  
  
**Origine**  
Visualizza il server master per il processo. Questa opzione è disponibile solo nella pagina **Proprietà processo - Generale** .  
  
**Creato**  
Visualizza la data e l'ora di creazione del processo. Questa opzione è disponibile solo nella pagina **Proprietà processo - Generale** .  
  
**Data ultima modifica**  
Visualizza la data e l'ora dell'ultima modifica apportata al processo. Questa opzione è disponibile solo nella pagina **Proprietà processo - Generale** .  
  
**Data ultima esecuzione**  
Visualizza la data e l'ora dell'ultima esecuzione del processo. Questa opzione è disponibile solo nella pagina **Proprietà processo - Generale** .  
  
**Visualizza cronologia processo**  
Consente di visualizzare la cronologia processo per il processo. Questa opzione è disponibile solo nella pagina **Proprietà processo - Generale** .  
  
## <a name="see-also"></a>Vedere anche  
[Implementazione di processi](../../ssms/agent/implement-jobs.md)  
[Categorie di processi - Gestisci categorie di processi](../../ssms/agent/job-categories-manage-job-categories.md)  
  
