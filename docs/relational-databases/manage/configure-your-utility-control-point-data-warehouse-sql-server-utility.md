---
title: Configurare il data warehouse del punto di controllo dell'utilità (Utilità SQL Server) | Microsoft Docs
description: Informazioni sul data warehouse di gestione dell'utilità, in cui le istanze di SQL Server archiviano i dati. Informazioni su come configurare il periodo di conservazione dei dati e la directory.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 06080937156afc4e38c9ef59bd9b92e98695eb57
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91867878"
---
# <a name="configure-your-utility-control-point-data-warehouse-sql-server-utility"></a>Configurazione del data warehouse del punto di controllo dell'utilità (Utilità SQL Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  I dati raccolti dalle istanze gestite di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono archiviati nel data warehouse di gestione dell'utilità. Il nome del file del data warehouse di gestione dell'utilità è sysutility_mdw.  
  
 È possibile configurare il periodo di memorizzazione dei dati in tale data warehouse. Per altre informazioni, vedere [Amministrazione utilità &#40;Utilità SQL Server&#41;](/previous-versions/sql/sql-server-2016/ee240832(v=sql.130)).  
  
 Le impostazioni di configurazione seguenti non sono configurabili in questa versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Nome del data warehouse di gestione dell'utilità (UMDW): Sysutility_mdw.  
  
-   Frequenza di caricamento del set di raccolta: ogni 15 minuti.  
  
 La directory del data warehouse di gestione dell'utilità è configurabile: \<System drive>:\Programmi\Microsoft SQL Server\MSSQL10_50.<Nome_UCP>\MSSQL\Data\\, dove \<System drive> è in genere l'unità C:\. Il file di log, Sysutility_mdw_\<GUID>_LOG, si trova nella stessa directory.  
  
> [!NOTE]  
>  È possibile modificare la posizione del file data warehouse di gestione dell'utilità (UMDW) sysutility_mdw utilizzando i comandi collega/scollega o l'istruzione ALTER DATABASE. È consigliabile utilizzare l'istruzione ALTER DATABASE. Per altre informazioni, vedere [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività e funzionalità di Utilità SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
