---
description: Metodo getEnablePrepareOnFirstPreparedStatementCall (SQLServerDataSource)
title: Metodo getEnablePrepareOnFirstPreparedStatementCall (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 418e50a49972ba70a7e2ca85b57850c336935c78
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88436073"
---
# <a name="getenableprepareonfirstpreparedstatementcall-method-sqlserverdatasource"></a>Metodo getEnablePrepareOnFirstPreparedStatementCall (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce il valore della proprietà di connessione **enablePrepareOnFirstPreparedStatementCall**. Se questa configurazione restituisce false, la prima esecuzione di un'istruzione preparata chiamerà sp_executesql e non preparerà un'istruzione. La seconda esecuzione chiamerà sp_prepexec e configurerà effettivamente un handle per l'istruzione preparata. Le esecuzioni seguenti chiameranno sp_execute. Viene così eliminata la necessità di sp_unprepare alla chiusura dell'istruzione preparata se l'istruzione viene eseguita una sola volta. 
  
## <a name="syntax"></a>Sintassi  
  
```
public boolean getEnablePrepareOnFirstPreparedStatementCall();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce il valore **boolean** della proprietà di connessione **enablePrepareOnFirstPreparedStatementCall**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Osservazioni  
 Questo metodo è disponibile dal driver JDBC versione 6.4 e successive.
 
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
