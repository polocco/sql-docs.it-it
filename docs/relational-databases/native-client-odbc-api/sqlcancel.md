---
description: SQLCancel
title: SQLCancel | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 86f50105acb4c506b6ecb937ff0f302f32b24bb3
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2020
ms.locfileid: "91811141"
---
# <a name="sqlcancel"></a>SQLCancel
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Nell' [argomento SQLCancel](../../odbc/reference/syntax/sqlcancel-function.md) si afferma che in ODBC 2. x, se un'applicazione **chiama SQLCancel** quando non viene eseguita alcuna elaborazione sull'istruzione, **SQLCancel** ha lo stesso effetto di **SQLFreeStmt** con l'opzione **SQL_CLOSE** ; Questo comportamento viene definito solo per completezza e le applicazioni devono chiamare **SQLFreeStmt** o **SQLCloseCursor** per chiudere i cursori. Tuttavia, anche se l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applicazione client nativa imposta la versione dell'API ODBC su 3.5. x o versioni successive, la funzione **SQLCancel** utilizzerà il comportamento ODBC 2. x.  
  
## <a name="see-also"></a>Vedere anche  
 [SQLCancel](../../odbc/reference/syntax/sqlcancel-function.md)   
 [Dettagli di implementazione dell'API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
