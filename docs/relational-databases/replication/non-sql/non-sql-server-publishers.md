---
title: Server di pubblicazione non SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 08/29/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- heterogeneous database replication, non-SQL Server Publishers
- non-SQL Server Publishers
- heterogeneous data sources, non-SQL Server Publishers
- Publishers [SQL Server replication], Oracle
ms.assetid: 08a160a6-33be-46b5-bc7b-d53180d8bdf1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9114317fde7ff4145c1008ccaf51bb5f0cec855f
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85893290"
---
# <a name="non-sql-server-publishers"></a>server di pubblicazione non SQL Server  
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

La pubblicazione di dati da origini non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] consente di consolidare i dati in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] consente la sottoscrizione di dati snapshot o transazionali pubblicati da un database Oracle. Per altre informazioni sulla pubblicazione da sistemi Oracle, vedere [Panoramica della pubblicazione Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporta gli scenari eterogenei seguenti per la replica transazionale e snapshot:  
  
-   Pubblicazione di dati da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a Sottoscrittori non[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  

-   Pubblicazione di dati da e verso Oracle con le limitazioni seguenti:  

  |Replica |2016 o versioni precedenti |2017 o versioni successive |
  |:-----------|:---------------|:-------------|
  |Replica da Oracle |Supporta solo Oracle 10g o versioni precedenti |Supporta solo Oracle 10g o versioni precedenti |
  |Replica verso Oracle |Fino a Oracle 12c |Non supportate |
  | &nbsp; | &nbsp; | &nbsp; |


 La replica eterogenea a Sottoscrittori non SQL Server è deprecata. La pubblicazione Oracle è deprecata. Per spostare dati, creare soluzioni utilizzando Change Data Capture e [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 La pubblicazione da database non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è ideale negli scenari seguenti:  
  
|Scenario|Descrizione|  
|--------------|-----------------|  
|Distribuzioni di applicazioni[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework|Sviluppo con [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , operando al contempo su dati replicati da un database non[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|Server di gestione temporanea di data warehousing|Mantenimento dei database di gestione temporanea di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sincronizzati con un database non[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|Migrazione a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Verifica dell'applicazione in tempo reale a fronte di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] replicando al contempo le modifiche del sistema di origine. Quando il risultato della migrazione è soddisfacente, passare a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
  
## <a name="see-also"></a>Vedere anche  
 [Replica di database eterogenei](../../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)  
  
  
