---
description: MSSQLSERVER_10533
title: MSSQLSERVER_10533 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10533 (Database Engine error)
ms.assetid: cc2fbdab-7b90-415f-a1f9-066824344283
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4ab2b32fab50f3a335d1d89fa76f0a3e26467e5d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88338897"
---
# <a name="mssqlserver_10533"></a>MSSQLSERVER_10533
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Dettagli  
  
| Attributo | valore |  
| :-------- | :---- |  
|Nome prodotto|SQL Server|  
|ID evento|10533|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|PG_NAME_TOO_BIG|  
|Testo del messaggio|Impossibile creare la guida di piano '%.*ls' perché il nome della guida di piano supera la lunghezza massima consentita di 124 caratteri. Specificare un nome che contiene meno di 125 caratteri.|  
  
## <a name="explanation"></a>Spiegazione  
Il nome della guida di piano supera la lunghezza massima consentita di 124 caratteri.  
  
## <a name="user-action"></a>Azione dell'utente  
Specificare un nome che contiene meno di 125 caratteri.  
  
## <a name="see-also"></a>Vedere anche  
[Guide di piano](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
