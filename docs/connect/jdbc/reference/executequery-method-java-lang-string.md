---
description: Metodo executeQuery (java.lang.String)
title: Metodo executeQuery (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.executeQuery (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 610205c2-6bcd-426c-ad6f-9682551efdec
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cff547cf27a6ef796e31383e524872717943b860
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88437703"
---
# <a name="executequery-method-javalangstring"></a>Metodo executeQuery (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Esegue l'istruzione SQL specificata e restituisce un solo oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final java.sql.ResultSet executeQuery(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sql*  
  
 Valore **String** contenente un'istruzione SQL.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto SQLServerResultSet.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo executeQuery viene specificato dal metodo executeQuery nell'interfaccia java.sql.Statement.  
  
 Questo metodo esegue l'override del metodo [executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) presente nella classe [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
 La chiamata di questo metodo genera un'eccezione perché l'istruzione SQL per l'oggetto SQLServerPreparedStatement viene specificata quando viene creato l'oggetto.  
  
 Viene generata l'eccezione [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) se l'istruzione SQL specificata produce un risultato diverso da un solo oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo executeQuery &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)   
 [Membri di SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Classe SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
