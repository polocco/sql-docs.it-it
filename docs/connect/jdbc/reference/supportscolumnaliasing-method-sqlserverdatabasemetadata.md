---
title: Metodo supportsColumnAliasing (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsColumnAliasing
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 85699f09-6456-4ee7-b46b-d6103e6ce0ab
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5997f81977ac91889ed6386abd820bb3ae22dd63
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80913187"
---
# <a name="supportscolumnaliasing-method-sqlserverdatabasemetadata"></a>Metodo supportsColumnAliasing (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un valore che indica se il database supporta l'aliasing delle colonne.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean supportsColumnAliasing()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se supportato. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo supportsColumnAliasing viene specificato dal metodo supportsColumnAliasing nell'interfaccia java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
