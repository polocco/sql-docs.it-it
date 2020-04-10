---
title: Metodo getAsciiStream (SQLServerClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerClob.getAsciiStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 134abe5e-5add-4d27-b333-b4b0f4d94c31
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 115e9a2670f89909c7551b31f7a4a163b1522afc
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925376"
---
# <a name="getasciistream-method-sqlserverclob"></a>Metodo getAsciiStream (SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Materializza l'oggetto CLOB come flusso ASCII.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.io.InputStream getAsciiStream()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Flusso di input che contiene i dati CLOB.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getAsciiStream viene specificato dal metodo getAsciiStream nell'interfaccia java.sql.Clob.  
  
 Restituisce sempre un flusso di byte e presuppone che i dati nell'oggetto CLOB siano in un formato ASCII in quanto non può sapere se siano in Unicode o qualsiasi altra tabella codici multibyte.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [Membri di SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [Classe SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
