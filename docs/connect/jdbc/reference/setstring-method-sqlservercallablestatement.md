---
description: Metodo setString (SQLServerCallableStatement)
title: Metodo setString (SQLServerCallableStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setString
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f38b97b5-d4f0-4f74-a33d-740241a85842
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6ab66f76ccc0f6c80c9358e56902c063ca5e1e15
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450713"
---
# <a name="setstring-method-sqlservercallablestatement"></a>Metodo setString (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il parametro designato sul valore **String** Java specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setString(java.lang.String sCol,  
                      java.lang.String s)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sCol*  
  
 Una **stringa** che contiene il nome del parametro.  
  
 *s*  
  
 Valore **String**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setString viene specificato dal metodo setString nell'interfaccia java.sql.CallableStatement.  
  
 Le conversioni da valori stringa a valori binari vengono eseguite solo quando il tipo di destinazione viene riconosciuto come binario da [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Nei casi in cui al driver JDBC non è noto il tipo sottostante, verrà passato il valore letterale **String** e verrà restituito un errore del server se il server non può eseguire la conversione.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
