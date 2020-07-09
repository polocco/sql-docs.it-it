---
title: Configurare il processo del set di transazioni (server di pubblicazione Oracle)
description: Informazioni su come configurare il processo del set di transazioni per un server di pubblicazione Oracle in un Sottoscrittore SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_publisherproperty
- Oracle publishing [SQL Server replication], configuring
ms.assetid: beea1a5c-0053-4971-a68f-0da53063fcbb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ff5338131ea2ee3d3e72efac857b430befad8ceb
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85897932"
---
# <a name="configure-the-transaction-set-job-for-an-oracle-publisher"></a>Configurare il processo del set di transazioni per un server di pubblicazione Oracle
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  **Xactset** è un processo del database Oracle creato dalla replica eseguita in un server di pubblicazione Oracle per la creazione di set di transazioni, qualora l'agente di lettura log non è connesso al server di pubblicazione. È possibile abilitare e configurare questo processo a livello di programmazione dal server di distribuzione, utilizzando le stored procedure di replica. Per altre informazioni, vedere [Ottimizzazione delle prestazioni per i server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md).  
  
### <a name="to-enable-the-transaction-set-job"></a>Per abilitare il processo del set di transazioni  
  
1.  Nel server di pubblicazione Oracle impostare il parametro di inizializzazione **job_queue_processes** su un valore sufficiente per consentire l'esecuzione del processo Xactset. Per ulteriori informazioni su questo parametro, vedere la documentazione del database relativa al server di pubblicazione Oracle.  
  
2.  Nel database di distribuzione eseguire [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Specificare il nome del server di pubblicazione Oracle per **\@publisher**, il valore **xactsetbatching** per **\@propertyname** e il valore **enabled** per **\@propertyvalue**.  
  
3.  Nel database di distribuzione eseguire [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Specificare il nome del server di pubblicazione Oracle per **\@publisher**, il valore **xactsetjobinterval** per **\@propertyname** e l'intervallo del processo espresso in minuti per **\@propertyvalue**.  
  
4.  Nel database di distribuzione eseguire [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Specificare il nome del server di pubblicazione Oracle per **\@publisher**, il valore **xactsetjob** per **\@propertyname** e il valore **enabled** per **\@propertyvalue**.  
  
### <a name="to-configure-the-transaction-set-job"></a>Per configurare il processo del set di transazioni  
  
1.  (Facoltativo) Nel database di distribuzione eseguire [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Specificare il nome del server di pubblicazione Oracle per **\@publisher**. Vengono restituite le proprietà del processo **Xactset** nel server di pubblicazione.  
  
2.  Nel database di distribuzione eseguire [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Specificare il nome del server di pubblicazione Oracle per **\@publisher**, il nome della proprietà del processo Xactset impostato per **\@propertyname** e la nuova impostazione per **\@propertyvalue**.  
  
3.  (Facoltativo) Ripetere il passaggio 2 per ogni proprietà del processo Xactset impostata. Se si modifica la proprietà **xactsetjobinterval** , è necessario riavviare il processo nel server di pubblicazione Oracle per rendere effettivo il nuovo intervallo.  
  
### <a name="to-view-properties-of-the-transaction-set-job"></a>Per visualizzare le proprietà del processo del set di transazioni  
  
1.  Nel server di distribuzione eseguire [sp_helpxactsetjob](../../../relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql.md). Specificare il nome del server di pubblicazione Oracle per **\@publisher**.  
  
### <a name="to-disable-the-transaction-set-job"></a>Per disabilitare il processo del set di transazioni  
  
1.  Nel database di distribuzione eseguire [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Specificare il nome del server di pubblicazione Oracle per **\@publisher**, il valore **xactsetjob** per **\@propertyname** e il valore **disabled** per **\@propertyvalue**.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene abilitato il processo `Xactset` e viene impostato un intervallo di tre minuti tra le esecuzioni.  
  
 [!code-sql[HowTo#sp_enable_xactsetjob](../../../relational-databases/replication/codesnippet/tsql/configure-the-transactio_1.sql)]  
  
## <a name="see-also"></a>Vedere anche  
 [Ottimizzazione delle prestazioni per i server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)   
 [Replication System Stored Procedures Concepts](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  
