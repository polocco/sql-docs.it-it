---
title: Metodo isClosed (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.isClosed
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3560ab18-4350-4d02-9716-439f0c2f7142
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 776c719a01378a30198b7a3bcc4134478ebeb742
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928673"
---
# <a name="isclosed-method-sqlserverconnection"></a>Metodo isClosed (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica se questo oggetto [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) è stato chiuso.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean isClosed()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se la connessione è chiusa. **false** in caso contrario.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo isClosed viene specificato dal metodo isClosed nell'interfaccia java.sql.Connection.  
  
 Verifica lo stato dell'oggetto SQLServerConnection chiamato. Una connessione viene chiusa se il metodo [close](../../../connect/jdbc/reference/close-method-sqlserverconnection.md) è stato chiamato su tale connessione o se si sono verificati determinati errori irreversibili. Questo metodo restituirà **true** solo se viene chiamato dopo la chiamata al metodo close.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
