---
description: Metodo getWorkstationID (SQLServerDataSource)
title: Metodo getWorkstationID (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getWorkstationID
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f6a701de-a8fa-4668-9310-99a8c6e32c88
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 44ba105413506ed95e5417e4a5f8b231aca19784
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433763"
---
# <a name="getworkstationid-method-sqlserverdatasource"></a>Metodo getWorkstationID (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce il nome del computer client utilizzato per la connessione all'origine dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getWorkstationID()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Valore **String** contenente il nome del computer client.  
  
## <a name="remarks"></a>Osservazioni  
 L'oggetto workstationID è il nome del computer o della workstation client. Se la proprietà workstationID non è impostata, il valore predefinito viene costruito chiamando il metodo InetAddress.getLocalHost().getHostName(). Se getHostName restituisce un valore vuoto, viene chiamato il metodo getHostAddress().toString().  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
