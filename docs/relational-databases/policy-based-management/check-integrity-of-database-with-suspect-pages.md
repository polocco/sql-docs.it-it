---
title: Verificare l'integrità di un database contenente pagine sospette | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3b1ec9fe-f6c5-46f7-aa63-6e671be1572d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: f37964a92e08e342be3d18213d47d634891fc30b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85654921"
---
# <a name="check-integrity-of-database-with-suspect-pages"></a>Verifica del'integrità di un database contenente pagine sospette
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Questa regola consente di controllare i database utente con stato impostato come sospetto. Quando il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] legge una pagina di database contenente un errore 824, la pagina viene considerata sospetta, l'ID di pagina corrispondente viene registrato nella tabella suspect_pages in msdb e il database contenente la pagina viene impostato come sospetto.  
  
 L'errore 824 indica che è stato rilevato un errore logico correlato alla consistenza durante un'operazione di lettura. Questo errore indica in genere il danneggiamento dei dati causato da un componente del sottosistema di I/O difettoso. Si tratta di una condizione di errore grave che può compromettere l'integrità del database e che deve essere corretta immediatamente.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
  
-   Esaminare il log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per individuare informazioni dettagliate sull'errore 824 per il database.  
  
-   Eseguire una verifica di coerenza del database ([DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)).  
  
-   Implementare le azioni dell'utente definite in [MSSQLSERVER_824](https://go.microsoft.com/fwlink/?LinkId=81397).  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Gestione della tabella suspect_pages &#40;SQL Server&#41;](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
