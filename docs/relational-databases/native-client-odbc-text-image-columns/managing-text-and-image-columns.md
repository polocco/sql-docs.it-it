---
title: Gestione delle colonne di testo e immagini Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- data types [ODBC], mapping
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 7b543556-ff36-4d35-ac08-de96223d92cd
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d3ac58e59f66dd107a9523a42f5647c90b4fb737
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297715"
---
# <a name="managing-text-and-image-columns"></a>Gestione di colonne di tipo text e image
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**I**dati text , **ntext**e **image** (noti anche come dati long) sono tipi di dati stringa binario o di tipo carattere che possono contenere valori di dati troppo grandi per essere inseriti nelle colonne **char**, **varchar**, **binary**o **varbinary** . Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo di dati **text** esegue il mapping al tipo di dati ODBC SQL_LONGVARCHAR. **ntext** viene mappato a SQL_WLONGVARCHAR; e mappe **immagine** per SQL_LONGVARBINARY. Alcuni elementi di dati, ad esempio i documenti lunghi o le bitmap di grandi dimensioni, potrebbero essere troppo grandi per essere archiviati correttamente in memoria. Per recuperare dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lunghi da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] parti sequenziali, il driver ODBC Native Client consente a un'applicazione di chiamare [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md). Per inviare dati lunghi in parti sequenziali, l'applicazione può chiamare [SQLPutData](../../relational-databases/native-client-odbc-api/sqlputdata.md). I parametri per i quali i dati vengono inviati in fase di esecuzione sono noti come parametri data-at-execution.  
  
 Un'applicazione può effettivamente scrivere o recuperare qualsiasi tipo di dati (non solo dati lunghi) con **SQLPutData** o **SQLGetData**, anche se solo i dati **di tipo carattere** e **binario** possono essere inviati o recuperati in parti. Tuttavia, se i dati sono sufficientemente piccoli da essere contenuti in un singolo buffer, non vi è in genere alcun motivo per utilizzare **SQLPutData** o **SQLGetData**. È molto più semplice associare il singolo buffer al parametro o alla colonna.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
-   [Colonne di tipo text e image associate e non associate](../../relational-databases/native-client-odbc-text-image-columns/bound-vs-unbound-text-and-image-columns.md)  
  
-   [Modifiche registrate e non registrate](../../relational-databases/native-client-odbc-text-image-columns/logged-vs-unlogged-modifications.md)  
  
-   [Colonne data-at-execution di tipo text, ntext o image](../../relational-databases/native-client-odbc-text-image-columns/data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
