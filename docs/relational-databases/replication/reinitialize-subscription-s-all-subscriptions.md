---
title: Reinizializza sottoscrizioni - Tutte le sottoscrizioni | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.reinit.all.f1
helpviewer_keywords:
- Reinitialize Subscription(s) dialog box
ms.assetid: e1122018-9f74-43e3-8489-7eae33ff23d9
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 9da983b0f59625c6bd2404512e99d4f0928bff01
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85767697"
---
# <a name="reinitialize-subscriptions---all-subscriptions"></a>Reinizializza sottoscrizioni - Tutte le sottoscrizioni
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  La finestra di dialogo **Reinizializza sottoscrizioni** consente di contrassegnare per la reinizializzazione tutte le sottoscrizioni di una pubblicazione. La reinizializzazione include l'applicazione di uno snapshot a ogni Sottoscrittore, eseguita dall'agente di distribuzione per le sottoscrizioni di pubblicazioni transazionali e dall'agente di merge per le sottoscrizioni a pubblicazioni di tipo merge.  
  
## <a name="options"></a>Opzioni  
 **Usa lo snapshot corrente**  
 Selezionare questa opzione per applicare lo snapshot corrente a ogni Sottoscrittore alla successiva esecuzione dell'agente di distribuzione o dell'agente di merge per la sottoscrizione. Se non sono disponibili snapshot validi, questa opzione non può essere selezionata.  
  
 **Usa un nuovo snapshot**  
 Selezionare questa opzione per reinizializzare tutte le sottoscrizioni con un nuovo snapshot. Lo snapshot può essere applicato a ogni Sottoscrittore solo dopo essere stato generato dall'agente snapshot. Se l'agente snapshot è impostato per l'esecuzione in base a una pianificazione, le sottoscrizioni non verranno reinizializzate fino al completamento della successiva esecuzione pianificata dell'agente snapshot.  
  
 Per avviare l'agente snapshot immediatamente, selezionare **Genera il nuovo snapshot ora** .  
  
 **Carica le modifiche non sincronizzate prima della reinizializzazione**  
 Solo per la replica di tipo merge. Selezionare questa opzione per caricare le modifiche in sospeso dai database di sottoscrizione prima che i dati nei Sottoscrittori vengano sovrascritti con uno snapshot.  
  
 Se si aggiunge, elimina o modifica un filtro con parametri, le modifiche in sospeso nel Sottoscrittore non possono essere caricate nel server di pubblicazione durante la reinizializzazione. Per caricare le modifiche in sospeso, sincronizzare tutte le sottoscrizioni prima di modificare il filtro.  
  
 **Contrassegna per la reinizializzazione**  
 Selezionare questa opzione per contrassegnare ogni sottoscrizione per la reinizializzazione. Dopo aver verificato la disponibilità di uno snapshot valido, alla successiva esecuzione dell'agente di distribuzione o dell'agente di merge per la sottoscrizione viene applicato lo snapshot nel Sottoscrittore.  
  
## <a name="see-also"></a>Vedere anche  
 [Reinizializzare le sottoscrizioni](../../relational-databases/replication/reinitialize-subscriptions.md)  
  
  
