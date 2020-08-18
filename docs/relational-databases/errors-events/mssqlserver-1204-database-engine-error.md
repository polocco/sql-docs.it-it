---
description: MSSQLSERVER_1204
title: MSSQLSERVER_1204 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1204 (Database Engine error)
ms.assetid: de6ece78-79de-484d-9224-ca0f7645815f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 04e9802e4ca7df64fd469ef2ca8151cbe160c182
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88336367"
---
# <a name="mssqlserver_1204"></a>MSSQLSERVER_1204
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Dettagli  
  
| Attributo | valore |  
| :-------- | :---- |  
|Nome prodotto|SQL Server|  
|ID evento|1204|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|LK_OUTOF|  
|Testo del messaggio|In questo momento l'istanza del Motore di database di SQL Server non è in grado di ottenere una risorsa LOCK. Eseguire nuovamente l'istruzione quando è presente un minor numero di utenti attivi. Chiedere all'amministratore del database di controllare la configurazione di memoria e di blocco per l'istanza o di verificare la presenza di transazioni con esecuzione prolungata.|  
  
## <a name="explanation"></a>Spiegazione  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è in grado di ottenere una risorsa di blocco. L'errore può essere causato da uno dei motivi seguenti:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è in grado di allocare ulteriore memoria dal sistema operativo perché questa è già usata da altri processi oppure perché è stata configurata l'opzione **Max Server Memory** per il server in uso.  
  
-   In Gestione blocchi non viene utilizzato più del 60 percento della memoria disponibile per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="user-action"></a>Azione dell'utente  
Se si sospetta che il motivo dell'errore sia l'impossibilità di SQL Server di allocare memoria sufficiente, procedere come segue:  
  
-   Se le risorse vengono utilizzate da altre applicazioni oltre a SQL Server, provare ad arrestarne l'esecuzione o a eseguirle in un server distinto. In questo modo verrà rilasciata memoria da altri processi di SQL Server.  
  
-   Se è stata configurata l'opzione max server memory, aumentarne il valore impostato.  
  
Se si sospetta che in Gestione blocchi sia stata utilizzata la massima quantità di memoria disponibile, individuare la transazione che mantiene la maggior parte dei blocchi e interromperla. Lo script seguente consente di individuare la transazione che presenta più blocchi:  
  
```  
SELECT request_session_id, COUNT (*) num_locks  
FROM sys.dm_tran_locks  
GROUP BY request_session_id   
ORDER BY count (*) DESC  
```  
  
Individuare l'ID di sessione più elevato e interrompere la transazione corrispondente tramite il comando KILL.  
  
