---
description: MSSQLSERVER_32044
title: MSSQLSERVER_32044 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 32044 (Database Engine error)
ms.assetid: f2d073be-d9a1-4837-8a38-028d3e3403bd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 675c50fc98f49ea0a6d8a05ce85e6518219eb59e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476252"
---
# <a name="mssqlserver_32044"></a>MSSQLSERVER_32044
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Dettagli  
  
| Attributo | valore |  
| :-------- | :---- |  
|Nome prodotto|SQL Server|  
|ID evento|32044|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SQLErrorNum32044|  
|Testo del messaggio|Generato avviso relativo a un overhead di commit del mirror. Il valore corrente di '%d' è maggiore della soglia '%d'.|  
  
## <a name="explanation"></a>Spiegazione  
Questo evento di mirroring del database viene generato nell'istanza del server principale per indicare che il tempo di attesa del commit di aggregazione ha raggiunto o superato un valore soglia specificato dall'utente a causa del mirroring del database. L'intervallo di attesa viene ottenuto moltiplicando il numero di transazioni per la durata di ogni transazione. Ad esempio i casi seguenti richiedono entrambi 1000 millisecondi di tempo di attesa: 1000 transazioni * 1 millisecondo e 1 transazione \* 1000 millisecondi. L'aumento del tempo di attesa del commit può dipendere da un picco nel numero di transazioni, da ritardi nell'invio del log o da ritardi nello scaricamento del log nell'istanza del server mirror.  
  
La quantità dell'overhead di commit del mirror è una metrica delle prestazioni che consente di valutare l'impatto sulle prestazioni correnti del funzionamento sincrono. Questa metrica è rilevante solo nella modalità a sicurezza elevata. Poiché la modalità a sicurezza elevata è sincrona, prima di eseguire il commit della transazione dopo aver inviato un record di log all'istanza del server mirror, l'istanza del server principale attende la conferma della scrittura del record di log sul disco. Il record di log rimane sul disco dell'istanza del server mirror in attesa di essere ripristinato nel database mirror.  
  
## <a name="user-action"></a>Azione dell'utente  
Controllare il carico delle istanze del server principale e del server mirror e la connessione di rete tra i sistemi per determinare la causa del problema.  
  
## <a name="see-also"></a>Vedere anche  
[Mirroring del database &#40;SQL Server&#41;](~/database-engine/database-mirroring/database-mirroring-sql-server.md)  
[Usare valori di soglia avvisi e avvisi sulle metriche delle prestazioni di mirroring &#40;SQL Server&#41;](~/database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
