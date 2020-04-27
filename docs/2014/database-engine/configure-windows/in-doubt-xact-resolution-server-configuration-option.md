---
title: Opzione di configurazione del server in-doubt xact resolution | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- distributed transactions [SQL Server], unresolved transactions
- unresolved transactions
- in-doubt xact resolution option
ms.assetid: 3426fd32-cad2-4f2f-8ca9-e0296cc12703
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 648f142eb80607412e13151098418c22e45f04bd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62781936"
---
# <a name="in-doubt-xact-resolution-server-configuration-option"></a>Opzione di configurazione del server in-doubt xact resolution
  L'opzione **in-doubt xact resolution** consente di controllare il risultato predefinito delle transazioni che non possono essere risolte da [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC). L'impossibilità di risolvere le transazioni potrebbe essere dovuta al tempo di inattività di MS DTC oppure a un risultato sconosciuto della transazione al momento del recupero.  
  
 Nella tabella seguente vengono descritti i possibili valori del risultato della risoluzione di una transazione in dubbio.  
  
|Valore risultato|Descrizione|  
|-------------------|-----------------|  
|0|No presumption (nessuna presupposizione). L'operazione di recupero ha esito negativo se tramite MS DTC non è possibile risolvere alcuna transazione in dubbio.|  
|1|Presume commit (presupposizione commit). Si presuppone il commit di qualsiasi transazione in dubbio MS DTC.|  
|2|Presume abort (presupposizione interruzione). Si presuppone l'interruzione di qualsiasi transazione in dubbio MS DTC.|  
  
 Per ridurre al minimo la possibilità di tempi di inattività prolungati, un amministratore può configurare questa opzione per presupporre il commit o l'interruzione, come illustrato nell'esempio seguente.  
  
```  
sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'in-doubt xact resolution', 2 -- presume abort  
GO  
RECONFIGURE  
GO  
sp_configure 'show advanced options', 0  
GO  
RECONFIGURE  
GO  
  
```  
  
 In alternativa, è possibile lasciare l'opzione predefinita, no presumption, e consentire il verificarsi dell'errore dell'operazione di recupero per essere a conoscenza di un errore DTC, come illustrato nell'esempio seguente.  
  
```  
sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'in-doubt xact resolution', 1 -- presume commit  
GO  
reconfigure  
GO  
ALTER DATABASE pubs SET ONLINE -- run recovery again  
GO  
sp_configure 'in-doubt xact resolution', 0 -- back to no assumptions  
GO  
sp_configure 'show advanced options', 0  
GO  
RECONFIGURE  
GO  
  
```  
  
 **in-doubt xact resolution** è un'opzione avanzata. Se si usa la stored procedure di sistema **sp_configure** per modificare l'impostazione, è possibile modificare **in-doubt xact resolution** solo quando il valore di **show advanced options** è impostato su 1. L'impostazione diventa effettiva immediatamente e non richiede il riavvio del server.  
  
> [!NOTE]  
>  Impostando questa opzione in modo coerente in tutte le istanze di [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] coinvolte in qualsiasi transazione distribuita, è possibile evitare inconsistenze dei dati.  
  
## <a name="see-also"></a>Vedere anche  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Opzioni di configurazione del server &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
