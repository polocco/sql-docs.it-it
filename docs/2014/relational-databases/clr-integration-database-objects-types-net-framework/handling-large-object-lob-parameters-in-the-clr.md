---
title: Gestione dei parametri di Large Object (LOB) in CLR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- large data, CLR integration
- LOB data [SQL Server], CLR integration
- SqlBytes data type
- SqlChars data type
ms.assetid: d07956f6-9543-4476-9426-536f95991150
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 09797eac229a4b3b92f94a60b6e1c06c9ec12f08
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62919497"
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a>Gestione di parametri di tipo LOB (Large Object) in CLR
  Utilizzare `SqlBytes` e `SqlChars` per passare rispettivamente parametri LOB di tipo binario (`varbinary(max)`) e parametri LOB di tipo carattere (`nvarchar(max)`). Questi tipi consentono di eseguire il flusso dei valori LOB dal database alla routine CLR (Common Language Runtime) anziché copiare l'intero valore nello spazio gestito. `SqlBinary` e `SqlString` devono essere utilizzati solo per i piccoli valori di stringa binari e di carattere.  
  
## <a name="see-also"></a>Vedi anche  
 [Tipi di dati di SQL Server in .NET Framework](sql-server-data-types-in-the-net-framework.md)  
  
  
