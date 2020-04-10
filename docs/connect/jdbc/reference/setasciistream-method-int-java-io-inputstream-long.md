---
title: Metodo setAsciiStream (int, java.io.InputStream, long) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9dfa7781-d72f-407a-a8d4-1c78c9446d09
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e095e139cb4f37fe44c3107d4f3a8f30f038bf06
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920173"
---
# <a name="setasciistream-method-int-javaioinputstream-long"></a>Metodo setAsciiStream (int, java.io.InputStream, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il numero di parametro designato sull'oggetto java.io.InputStream specificato, con il numero di byte specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final void setAsciiStream(int parameterIndex,  
                                 java.io.InputStream x,  
                                    long length)  
```  
  
#### <a name="parameters"></a>Parametri  
 *parameterIndex*  
  
 Valore **int** che indica il numero di parametro.  
  
 *x*  
  
 Oggetto java.io.InputStream.  
  
 *length*  
  
 Valore **long** che indica il numero di byte.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setAsciiStream viene specificato dal metodo setAsciiStream nell'interfaccia java.sql.PreparedStatement.  
  
 Se la lunghezza del flusso è diversa da quanto specificato nel parametro *length*, il driver JDBC genera un'eccezione al momento dell'aggiornamento o dell'inserimento della riga.  
  
 Se la lunghezza del flusso è sconosciuta, il parametro *length* può essere impostato su -1 a indicare che il driver deve accettare il flusso indipendentemente dalla lunghezza. Con sqljdbc4.jar, è consigliabile usare il [metodo setAsciiStream &#40;int, java.io.InputStream&#41;](../../../connect/jdbc/reference/setasciistream-method-int-java-io-inputstream.md) di JDBC 40 se nell'applicazione è richiesto l'aggiornamento della colonna da un flusso la cui lunghezza è sconosciuta.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setAsciiStream &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setasciistream-method-sqlserverpreparedstatement.md)   
 [Membri di SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
