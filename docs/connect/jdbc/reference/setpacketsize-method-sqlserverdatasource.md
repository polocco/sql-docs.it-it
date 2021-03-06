---
description: Metodo setPacketSize (SQLServerDataSource)
title: Metodo setPacketSize (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setPacketSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5d490edc-a223-4870-a838-784952497e5f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7c1005f1acb2572bbdf118d16c045fe91bd8ac79
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458505"
---
# <a name="setpacketsize-method-sqlserverdatasource"></a>Metodo setPacketSize (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta le dimensioni, specificate in byte, del pacchetto di rete corrente usato per comunicare con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setPacketSize(int packetSize)  
```  
  
#### <a name="parameters"></a>Parametri  
 *packetSize*  
  
 Valore **int** contenente la dimensione del pacchetto di rete.  
  
## <a name="remarks"></a>Osservazioni  
 L'intervallo di valori accettabili di questa proprietà è [-1 | 0 | 512..32767]. Se questa proprietà è impostata su un valore che non rientra nell'intervallo valido, viene generata un'eccezione.  
  
 L'applicazione potrebbe voler impostare la proprietà packetSize durante la connessione con crittografia Transport Layer Security (TLS), precedentemente nota come Secure Sockets Layer (SSL). Le dimensioni del pacchetto vengono negoziate con il server da [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Se la proprietà di crittografia è impostata su "**true**" e le dimensioni del pacchetto negoziate sono superiori alle dimensioni dei record TLS del provider di sicurezza predefinito di JVM (Java Virtual Machine), il driver genererà un errore e terminerà la connessione.  
  
 È anche possibile che l'applicazione voglia impostare la proprietà packetSize senza richiedere la crittografia TLS. In questo caso, se il server richiede il supporto della crittografia TLS da parte del client, il driver verificherà le dimensioni dei record TLS del provider di sicurezza predefinito di JVM. Se le dimensioni della proprietà packetSize sono superiori rispetto alle dimensioni dei record TLS del provider di sicurezza predefinito di JVM, il driver genererà un errore e terminerà la connessione.  
  
 Per altre informazioni sull'uso di TLS, vedere [Uso della crittografia](../../../connect/jdbc/using-ssl-encryption.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
