---
title: Aprire, visualizzare e stampare un file deadlock (SSMS)
ms.custom: seo-dt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- deadlocks [SQL Server], printing files
- deadlocks [SQL Server], opening files
- opening deadlock files
- printing deadlock files
ms.assetid: 5061b13f-2cb7-457a-b8d0-fbd437b510ab
author: julieMSFT
ms.author: jrasnick
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 61204492bad49c3d3d8ec01442cb9baca538a0f8
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85758875"
---
# <a name="open-view-and-print-a-deadlock-file-in-sql-server-management-studio-ssms"></a>Aprire, visualizzare e stampare un file deadlock in SQL Server Management Studio (SSMS)

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Quando tramite [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] viene generato un deadlock, è possibile acquisire e salvare le informazioni del deadlock in un file. Dopo avere salvato il file deadlock, è possibile aprirlo in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per visualizzarlo o stamparlo.  
  
## <a name="open-and-view-a-deadlock-file"></a>Aprire e visualizzare un file deadlock  
  
1. Scegliere **Apri** dal menu [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]File **di** e quindi selezionare **File**.  
  
2. Nella finestra di dialogo **Apri file** selezionare il tipo di file con estensione xdl nella casella **Tipo file** . Si ottiene un elenco filtrato contenente solo i file deadlock.  
  
## <a name="print-a-deadlock-file"></a>Stampare un file deadlock  
  
1. Scegliere **Apri** dal menu [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]File **di** e quindi selezionare **File**.  
  
2. Nella finestra di dialogo **Apri file** selezionare il tipo di file con estensione xdl nella casella **Tipo file** . Si ottiene un elenco filtrato contenente solo i file deadlock.  
  
3. Selezionare il file deadlock che si vuole stampare e quindi scegliere **Apri**.  
  
4. Scegliere **Stampa** dal menu **File**.  
  
## <a name="see-also"></a>Vedere anche  
 [Salvare eventi Deadlock Graph &#40;SQL Server Profiler&#41;](../../relational-databases/performance/save-deadlock-graphs-sql-server-profiler.md)  
  
  
