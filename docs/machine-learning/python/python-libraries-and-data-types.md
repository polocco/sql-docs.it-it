---
title: Convertire tipi di dati Python e SQL
description: Esaminare le conversioni dei tipi di dati implicite ed esplicite tra Python e SQL Server nelle soluzioni di data science e Machine Learning.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 10/06/2020
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=azuresqldb-mi-current||=sqlallproducts-allversions'
ms.openlocfilehash: 1d83caf3f80369da449175fca78a47677e10e861
ms.sourcegitcommit: 9774e2cb8c07d4f6027fa3a5bb2852e4396b3f68
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2020
ms.locfileid: "92098790"
---
# <a name="data-type-mappings-between-python-and-sql-server"></a>Mapping dei tipi di dati tra Python e SQL Server
[!INCLUDE [SQL Server 2017 SQL MI](../../includes/applies-to-version/sqlserver2017-asdbmi.md)]

Questo articolo elenca i tipi di dati supportati e le conversioni dei tipi di dati eseguite quando si usa la funzionalità di integrazione di Python in SQL Server Machine Learning Services.

Python supporta un numero limitato di tipi di dati rispetto a SQL Server. Di conseguenza, ogni volta che si usano dati di SQL Server all'interno di script Python, i dati SQL possono essere convertiti in modo implicito in un tipo di dati Python compatibile. Spesso, tuttavia, non è possibile eseguire automaticamente una conversione esatta e viene restituito un errore.

## <a name="python-and-sql-data-types"></a>Tipi di dati Python e SQL

Questa tabella elenca le conversioni implicite disponibili. Altri tipi di dati non sono supportati.

| Tipo SQL             | Tipo Python | Descrizione |
|----------------------|-------------|-------------|
| **bigint**           | `float64`   |
| **binary**           | `bytes`     |
| **bit**              | `bool`      |
| **char**             | `str`       |
| **date**             | `datetime`  |
| **datetime**         |`datetime`   | Supportato con SQL Server 2017 CU6 e versioni successive (con matrici **NumPy** di tipo `datetime.datetime` o `pandas.Timestamp` **Pandas**). `sp_execute_external_script` supporta ora i tipi `datetime` con i secondi frazionari.|
| **float**            | `float64`   |
| **nchar**            | `str`       |
| **nvarchar**         | `str`       |
| **nvarchar(max)**    | `str`       |
| **real**             | `float64`   |
| **smalldatetime**    | `datetime`  |
| **smallint**         | `int32`     |
| **tinyint**          | `int32`     |
| **uniqueidentifier** | `str`       |
| **varbinary**        | `bytes`     |
| **varbinary(max)**   | `bytes`     |
| **varchar(n)**       | `str`       |
| **ntext**     | `str`       |

## <a name="see-also"></a>Vedi anche

+ [Mapping dei tipi di dati tra R e SQL Server](../r/r-libraries-and-data-types.md)
