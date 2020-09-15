---
title: Tipi di dati Java
titleSuffix: SQL Server Language Extensions
description: Eseguire il mapping di tipi di dati da Java a SQL Server per strutture di dati di input e output e per parametri di input in sp_execute_external_script.
author: dphansen
ms.author: davidph
ms.date: 11/05/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7e5239520d6c19de51b20f33d43ce72bb1079eba
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2020
ms.locfileid: "88173543"
---
# <a name="java-and-sql-server-supported-data-types"></a>Tipi di dati Java e SQL Server supportati
[!INCLUDE [SQL Server 2019 and later](../../includes/applies-to-version/sqlserver2019.md)]

In questo articolo viene eseguito il mapping di tipi di dati SQL Server a tipi di dati Java per parametri e strutture di dati in [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

Sono attualmente supportati i tipi di dati SQL e Java seguenti per i set di dati di input/output e i parametri di input/output.

| Tipo di dati SQL        | Tipo di dati Java | Comment |
| ------------- |-------------|-|
| bit      | boolean | |
| Tinyint      | short      | |
| Smallint | short      | |
| Int | INT      | |
| Real | float      | |
| Bigint | long      | |
| float | double      | |
| nchar(n) | string      | |
| nvarchar(n) | string      | |
| binary(n) | byte[]      | |
| varbinary(n) | byte[]      | |
| nvarchar(max) | string      | |
| varbinary(max) | byte[]      | |
| UNIQUEIDENTIFIER | string | |
| char(n) | string | Sono supportate solo stringhe UTF8 |
| varchar(n) | string | Sono supportate solo stringhe UTF8 |
| ntext | string | Sono supportate solo stringhe UTF8 |
| Data | java.sql.date  | |
| NUMERIC | java.math.BigDecimal  | |
| decimal | java.math.BigDecimal  | |
| money | java.math.BigDecimal  | |
| SMALLMONEY | java.math.BigDecimal  | |
| smalldatetime | java.sql.timestamp  | |
| Datetime | java.sql.timestamp  | |
| datetime2 | java.sql.timestamp  | |


## <a name="next-steps"></a>Passaggi successivi

+ [Come chiamare Java in SQL Server](../how-to/call-java-from-sql.md)
