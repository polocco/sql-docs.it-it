---
title: DDL, funzioni, stored procedure e viste FILESTREAM | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
ms.assetid: 9ecb49ee-f64e-4d30-a803-e4064a21950a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5fdcf6fbc7a7c9eb325d87a5eec838a5854664c9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66010125"
---
# <a name="filestream-ddl-functions-stored-procedures-and-views"></a>DDL, funzioni, stored procedure e viste FILESTREAM
  Sono elencati le istruzioni Transact-SQL e gli oggetti di database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che supportano FILESTREAM.  
  
 Per l'elenco di oggetti di database che supportano la caratteristica FileTable, vedere [FileTable DDL, Functions, Stored Procedures, and Views](../views/views.md).  
  
##  <a name="transact-sql-data-definition-language-ddl-statements"></a><a name="ddl"></a> Istruzioni Transact-SQL DDL (Data Definition Language)  
  
-   [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
-   [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
-   [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql)  
  
-   [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)  
  
-   [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)  
  
-   [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)DROP INDEX  
  
##  <a name="system-functions"></a><a name="func"></a> Funzioni di sistema  
  
-   [GET_FILESTREAM_TRANSACTION_CONTEXT &#40;Transact-SQL&#41;](/sql/t-sql/functions/get-filestream-transaction-context-transact-sql)  
  
-   [PathName &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/pathname-transact-sql)  
  
##  <a name="system-stored-procedures"></a><a name="proc"></a> Stored procedure di sistema  
  
-   [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
-   [sp_filestream_force_garbage_collection &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection)  
  
##  <a name="system-views---catalog-views"></a><a name="cat"></a> Viste di sistema: viste del catalogo  
  
-   [sys.database_filestream_options &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql)  
  
##  <a name="system-views---dynamic-management-views"></a><a name="dmv"></a> Viste di sistema: DMV  
  
-   [sys.dm_filestream_file_io_handles &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-handles-transact-sql)  
  
-   [sys.dm_filestream_file_io_requests &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-filestream-file-io-requests-transact-sql)  
  
##  <a name="programming-apis"></a><a name="api"></a> API di programmazione  
  
-   [Accesso ai dati FILESTREAM con OpenSqlFilestream](access-filestream-data-with-opensqlfilestream.md)  
  
-   [API gestita - classe SqlFileStream](https://go.microsoft.com/fwlink/?LinkId=220875)  
  
  
