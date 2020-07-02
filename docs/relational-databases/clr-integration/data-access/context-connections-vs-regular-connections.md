---
title: Confronto tra normali e connessioni di contesto | Microsoft Docs
description: In SQL Server, a volte è necessario usare connessioni regolari per le istruzioni Transact-SQL, ma le connessioni di contesto offrono vantaggi in merito alle prestazioni e all'utilizzo delle risorse.
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: a1dead02-be88-4b16-8cb2-db1284856764
author: rothja
ms.author: jroth
ms.openlocfilehash: 6417a0121a7e290d711690fb0150fdbe908827dd
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85637519"
---
# <a name="context-connections-vs-regular-connections"></a>Connessioni di contesto e connessioni regolari
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  Se si esegue una connessione a un server remoto, utilizzare sempre connessioni normali anziché connessioni di contesto. Se è necessario connettersi allo stesso server in cui è in esecuzione la stored procedure o la funzione, utilizzare la connessione di contesto nella maggior parte dei casi. Questa connessione offre vantaggi quali l'esecuzione nello stesso spazio della transazione e la non necessità di eseguire una nuova autenticazione.  
  
 L'utilizzo della connessione di contesto, inoltre, consente in genere prestazioni migliori e un minore utilizzo delle risorse. La connessione del contesto è una connessione solo in-process, quindi è in grado di contattare il server "direttamente" ignorando il protocollo di rete e i livelli di trasporto per inviare istruzioni Transact-SQL e ricevere risultati. Viene ignorato anche il processo di autenticazione. Nella figura seguente vengono illustrati i componenti principali del provider gestito **SqlClient** , nonché il modo in cui i diversi componenti interagiscono tra loro quando si utilizza una connessione normale e quando si utilizza la connessione di contesto.  
  
 ![Percorsi del codice di una connessione del contesto e una connessione regolare](../../../relational-databases/clr-integration/data-access/media/clrintdataaccess.gif "Percorsi del codice di una connessione del contesto e una connessione regolare")  
  
 Poiché la connessione di contesto segue un percorso di codice più corto e interessa un numero minore di componenti, è probabile che le richieste e i risultati vengano trasmessi al e dal server più rapidamente che in una connessione normale. I tempi di esecuzione delle query nel server sono uguali per le connessioni normali e di contesto.  
  
 In alcuni casi, potrebbe essere necessario aprire una connessione normale separata allo stesso server. Esistono, ad esempio, alcune restrizioni sull'utilizzo della connessione di contesto, descritte in [restrizioni sulle connessioni normali e di contesto](../../../relational-databases/clr-integration/data-access/context-connections-and-regular-connections-restrictions.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione di contesto](../../../relational-databases/clr-integration/data-access/context-connection.md)  
  
  
