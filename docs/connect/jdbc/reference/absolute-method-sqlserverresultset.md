---
description: Metodo absolute (SQLServerResultSet)
title: Metodo absolute (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.absolute
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 638e8148-8ca0-4e1f-9ec2-04a11bc9809b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 260849163934c32cf1d671af024856f81cad7db3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438313"
---
# <a name="absolute-method-sqlserverresultset"></a>Metodo absolute (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Sposta il cursore nella riga specificata in questo oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean absolute(int row)  
```  
  
#### <a name="parameters"></a>Parametri  
 *row*  
  
 Valore **int** che indica il numero di riga in cui spostarsi. Può essere positivo, negativo o 0.  
  
## <a name="return-value"></a>Valore restituito  
 **true** se il cursore viene spostato nella posizione specificata. **false** se precede la prima riga o segue l'ultima riga.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo absolute viene specificato dal metodo absolute nell'interfaccia java.sql.ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
