---
title: Metodo createBlob (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 630a93b0-6e3c-4255-a007-1097ce0ee243
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fee6b9fd1143991d6b18a3eb4d84a534c103163d
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927715"
---
# <a name="createblob-method-sqlserverconnection"></a>Metodo createBlob (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crea un oggetto Blob senza dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.Blob createBlob()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto Blob.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo createBlob viene specificato dal metodo createBlob nell'interfaccia java.sql.Connection.  
  
 Questo metodo sostituisce la necessità del [Costruttore SQLServerBlob &#40;SQLServerConnection, byte&#41;](../../../connect/jdbc/reference/sqlserverblob-constructor-sqlserverconnection-byte.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
