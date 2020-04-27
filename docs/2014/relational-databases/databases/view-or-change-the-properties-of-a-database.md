---
title: Visualizzare o modificare le proprietà di un database | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- displaying databases
- database viewing [SQL Server]
- databases [SQL Server], viewing
- viewing databases
ms.assetid: 9e8ac097-84b7-46c7-85e3-c1e79f94d747
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 10ad92286011f6f81fbaff5ab4908007e16bdd45
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62870951"
---
# <a name="view-or-change-the-properties-of-a-database"></a>Visualizzare o modificare le proprietà di un database
  In questo argomento si illustra come visualizzare o modificare le proprietà di un database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Dopo aver modificato la proprietà di un database, la modifica diventa effettiva immediatamente.  
  
 **Contenuto dell'articolo**  
  
-   **Prima di iniziare:**  
  
     [Indicazioni](#Recommendations)  
  
     [Sicurezza](#Security)  
  
-   **Per visualizzare o modificare le proprietà di un database utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Raccomandazioni  
  
-   Se l'opzione AUTO_CLOSE è impostata su ON, alcune colonne nella vista del catalogo [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) e della funzione DATABASEPROPERTYEX restituiranno NULL perché il database non è disponibile per il recupero dei dati. Per risolvere questo problema, eseguire un'istruzione USE per aprire il database.  
  
###  <a name="security"></a><a name="Security"></a> Sicurezza  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorizzazioni  
 È richiesta l'autorizzazione ALTER per il database.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-view-or-change-the-properties-of-a-database"></a>Per visualizzare o modificare le proprietà di un database  
  
1.  In **Esplora oggetti**connettersi a un'istanza del, quindi [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]espandere l'istanza.  
  
2.  Espandere **Database**, fare clic con il pulsante destro del mouse sul database da visualizzare, quindi scegliere **Proprietà**.  
  
3.  Nella finestra di dialogo **Proprietà database** selezionare una pagina per visualizzare le informazioni corrispondenti. Selezionare la pagina **File** , ad esempio, per visualizzare le informazioni sui file di dati e di log.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-view-a-property-of-a-database-by-using-databasepropertyex"></a>Per visualizzare una proprietà di un database tramite DATABASEPROPERTYEX  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. Questo esempio usa la funzione di sistema [DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql) per restituire lo stato dell'opzione di database AUTO_SHRINK nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Un valore restituito pari a 1 indica che l'opzione è impostata su ON, mentre un valore restituito pari a 0 indica che l'opzione è impostata su OFF.  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT DATABASEPROPERTYEX('AdventureWorks2012', 'IsAutoShrink');  
GO  
  
```  
  
#### <a name="to-view-the-properties-of-a-database-by-querying-sysdatabases"></a>Per visualizzare le proprietà di un database eseguendo una query su sys.databases  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. In questo esempio si esegue una query sulla vista del catalogo [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) per visualizzare diverse proprietà del database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . In questo esempio viene restituito il numero ID del database (`database_id`), se il database è di sola lettura o di lettura e scrittura (`is_read_only`), le regole di confronto per il database (`collation_name`), nonché il livello di compatibilità del database (`compatibility_level`).  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT database_id, is_read_only, collation_name, compatibility_level  
FROM sys.databases WHERE name = 'AdventureWorks2012';  
GO  
  
```  
  
#### <a name="to-change-the-properties-of-a-database"></a>Per modificare le proprietà di un database  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query. Nell'esempio si determina lo stato di isolamento dello snapshot nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] , si modifica lo stato della proprietà, quindi si verifica la modifica.  
  
     Per determinare lo stato di isolamento dello snapshot, selezionare la prima istruzione `SELECT` e fare clic su **Esegui**.  
  
     Per modificare lo stato di isolamento dello snapshot, selezionare la prima istruzione `ALTER DATABASE` e fare clic su **Esegui**.  
  
     Per verificare la modifica, selezionare la seconda istruzione `SELECT` e fare clic su **Esegui**.  
  
 [!code-sql[DatabaseDDL#AlterDatabase9](../../snippets/tsql/SQL14/tsql/databaseddl/transact-sql/alterdatabase.sql#alterdatabase9)]  
  
## <a name="see-also"></a>Vedi anche  
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)   
 [ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-hadr)   
 [Opzioni ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)   
 [Mirroring del database ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [Livello di compatibilità ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)   
 [Opzioni per file e filegroup ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)  
  
  
