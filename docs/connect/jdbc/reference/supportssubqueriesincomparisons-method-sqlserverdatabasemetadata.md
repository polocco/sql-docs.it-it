---
description: Metodo supportsSubqueriesInComparisons (SQLServerDatabaseMetaData)
title: Metodo supportsSubqueriesInComparisons (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsSubqueriesInComparisons
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 467d32e6-b47e-4095-9f8b-73e07fb814e8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 487dacc09950670df68cec5517a14a46378beeec
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450150"
---
# <a name="supportssubqueriesincomparisons-method-sqlserverdatabasemetadata"></a>Metodo supportsSubqueriesInComparisons (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un valore che indica se il database supporta le sottoquery nelle espressioni di confronto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean supportsSubqueriesInComparisons()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se supportato. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo supportsSubqueriesInComparisons viene specificato dal metodo supportsSubqueriesInComparisons nell'interfaccia java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
