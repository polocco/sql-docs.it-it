---
description: Ottimizzazione dell'amministrazione automatizzata in un'organizzazione
title: Ottimizzazione dell'amministrazione automatizzata in un'organizzazione
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- performance [SQL Server], automated administration
- tuning automated administration [SQL Server]
- monitoring performance [SQL Server], automated administration
ms.assetid: 671fed35-3859-4b0d-8f38-4dd07436857e
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6fbb2e883e77ed797fb367c3624429c2b1a4d720
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/14/2020
ms.locfileid: "92038731"
---
# <a name="tune-automated-administration-across-an-enterprise"></a>Ottimizzazione dell'amministrazione automatizzata in un'organizzazione

[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In [Istanza gestita di SQL di Azure](/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte ma non tutte le funzionalità di SQL Server Agent. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita di SQL di Azure e SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

L'amministrazione multiserver implementata da Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sfrutta le caratteristiche di ottimizzazione automatica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. In condizioni normali, non è pertanto necessario eseguire ottimizzazioni dei processi aggiuntive. L'esecuzione di processi, la generazione di avvisi e le notifiche agli operatori possono tuttavia determinare un aumento dei carichi di rete e in questi casi è possibile ottimizzare l'amministrazione automatizzata all'interno di un'organizzazione in modo da ridurre al minimo il traffico di rete provocato da queste attività.  

## <a name="see-also"></a>Vedere anche

[Monitoraggio delle prestazioni del motore del flusso di dati](../../integration-services/performance/performance-counters.md)