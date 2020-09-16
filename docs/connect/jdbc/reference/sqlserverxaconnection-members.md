---
description: Membri di SQLServerXAConnection
title: Membri di SQLServerXAConnection | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4b61dabd-369b-460c-8450-9fe424f76541
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9b0c1f613cfa44859c51bf4429939e93c157d75a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88462543"
---
# <a name="sqlserverxaconnection-members"></a>Membri di SQLServerXAConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Nelle tabelle seguenti sono elencati i membri esposti dalla classe [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md).  
  
## <a name="constructors"></a>Costruttori  
 Nessuno.  
  
## <a name="fields"></a>Campi  
 No.  
  
## <a name="inherited-fields"></a>Campi ereditati  
 No.  
  
## <a name="methods"></a>Metodi  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[addConnectionEventListener](../../../connect/jdbc/reference/addconnectioneventlistener-method-sqlserverpooledconnection.md)|Ereditato da [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md). Registra il listener di eventi specificato in modo che riceva una notifica quando si verifica un evento su questo oggetto Connection.|  
|[close](../../../connect/jdbc/reference/close-method-sqlserverpooledconnection.md)|Ereditato da [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md). Chiude la connessione fisica rappresentata da questo oggetto Connection.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverpooledconnection.md)|Ereditato da [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md). Crea un handle di oggetto per la connessione fisica rappresentata da questo oggetto Connection.|  
|[getXAResource](../../../connect/jdbc/reference/getxaresource-method-sqlserverxaconnection.md)|Recupera un oggetto [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) che verrà usato dal servizio di gestione transazioni per gestire la partecipazione di questo oggetto [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) in una transazione distribuita.|  
|[removeConnectionEventListener](../../../connect/jdbc/reference/removeconnectioneventlistener-method-sqlserverpooledconnection.md)|Ereditato da [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md). Rimuove il listener di eventi specificato.|  
  
## <a name="inherited-methods"></a>Metodi ereditati  
  
|Classe ereditata da:|Metodi|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerPooledConnection|addConnectionEventListener, close, getConnection, removeConnectionEventListener|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|javax.sql.PooledConnection|addConnectionEventListener, close, getConnection, removeConnectionEventListener|  
  
## <a name="see-also"></a>Vedere anche  
 [Classe SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)  
  
  
