---
description: Metodo nullsAreSortedLow (SQLServerDatabaseMetaData)
title: Metodo nullsAreSortedLow (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.nullsAreSortedLow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 30c06a9d-3513-42d0-8b2a-5a20ac31eb0e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 33239e2f4755adb526b9b81158efd2498702452f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433133"
---
# <a name="nullsaresortedlow-method-sqlserverdatabasemetadata"></a>Metodo nullsAreSortedLow (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un valore che indica se i valori NULL vengono posizionati in basso.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean nullsAreSortedLow()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se i valori vengono posizionati in basso. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo nullsAreSortedLow viene specificato dal metodo nullsAreSortedLow nell'interfaccia java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
