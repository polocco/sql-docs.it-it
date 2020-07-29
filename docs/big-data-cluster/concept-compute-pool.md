---
title: Che cosa sono i pool di calcolo?
titleSuffix: SQL Server big data clusters
description: Questo articolo descrive il pool di calcolo di un cluster Big Data di SQL Server 2019.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c7afce300e40f6703cbe4c2d734751aa27256959
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730666"
---
# <a name="what-are-compute-pools-in-a-sql-server-big-data-cluster"></a>Che cosa sono i pool di calcolo in un cluster Big Data di SQL Server?

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

Questo articolo descrive il ruolo dei *pool di calcolo di SQL Server* in un cluster Big Data di SQL Server. I pool di calcolo forniscono risorse di calcolo di scale-out per un cluster Big Data. Le sezioni seguenti descrivono l'architettura e le funzionalità di un pool di calcolo.

È anche possibile guardare questo video di 5 minuti per un'introduzione ai pool di calcolo:

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Overview-Big-Data-Cluster-Compute-Pool/player?WT.mc_id=dataexposed-c9-niner]


## <a name="compute-pool-architecture"></a>Architettura dei pool di calcolo

Un pool di calcolo è costituito da uno o più pod di calcolo in esecuzione in Kubernetes. Le operazioni automatiche di creazione e gestione di questi pod sono coordinate dall'[istanza master di SQL Server](concept-master-instance.md). Ogni pod contiene un set di servizi di base e un'istanza del motore di database di SQL Server.

## <a name="scale-out-groups"></a>Gruppi con scalabilità orizzontale

Un pool di calcolo può svolgere la funzione di un gruppo con scalabilità orizzontale PolyBase per query distribuite tra origini dati diverse, ad esempio HDFS, Oracle, MongoDB o Teradata. Usando pod di calcolo in Kubernetes, i cluster Big Data possono automatizzare la creazione e la configurazione di pod di calcolo per gruppi PolyBase di scale-out.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sui [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)], vedere le risorse seguenti:

- [Che cosa sono i [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)
- [Workshop: Architettura Microsoft dei [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
