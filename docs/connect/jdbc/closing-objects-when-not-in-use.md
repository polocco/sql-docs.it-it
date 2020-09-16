---
description: Chiusura di oggetti quando non sono in uso
title: Chiusura di oggetti quando non sono in uso | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ce8f9b35-c761-4b0c-9a46-985eef2c2e0b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0c8e1242f5090e347dd3dd61d42fedd3698613cb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438453"
---
# <a name="closing-objects-when-not-in-use"></a>Chiusura di oggetti quando non sono in uso
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Quando si usano oggetti di [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], in particolare [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) o uno degli oggetti Statement come [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) o [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), è necessario chiuderli in modo esplicito usando i rispettivi metodi close quando non sono più necessari. In questo modo, è possibile migliorare le prestazioni liberando le risorse del driver e del server appena possibile, anziché attendere che questa operazione venga eseguita dal Garbage Collector di Java Virtual Machine.  
  
 La chiusura degli oggetti è particolarmente importante per garantire una buona concorrenza nel server quando si utilizzano blocchi di scorrimento. I blocchi di scorrimento nel buffer di recupero in cui è stato effettuato l'ultimo accesso vengono mantenuti attivi fino a quando non viene chiuso il set di risultati. Analogamente, gli handle di istruzione preparati vengono mantenuti fino a quando l'istruzione non viene chiusa. Se si sta riutilizzando una connessione per più istruzioni, chiudendo le istruzioni prima che escano dall'ambito si consente al server di eseguire prima la pulizia degli handle preparati.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso del driver JDBC per il miglioramento di prestazioni e affidabilità](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
