---
title: Definizione di tabelle e colonne UDT | Microsoft Docs
description: Dopo aver registrato l'assembly che contiene una definizione del tipo definito dall'utente, è possibile utilizzarlo in una definizione di colonna.
ms.custom: ''
ms.date: 12/05/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- user-defined types [CLR integration], columns
- UDTs [CLR integration], columns
- columns [CLR integration]
- user-defined types [CLR integration], tables
- tables [CLR integration]
- UDTs [CLR integration], tables
- UDTs [CLR integration], indexes
- user-defined types [CLR integration], indexes
- indexes [CLR integration]
ms.assetid: aea495f4-ce26-4952-b019-38f012625f3f
author: rothja
ms.author: jroth
ms.openlocfilehash: 7fc857b99772983d925504357f641f89780fdd67
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727774"
---
# <a name="working-with-user-defined-types---defining-udt-tables-and-columns"></a>Uso di tipi definiti dall'utente - Definizione di tabelle e colonne UDT
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Una volta che l'assembly contenente la definizione del tipo definito dall'utente (UDT) è stato registrato in un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, può essere utilizzato in una definizione di colonna. Per altre informazioni, vedere [CREATE TYPE (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md).  
  
## <a name="creating-tables-with-udts"></a>Creazione di tabelle con tipo definito dall'utente  
 Per la creazione di una colonna con tipo definito dall'utente in una tabella non è necessaria una sintassi speciale. È possibile utilizzare il nome del tipo definito dall'utente in una definizione di colonna come se fosse uno dei tipi di dati intrinseci di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'istruzione CREATE TABLE seguente [!INCLUDE[tsql](../../includes/tsql-md.md)] Crea una tabella denominata **Points**, con una colonna denominata **ID,** definita come colonna Identity **int** e la chiave primaria per la tabella. La seconda colonna è denominata **PointValue**, con tipo di dati **Point**. Il nome dello schema utilizzato in questo esempio è **dbo**. Si noti che per specificare un nome di schema è necessario disporre delle autorizzazioni appropriate. Se si omette il nome dello schema, viene utilizzato lo schema predefinito per l'utente del database.  
  
```sql  
CREATE TABLE dbo.Points   
(ID int IDENTITY(1,1) PRIMARY KEY, PointValue Point)  
```  
  
## <a name="creating-indexes-on-udt-columns"></a>Creazione di indici in colonne con tipo definito dall'utente  
 Per indicizzare una colonna con tipo definito dall'utente, sono disponibili due opzioni:  
  
-   **Indicizzare il valore completo.** In questo caso, se il tipo definito dall'utente ha ordinamento binario, è possibile creare un indice sull'intera colonna con tipo definito dall'utente utilizzando l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE INDEX.  
  
-   **Indicizzare espressioni dei tipi definiti dall'utente.** È possibile creare indici in colonne calcolate persistenti su espressioni dei tipi definiti dall'utente. L'espressione del tipo definito dall'utente può essere un campo, un metodo o una proprietà di un tipo definito dall'utente. L'espressione deve essere deterministica e non deve eseguire accesso ai dati.  
  
 Per altre informazioni, vedere [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di tipi definiti dall'utente in SQL Server](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md)     
 [CREATE TYPE (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md)     
 [Tipi CLR definiti dall'utente](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)     
