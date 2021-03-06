---
title: Creare e accedere alle tabelle TempDB da stored procedure
description: TempDB non supporta la creazione e l'accesso alle tabelle dalle stored procedure compilate in modo nativo. Usare tabelle ottimizzate per la memoria, tipi di tabella e variabili di tabella.
ms.custom: seo-dt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 12be8011-b76c-45c1-8f55-7f46e0e374e9
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 50db7b7594aeb244f5408cbf48efde7dd0fd703c
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91867721"
---
# <a name="create-and-access-tables-in-tempdb-from-stored-procedures"></a>Creare e accedere alle tabelle in TempDB da stored procedure
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  La creazione e l'accesso alle tabelle in TempDB dalle stored procedure compilate in modo nativo non è supportato. Usare invece tabelle ottimizzate per la memoria con DURABILITY=SCHEMA_ONLY o tipi di tabella e variabili di tabella. 

Per altre informazioni sull'ottimizzazione della memoria di scenari con tabelle temporanee e variabili di tabella, vedere: [Tabella temporanea e variabile di tabella più rapide con l'ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md).
  
  L'esempio seguente mostra come usare una variabile di tabella **\@OrderQuantityByProduct** di tipo **dbo.OrderQuantityByProduct** anziché una tabella temporanea con tre colonne (ID, ProductID, Quantity):  
  
```sql  
CREATE TYPE dbo.OrderQuantityByProduct   
  AS TABLE   
   (id INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=100000),   
    ProductID INT NOT NULL,   
    Quantity INT NOT NULL) WITH (MEMORY_OPTIMIZED=ON)  
GO  
CREATE PROCEDURE dbo.usp_OrderQuantityByProduct   
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  
    TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
    LANGUAGE = N'ENGLISH'  
)  
  -- declare table variables for the list of orders   
  DECLARE @OrderQuantityByProduct dbo.OrderQuantityByProduct  
  
  -- populate input  
  INSERT @OrderQuantityByProduct SELECT ProductID, Quantity FROM dbo.[Order Details]  
  end  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di migrazione relativi alle stored procedure compilate in modo nativo](./a-guide-to-query-processing-for-memory-optimized-tables.md)   
 [Costrutti Transact-SQL non supportati da OLTP in memoria](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
