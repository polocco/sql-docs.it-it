---
description: MSSQLSERVER_41399
title: MSSQLSERVER_41399 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41399 (Database Engine error)
ms.assetid: 5e5acb07-16ca-4329-8210-cd2bab0c904f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2265ac2c7b83dde303e25f68d3a3c49cc35bbfa3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471074"
---
# <a name="mssqlserver_41399"></a>MSSQLSERVER_41399
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Dettagli  
  
| Attributo | valore |  
| :-------- | :---- |  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|41399|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|MAX_SORT_ROW_WIDTH_EXCEEDED|  
|Testo del messaggio|L'operazione di ordinamento è troppo complessa. Per ulteriori informazioni, vedere la documentazione online di SQL Server.|  
  
## <a name="explanation"></a>Spiegazione  
L'ordinamento del risultato di operazioni di join e di aggregazione aumenta la complessità dell'operazione di ordinamento incrementando le dimensioni della riga nel buffer di ordinamento. Questo errore indica che le dimensioni della riga sono maggiori delle dimensioni massime supportate dall'operatore di ordinamento nelle stored procedure compilate in modo nativo. Notare che le dimensioni di una riga nel buffer di ordinamento sono determinate unicamente dal numero di join e dal numero e dal tipo di funzioni di aggregazione. Le dimensioni delle righe nelle tabelle di base non influisce sulle dimensioni della riga nel buffer.  
  
## <a name="user-action"></a>Azione dell'utente  
Ridurre la complessità della query rimuovendo le funzioni di aggregazione o i join.  
  
## <a name="see-also"></a>Vedere anche  
[OLTP in memoria &#40;ottimizzazione per la memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
