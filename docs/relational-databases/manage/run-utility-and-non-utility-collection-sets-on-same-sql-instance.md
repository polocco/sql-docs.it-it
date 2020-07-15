---
title: Eseguire i set di raccolta dell'utilità e non appartenenti all'utilità nella stessa istanza di SQL | Microsoft Docs
description: Informazioni su come monitorare un'istanza di SQL Server usando set di raccolta dell'utilità e non appartenenti all'utilità che funzionano affiancati. Visualizzare i requisiti di configurazione.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ca7ee9b3-ef9a-4ba4-83d0-9ee9f80dab27
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 522b21e2a2c7e78c8ca16483fc02f2564e0ebaf5
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773475"
---
# <a name="run-utility-and-non-utility-collection-sets-on-same-sql-instance"></a>Eseguire i set di raccolta dell'utilità e non appartenenti all'utilità nella stessa istanza di SQL
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  L'esecuzione side-by-side del set di raccolta di Utilità [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e dei set di raccolta non appartenenti a Utilità [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è supportata. Ciò significa che un'istanza gestita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può essere monitorata da altri set di raccolta anche se l'istanza è membro di un'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . È tuttavia necessario disabilitare la funzionalità della raccolta dati non appartenente all'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mentre l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene registrata nell'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Dopo la registrazione dell'istanza con il punto di controllo dell'utilità, è possibile riavviare i set di raccolta non appartenenti dell'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Tuttavia, tutti i set di raccolta sull'istanza gestita caricheranno i propri dati nel data warehouse di gestione dell'utilità (UMDW); il nome del file UMDW è sysutility_mdw.  
  
 Per eseguire side-by-side i set di raccolta dell'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e i set di raccolta non appartenenti all'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , tenere presente quanto segue:  
  
-   L'esecuzione side-by-side dei set di raccolta è supportata.  
  
-   È necessario disabilitare gli agenti di raccolta dati esistenti mentre si registrano le istanze nell'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Per soddisfare i requisiti della convalida, è necessario eseguire le stored procedure seguenti sull'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prima di creare un punto di controllo dell'utilità e su un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prima di registrarla nell'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
    ```  
    exec msdb.dbo.sp_syscollector_set_warehouse_database_name NULL  
    exec msdb.dbo.sp_syscollector_set_warehouse_instance_name NULL  
    ```  
  
     Se non si eseguono queste stored procedure prima di avviare la procedura guidata Crea punto di controllo dell'utilità o Aggiungi istanza gestita, l'operazione non riuscirà.  
  
-   È necessario utilizzare il data warehouse di gestione (sysutility_mdw) dell'utilità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per tutti i set di raccolta su un'istanza gestita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Attività e funzionalità di Utilità SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Configurare il data warehouse del punto di controllo dell'utilità &#40;Utilità SQL Server&#41;](../../relational-databases/manage/configure-your-utility-control-point-data-warehouse-sql-server-utility.md)  
  
  
