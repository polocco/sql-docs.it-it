---
title: Script di informazioni su database di distribuzione e server di pubblicazione | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Publishers [SQL Server replication], information scripts
- Distributors [SQL Server replication], information scripts
ms.assetid: 8622db47-c223-48fa-87ff-0b4362cd069a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 35b7c489b49a4463dc0b12f1469d1310f5d26fef
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "63186995"
---
# <a name="distributor-and-publisher-information-script"></a>Script di informazioni sui server di distribuzione e di pubblicazione
  Questo script utilizza le tabelle di sistema e le stored procedure di replica per rispondere a domande frequenti su oggetti presenti nei server di distribuzione e pubblicazione. Può essere utilizzato senza alcuna variazione e può inoltre costituire la base per la generazione di script personalizzati. Per eseguire lo script nel proprio ambiente potrebbe essere necessario apportare due modifiche:  
  
-   Modificare la riga `use AdventureWorks2012` per utilizzare il nome del database di pubblicazione in uso.  
  
-   Rimuovere i commenti (`--`) dalla riga `exec sp_helparticle @publication='<PublicationName>'` e sostituire \<NomePubblicazione> con il nome di una pubblicazione.  
  
```  
--********** Execute at the Distributor in the master database **********--  
  
USE master;  
go  
  
--Is the current server a Distributor?  
--Is the distribution database installed?  
--Are there other Publishers using this Distributor?  
EXEC sp_get_distributor  
  
--Is the current server a Distributor?  
SELECT is_distributor FROM sys.servers WHERE name='repl_distributor' AND data_source=@@servername;  
  
--Which databases on the Distributor are distribution databases?  
SELECT name FROM sys.databases WHERE is_distributor = 1  
  
--What are the Distributor and distribution database properties?  
EXEC sp_helpdistributor;  
EXEC sp_helpdistributiondb;  
EXEC sp_helpdistpublisher;  
  
--********** Execute at the Publisher in the master database **********--  
  
--Which databases are published for replication and what type of replication?  
EXEC sp_helpreplicationdboption;  
  
--Which databases are published using snapshot replication or transactional replication?  
SELECT name as tran_published_db FROM sys.databases WHERE is_published = 1;  
--Which databases are published using merge replication?  
SELECT name as merge_published_db FROM sys.databases WHERE is_merge_published = 1;  
  
--What are the properties for Subscribers that subscribe to publications at this Publisher?  
EXEC sp_helpsubscriberinfo;  
  
--********** Execute at the Publisher in the publication database **********--  
  
USE AdventureWorks2012;  
go  
  
--What are the snapshot and transactional publications in this database?   
EXEC sp_helppublication;  
--What are the articles in snapshot and transactional publications in this database?  
--REMOVE COMMENTS FROM NEXT LINE AND REPLACE <PublicationName> with the name of a publication  
--EXEC sp_helparticle @publication='<PublicationName>';  
  
--What are the merge publications in this database?   
EXEC sp_helpmergepublication;  
--What are the articles in merge publications in this database?  
EXEC sp_helpmergearticle; -- to return information on articles for a single publication, specify @publication='<PublicationName>'  
  
--Which objects in the database are published?  
SELECT name AS published_object, schema_id, is_published AS is_tran_published, is_merge_published, is_schema_published  
FROM sys.tables WHERE is_published = 1 or is_merge_published = 1 or is_schema_published = 1  
UNION  
SELECT name AS published_object, schema_id, 0, 0, is_schema_published  
FROM sys.procedures WHERE is_schema_published = 1  
UNION  
SELECT name AS published_object, schema_id, 0, 0, is_schema_published  
FROM sys.views WHERE is_schema_published = 1;  
  
--Which columns are published in snapshot or transactional publications in this database?  
SELECT object_name(object_id) AS tran_published_table, name AS published_column FROM sys.columns WHERE is_replicated = 1;  
  
--Which columns are published in merge publications in this database?  
SELECT object_name(object_id) AS merge_published_table, name AS published_column FROM sys.columns WHERE is_merge_published = 1;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Domande frequenti per gli amministratori di replica](frequently-asked-questions-for-replication-administrators.md)   
 [sp_get_distributor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-get-distributor-transact-sql)   
 [sp_helparticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql)   
 [sp_helpdistributiondb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql)   
 [sp_helpdistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql)   
 [sp_helpdistributor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql)   
 [sp_helpmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql)   
 [sp_helpmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)   
 [sp_helppublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)   
 [sp_helpreplicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpreplicationdboption-transact-sql)   
 [sp_helpsubscriberinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)   
 [sys.columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql)   
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)   
 [sys.procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-procedures-transact-sql)   
 [sys.servers &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-servers-transact-sql)   
 [sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql)   
 [sys.views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-views-transact-sql)  
  
  
