---
title: Copiare database in altri server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- servers [SQL Server], copying databases between
- bulk exporting [SQL Server], between servers
- database copying [SQL Server]
- migrating databases [SQL Server]
- moving databases
- copying databases
- bulk importing [SQL Server], between servers
ms.assetid: 978406d6-a3c8-4902-b1f4-4ced75234be5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d40c76281b3368505caee55af3def9f7f61f1696
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62872419"
---
# <a name="copy-databases-to-other-servers"></a>Copia di database in altri server
  È talvolta utile copiare un database da un computer a un altro, ad esempio per eseguire test o controlli di consistenza, sviluppare software, eseguire report, creare un database mirror o rendere il database disponibile per attività di filiali remote.  
  
 È possibile copiare un database in diversi modi:  
  
-   Utilizzo di Copia guidata database  
  
     È possibile utilizzare Copia guidata database per copiare o spostare database tra server o per aggiornare un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a una versione successiva. Per altre informazioni, vedere [Use the Copy Database Wizard](use-the-copy-database-wizard.md).  
  
-   Ripristinando un backup del database.  
  
     Per copiare un intero database è possibile utilizzare le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] BACKUP e RESTORE. Generalmente la copia di un database da un computer a un altro viene eseguita mediante il ripristino di un backup completo del database in oggetto per diverse ragioni. Per informazioni sull'uso delle operazioni di backup e ripristino allo scopo di eseguire la copia di un database, vedere [Copiare database tramite backup e ripristino](copy-databases-with-backup-and-restore.md).  
  
    > [!NOTE]  
    >  Per impostare un database mirror per il mirroring del database, è necessario ripristinare il database nel server mirror con RESTORE DATABASE *<nome_database>* WITH NORECOVERY. Per altre informazioni, vedere [Preparazione di un database mirror per il mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/prepare-a-mirror-database-for-mirroring-sql-server.md).  
  
-   Utilizzo della procedura guidata di generazione script per pubblicare database  
  
     È possibile utilizzare la procedura guidata Genera script per trasferire un database da un computer locale a un provider di hosting Web. Per altre informazioni, vedere [Procedura guidata Genera e pubblica script](../scripting/generate-and-publish-scripts-wizard.md).  
  
  
