---
title: Utilizzo dell'associazione del set di righe (ODBC) . Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowset binding [ODBC]
ms.assetid: a7be05f0-6b11-4b53-9fbc-501e591eef09
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 05277e548dab36b22c023fe674e404d8b9014c7c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284571"
---
# <a name="use-rowset-binding-odbc"></a>Utilizzare l'associazione di set di righe (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
### <a name="to-use-column-wise-binding"></a>Per utilizzare l'associazione per colonna  
  
1.  Per ogni colonna associata, eseguire le operazioni seguenti:  
  
    -   Allocare una matrice di R (o più) buffer di colonna per archiviare i valori dei dati, dove R è il numero di righe del set di righe.  
  
    -   Facoltativamente, allocare una matrice di R (o più) buffer di colonna per archiviare le lunghezze dei dati.  
  
    -   Chiamare [SQLBindCol](../../../relational-databases/native-client-odbc-api/sqlbindcol.md) per associare le matrici di valori di dati e lunghezza dei dati della colonna alla colonna del set di righe.  
  
2.  Chiamare [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) per impostare gli attributi seguenti:  
  
    -   Impostare SQL_ATTR_ROW_ARRAY_SIZE sul numero di righe nel set di righe (R).  
  
    -   Impostare SQL_ATTR_ROW_BIND_TYPE su SQL_BIND_BY_COLUMN.  
  
    -   Impostare l'attributo SQL_ATTR_ROWS FETCHED_PTR affinché punti a una variabile SQLUINTEGER per mantenere il numero di righe recuperate.  
  
    -   Impostare SQL_ATTR_ROW_STATUS_PTR affinché punti a una matrice [R] di variabili SQLUSSMALLINT per mantenere gli indicatori di stato della riga.  
  
3.  Eseguire l'istruzione.  
  
4.  Ogni chiamata a [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) o [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) recupera le righe R e trasferisce i dati nelle colonne associate.  

### <a name="to-use-row-wise-binding"></a>Per utilizzare l'associazione per riga  
  
1.  Allocare una matrice [R] di strutture, dove R è il numero di righe nel set di righe. La struttura dispone di un elemento per ogni colonna e ogni elemento dispone di due parti:  
  
    -   La prima parte è una variabile del tipo di dati appropriato per mantenere i dati della colonna.  
  
    -   La seconda parte è una variabile SQLINTEGER per mantenere l'indicatore di stato della colonna.  
  
2.  Chiamare [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) per impostare gli attributi seguenti:  
  
    -   Impostare SQL_ATTR_ROW_ARRAY_SIZE sul numero di righe nel set di righe (R).  
  
    -   Impostare SQL_ATTR_ROW_BIND_TYPE sulla dimensione della struttura allocata nel Passaggio 1.  
  
    -   Impostare l'attributo SQL_ATTR_ROWS_FETCHED_PTR affinché punti a una variabile SQLUINTEGER per mantenere il numero di righe recuperate.  
  
    -   Impostare SQL_ATTR_PARAMS_STATUS_PTR affinché punti a una matrice [R] di variabili SQLUSSMALLINT per mantenere gli indicatori di stato della riga.  
  
3.  Per ogni colonna nel set di risultati, chiamare [SQLBindCol](../../../relational-databases/native-client-odbc-api/sqlbindcol.md) in modo che punti il valore dei dati e il puntatore alla lunghezza dei dati della colonna alle relative variabili nel primo elemento della matrice di strutture allocate nel passaggio 1.  
  
4.  Eseguire l'istruzione.  
  
5.  Ogni chiamata a [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) o [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) recupera le righe R e trasferisce i dati nelle colonne associate.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di argomenti relativi ai cursori &#40;&#41;ODBC](../../../relational-databases/native-client-odbc-how-to/cursors/using-cursors-how-to-topics-odbc.md)   
 [Modalità di implementazione dei cursori](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)   
 [Utilizzare i cursori &#40;&#41;ODBC](../../../relational-databases/native-client-odbc-how-to/cursors/use-cursors-odbc.md)  
  
  
