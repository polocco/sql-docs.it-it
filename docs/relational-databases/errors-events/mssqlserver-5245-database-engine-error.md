---
description: MSSQLSERVER_5245
title: MSSQLSERVER_5245 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5245 (Database Engine error)
ms.assetid: 6005c9ec-ccdd-4def-9eb4-37cdb599ddb3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 67ae97cdfc3e6db07870844e418eacc07c4c857f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471009"
---
# <a name="mssqlserver_5245"></a>MSSQLSERVER_5245
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Dettagli  
  
| Attributo | valore |  
| :-------- | :---- |  
|Nome prodotto|SQL Server|  
|ID evento|5245|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC4_TABLE_LOCK_TIMEOUT_EXCEEDED|  
|Testo del messaggio|ID oggetto O_ID (oggetto 'NAME'): DBCC non è in grado di ottenere un blocco sull'oggetto. Timeout della richiesta di blocco. L'oggetto è stato ignorato e non verrà elaborato.|  
  
## <a name="explanation"></a>Spiegazione  
Si è verificato un timeout di blocco mentre DBCC era in attesa di un blocco a livello di tabella per l'oggetto specificato.  
  
## <a name="user-action"></a>Azione dell'utente  
Eseguire di nuovo il comando DBCC.  
  
