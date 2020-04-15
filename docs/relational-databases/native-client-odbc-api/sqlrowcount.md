---
title: Proprietà SQLRowCount . Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLRowCount function
ms.assetid: 967ed3d4-3d31-4485-ac92-027076ebc829
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3cfb76dbd1732e32238c484f589d3b4696ff89d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302330"
---
# <a name="sqlrowcount"></a>SQLRowCount
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Quando vengono associate matrici di valori di parametro per l'esecuzione di istruzioni, **SQLRowCount** restituisce SQL_ERROR se qualsiasi riga di valori di parametro genera una condizione di errore nell'esecuzione dell'istruzione. Tramite l'argomento *RowCountPtr* della funzione non viene restituito alcun valore.  
  
 L'applicazione può sfruttare l'attributo di istruzione SQL_ATTR_PARAMS_PROCESSED_PTR per acquisire il numero di parametri elaborati prima del verificarsi dell'errore.  
  
 L'applicazione può inoltre utilizzare una matrice di valori di stato, associata tramite l'attributo di istruzione SQL_ATTR_PARAM_STATUS_PTR, per acquisire gli offset della matrice di righe di parametri con errori. L'applicazione può attraversare la matrice di stati per determinare il numero effettivo di righe elaborate.  
  
 Quando [!INCLUDE[tsql](../../includes/tsql-md.md)] viene eseguita un'istruzione INSERT, UPDATE, DELETE o MERGE con una clausola OUTPUT, SQLRowCount non restituirà il conteggio delle righe interessate fino a quando non sono state utilizzate tutte le righe nel set di risultati generato dalla clausola OUTPUT. Per gestire queste righe, chiamare SQLFetch o SQLFetchScroll.To sconsume these rows, you call SQLFetch or SQLFetchScroll. SQLResultCols restituirà -1 fino a quando non sono state utilizzate tutte le righe di risultati. Dopo SQLFetch o SQLFetchScroll restituisce SQL_NO_DATA, l'applicazione deve chiamare SQLRowCount per determinare il numero di righe interessate prima di chiamare SQLMoreResults per passare al risultato successivo.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzione SQLRowCountSQLRowCount Function](https://go.microsoft.com/fwlink/?LinkId=59367)   
 [Dettagli di implementazione dell'API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
