---
description: updateDateTimeOffset(int, microsoft.sql.DateTimeOffset) (SQLServerResultSet)
title: updateDateTimeOffset(int) (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 21ec0054-c808-4e88-9c8d-c71b696ce658
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1b8a6c4902dd4059a461b4d2947c789a393a0a4f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88353837"
---
# <a name="updatedatetimeoffsetint-microsoftsqldatetimeoffset-sqlserverresultset"></a>updateDateTimeOffset(int, microsoft.sql.DateTimeOffset) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Questo metodo è stato aggiunto in JDBC Driver 3.0 per [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Aggiorna il valore della colonna specificata al valore della [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md), secondo il numero ordinale di colonna in base zero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateDateTimeOffset(int index, microsoft.sql.DateTimeOffset x)  
```  
  
#### <a name="parameters"></a>Parametri  
 *index*  
  
 Numero ordinale in base zero di una colonna.  
  
 *x*  
  
 Oggetto [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md).  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 È possibile recuperare un valore della [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) con [SQLServerResultSet.getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md).  
  
## <a name="see-also"></a>Vedere anche  
 [updateDateTimeOffset &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatedatetimeoffset-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
