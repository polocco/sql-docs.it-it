---
description: Metodo getBinaryStream (java.lang.String)
title: Metodo getBinaryStream (java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getBinaryStream (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 149609b5-a6de-4e23-a440-7061775d0899
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8d0887b6cd8770310304596606ace6bba321465c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88437253"
---
# <a name="getbinarystream-method-javalangstring"></a>Metodo getBinaryStream (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore del nome della colonna designata nella riga corrente di questo oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) come flusso binario di byte non interpretati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.io.InputStream getBinaryStream(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnName*  
  
 Valore **String** contenente il nome della colonna.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto InputStream.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getBinaryStream viene specificato dal metodo getBinaryStream nell'interfaccia java.sql.ResultSet.  
  
 Questo metodo può essere usato solo con i tipi di dati binary, varbinary, varbinary(max) e image di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Se si tenta di utilizzarlo con altri tipi di dati genererà un'eccezione.  
  
 Una volta ottenuto il valore come flusso tramite questo metodo, tale valore può essere letto in blocchi dal flusso. Questo metodo è particolarmente adatto per il recupero di valori LONGVARBINARY di grandi dimensioni.  
  
> [!NOTE]  
>  Prima di ottenere il valore di qualsiasi altra colonna, è necessario leggere tutti i dati nel flusso restituito. La chiamata successiva a un metodo di richiamo chiude in modo implicito il flusso. Un flusso può anche restituire 0 quando viene chiamato il metodo InputStream.available, siano o meno disponibili dati.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getBinaryStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getbinarystream-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
