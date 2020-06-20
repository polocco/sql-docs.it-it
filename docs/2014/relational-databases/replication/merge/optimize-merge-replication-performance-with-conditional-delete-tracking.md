---
title: Ottimizzare le prestazioni della replica di tipo merge con il rilevamento condizionale delle eliminazioni | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- conditional delete tracking [SQL Server replication]
- merge replication [SQL Server replication], conditional delete tracking
- articles [SQL Server replication], conditional delete tracking
ms.assetid: 58f120a3-ea3a-4e97-93f0-0eb4e580ecf2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a564dc4bcabc46689fbf1a521a9ecb1209654594
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85010503"
---
# <a name="optimize-merge-replication-performance-with-conditional-delete-tracking"></a>Ottimizzazione delle prestazioni della replica di tipo merge con il rilevamento condizionale delle eliminazioni
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 Con la replica di tipo merge è possibile specificare che le eliminazioni per uno o più articoli non devono essere rilevate dai trigger di replica e dalle tabelle di sistema. Se si specifica questa opzione per un articolo, le eliminazioni non vengono rilevate o replicate dal server di pubblicazione o da qualsiasi Sottoscrittore. Questa opzione è disponibile per il supporto di numerosi scenari applicativi e per offrire l'ottimizzazione delle prestazioni, nei casi in cui la replica delle eliminazioni non è necessaria o desiderata. Il miglioramento delle prestazioni avviene per tre motivi: non vengono archiviati i metadati delle eliminazioni, le eliminazioni non vengono enumerate durante la sincronizzazione e, infine, non vengono replicate nel Sottoscrittore e applicate allo stesso.  
  
> [!NOTE]  
>  Per utilizzare questo tipo di articoli è necessario che il livello di compatibilità della pubblicazione sia impostato almeno su 90RTM.  
  
 Questa opzione può essere specificata alla creazione della pubblicazione oppure attivata e disattivata se un'applicazione richiede la replica di alcune eliminazioni e non di altre, ad esempio eliminazioni batch. Gli esempi seguenti illustrano le modalità di utilizzo di questa opzione in un'applicazione.  
  
-   Un'applicazione per la forza vendita mobile in genere contiene tabelle come **SalesOrderHeader**, **SalesOrderDetail** e **Product**. Gli ordini vengono immessi nel Sottoscrittore e poi replicati nel server di pubblicazione, che spesso assicura i dati a un sistema di evasione degli ordini. Molti lavoratori mobili utilizzano dispositivi palmari che hanno una capacità di archiviazione limitata: quando l'ordine viene ricevuto nel server di pubblicazione, può essere eliminato nel Sottoscrittore. L'eliminazione non viene propagata al server di pubblicazione, perché l'ordine è ancora attivo nel sistema.  
  
     In questo scenario, le eliminazioni non verrebbero rilevate per le tabelle **SalesOrderHeader** e **SalesOrderDetail** . Verrebbero invece rilevate per la tabella **Product** perché se un prodotto viene eliminato nel server di pubblicazione l'eliminazione deve essere inviata al Sottoscrittore per mantenere aggiornato l'elenco dei prodotti.  
  
-   Un'applicazione potrebbe archiviare i dati storici in una tabella come **TransactionHistory**, da cui vengono periodicamente eliminati i record più vecchi di un anno. La tabella potrebbe essere filtrata in modo che i Sottoscrittori ricevano solo i dati delle transazioni del mese corrente. Le eliminazioni batch mensili del server di pubblicazione, con cui vengono eliminati i dati più vecchi, non interessano i Sottoscrittori, ma verrebbero comunque rilevate ed enumerate per impostazione predefinita.  
  
     In questo scenario, prima che abbia luogo l'elaborazione batch, sarebbe possibile arrestare l'attività del sistema e disabilitare il rilevamento delle eliminazioni dall'applicazione. Al termine dell'elaborazione, sarebbe possibile riabilitare la rilevazione.  
  
> [!IMPORTANT]  
>  Se nel server di pubblicazione prosegue l'attività, è necessario verificare che le eliminazioni che dovrebbero essere propagate ai Sottoscrittori non abbiano luogo mentre il rilevamento delle eliminazioni è disabilitato.  
  
 **Per specificare di non rilevare le eliminazioni**  
  
-   Programmazione [!INCLUDE[tsql](../../../includes/tsql-md.md)] della replica: [Disattivare del rilevamento delle eliminazioni per gli articoli di merge &#40;programmazione Transact-SQL della replica&#41;](..//publish/specify-merge-replication-properties.md#tracking-deletes)  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni degli articoli per la replica di tipo merge](article-options-for-merge-replication.md)   
 [Ottimizzare le prestazioni della replica di tipo merge con gli articoli di solo download](optimize-merge-replication-performance-with-download-only-articles.md)  
  
  
