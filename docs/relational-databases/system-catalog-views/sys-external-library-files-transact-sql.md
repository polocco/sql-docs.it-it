---
title: sys. external_library_files (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2019
ms.prod: sql
ms.technology: machine-learning
ms.topic: language-reference
f1_keywords:
- external_library_files
- external_library_files_TSQL
- sys.external_library_files
- sys.external_library_files_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_library_files catalog view
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b2f1bbdc3936dc6295b9ecc51b937e50cae20670
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "80664235"
---
# <a name="sysexternal_library_files-transact-sql"></a>sys.external_library_files (Transact-SQL)  
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Elenca una riga per ogni file che costituisce una libreria esterna.

|Nome colonna |Tipo di dati |Descrizione|
|------|------|-----|
|external_library_id | INT |ID dell'oggetto libreria esterna. |
|content |varbinary(max) |Contenuto dell'elemento del file di libreria esterno. |
|Piattaforma |TINYINT |ID della piattaforma host in cui è installato SQL Server. |
|platform_desc | nvarchar(60) |Nome della piattaforma host. I valori validi sono ' WINDOWS ',' LINUX '. |

### <a name="see-also"></a>Vedere anche  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[CREA LIBRERIA ESTERNA](../../t-sql/statements/create-external-library-transact-sql.md)  

