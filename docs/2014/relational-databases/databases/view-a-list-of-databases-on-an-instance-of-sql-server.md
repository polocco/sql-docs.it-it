---
title: Visualizzare un elenco di database in un'istanza di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- current databases
- databases currently on server [SQL Server]
- database list [SQL Server]
- viewing database list
- displaying database list
- databases [SQL Server], viewing
- servers [SQL Server], databases listed on
- listing databases
ms.assetid: 7ee7a789-db36-4be9-8a0e-0362a1e152dd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cdce1c0fc6f36bb0d58e93abba29ecab9d2dcd54
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62916966"
---
# <a name="view-a-list-of-databases-on-an-instance-of-sql-server"></a>Visualizzare un elenco di database in un'istanza di SQL Server
  In questo argomento si illustra come visualizzare un elenco di database in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'articolo**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Per visualizzare un elenco di database in un'istanza di SQL Server utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="security"></a><a name="Security"></a> Sicurezza  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorizzazioni  
 Se il chiamante di **sys.databases** non è il proprietario del database e il database non è **master** o **tempdb**, le autorizzazioni minime necessarie per visualizzare la riga corrispondente sono ALTER ANY DATABASE o VIEW ANY DATABASE a livello di server oppure l'autorizzazione CREATE DATABASE nel database **master** . Il database a cui è connesso il chiamante può essere sempre visualizzato in **sys.databases**.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Con SQL Server Management Studio  
  
#### <a name="to-view-a-list-of-databases-on-an-instance-of-sql-server"></a>Per visualizzare un elenco di database in un'istanza di SQL Server  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], quindi espandere questa istanza.  
  
2.  Per visualizzare un elenco di tutti i database dell'istanza, espandere **Database**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Con Transact-SQL  
  
#### <a name="to-view-a-list-of-databases-on-an-instance-of-sql-server"></a>Per visualizzare un elenco di database in un'istanza di SQL Server  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. In questo esempio viene restituito un elenco di database nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Nell'elenco sono inclusi i nomi dei database, i relativi ID di database, nonché le date di creazione dei database.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT name, database_id, create_date  
FROM sys.databases ;  
GO  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo di database e file &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql)   
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
