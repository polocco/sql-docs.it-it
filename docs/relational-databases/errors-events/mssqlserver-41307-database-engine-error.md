---
description: MSSQLSERVER_41307
title: MSSQLSERVER_41307 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41307 (Database Engine error)
ms.assetid: 56f56410-b07d-4379-b01c-702c95761070
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6a19c447c70769c6be45b5a69f025f63c08fc17e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88428723"
---
# <a name="mssqlserver_41307"></a>MSSQLSERVER_41307
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Dettagli  
  
| Attributo | valore |  
| :-------- | :---- |  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|41307|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|HK_HEKATON_ROW_LIMIT|  
|Testo del messaggio|Il limite di dimensioni riga di *numero* byte per le tabelle con ottimizzazione per la memoria è stato superato. Semplificare la definizione di tabella.|  
  
## <a name="explanation"></a>Spiegazione  
Il limite di dimensioni riga per le tabelle con ottimizzazione per la memoria è di 8.060 byte. Per altre informazioni, vedere [Dimensioni di tabelle e righe per le tabelle con ottimizzazione per la memoria](~/relational-databases/in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md). Per altre informazioni, vedere [OLTP in memoria &#40;ottimizzazione in memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Vedere anche  
[OLTP in memoria &#40;ottimizzazione per la memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
