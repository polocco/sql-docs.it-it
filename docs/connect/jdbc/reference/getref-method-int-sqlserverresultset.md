---
description: Metodo getRef (int) (SQLServerResultSet)
title: Metodo getRef (int) (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getRef (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fc3f2d79-7cc3-47fa-a05e-4f7939d7f090
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 74db46cee4615a29827483c985e5cc8d1ce7f175
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434903"
---
# <a name="getref-method-int-sqlserverresultset"></a>Metodo getRef (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore dell'indice di colonna designato nella riga corrente di questo oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) come oggetto Ref nel linguaggio di programmazione Java.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.Ref getRef(int i)  
```  
  
#### <a name="parameters"></a>Parametri  
 *i*  
  
 Valore **int** che indica l'indice di colonna.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto Ref.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getRef viene specificato dal metodo getRef nell'interfaccia java.sql.ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getRef &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getref-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
