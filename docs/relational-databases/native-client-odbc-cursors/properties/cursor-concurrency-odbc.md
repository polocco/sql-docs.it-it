---
title: Concorrenza del cursore (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- concurrency [ODBC]
- cursors [ODBC], concurrency
- ODBC cursors, concurrency
ms.assetid: 68228ece-cbf1-4f19-bfdc-053884c1af48
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 309bfb0313adeeb0002910975c0a484461ea608c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298371"
---
# <a name="cursor-concurrency-odbc"></a>Concorrenza dei cursori (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le operazioni dei cursori, come i tipi di cursore, sono influenzate dalle opzioni di concorrenza impostate dall'applicazione. Le opzioni di concorrenza vengono impostate utilizzando l'opzione SQL_ATTR_CONCURRENCY di [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md). I tipi di concorrenza sono i seguenti:  
  
-   Di sola lettura (SQL_CONCUR_READONLY)  
  
-   Valori (SQL_CONCUR_VALUES)  
  
-   Versione di riga (SQL_CONCUR_ROWVER)  
  
-   Blocco (SQL_CONCUR_LOCK)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà del cursore](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
