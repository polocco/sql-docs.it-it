---
description: Classe SQLServerException
title: Classe SQLServerException | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: af5ef257-7cf6-4db3-b1ee-07d22d82bef1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b096f1b41cc817b216cea9ff3618e7731abd5003
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450517"
---
# <a name="sqlserverexception-class"></a>Classe SQLServerException
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rappresenta un'esecuzione non riuscita o incompleta di un'istruzione SQL.  
  
 **Pacchetto:** com.microsoft.sqlserver.jdbc  
  
 **Estende:** java.sql.SQLException  
  
 **Implementa:** java.io.Serializable  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final class SQLServerException  
```  
  
## <a name="remarks"></a>Osservazioni  
 La classe SQLServerException gestisce sia i codici di stato SQL 92 che XOPEN. Sono intercambiabili tramite una proprietà di connessione specificata dall'utente. Le eccezioni vengono scritte in qualsiasi file di log aperto che è stato specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerException](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [Informazioni di riferimento sull'API del driver JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
