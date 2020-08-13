---
title: Proprietà ruolo utente (Management Studio) | Microsoft Docs
description: Informazioni sulla pagina Proprietà ruolo utente in SQL Server Management Studio in cui è possibile visualizzare le attività di definizione di ruolo a livello di elemento, modificare l'elenco di attività o modificare una descrizione di ruolo.
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.userroleproperties.f1
ms.assetid: c8b22236-a8b1-4e15-b1ff-4e1909b602d3
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 15e72e12f36753c86010a487e33ba4170c4d91c5
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2020
ms.locfileid: "86918927"
---
# <a name="user-role-properties-management-studio"></a>Proprietà ruolo utente (Management Studio)
  Questa pagina consente di visualizzare le attività incluse in una definizione di ruolo a livello di elemento. La pagina consente inoltre di modificare l'elenco di attività o una descrizione di ruolo.  
  
 Una definizione di ruolo a livello di elemento è una raccolta denominata di attività che possono essere eseguite dagli utenti in relazione a un elemento specifico, ovvero una cartella, un report, una risorsa o un'origine dati condivisa. Le definizioni di ruolo vengono assegnate a un utente o a un gruppo per creare un'assegnazione di ruolo in Gestione report. Le attività incluse nella definizione di ruolo indicano le operazioni consentite per un utente o un gruppo.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Reporting Services include varie definizioni di ruolo a livello di elemento predefinite, pronte per l'utilizzo. È possibile modificare le definizioni di ruolo modificando l'elenco di attività di ogni definizione. Le modifiche apportate a una definizione di ruolo vengono propagate a tutte le assegnazioni di ruolo che includono tale definizione.  
  
> [!NOTE]  
>  Le assegnazioni di ruolo a livello di utente vengono utilizzate solo in un server di report in esecuzione in modalità nativa. Se il server di report è configurato per l'integrazione con SharePoint, in questa pagina vengono visualizzate informazioni di sola lettura sui ruoli e sui livelli di autorizzazione definiti nel sito di SharePoint.  
  
## <a name="options"></a>Opzioni  
 **Nome**  
 Consente di specificare il nome della definizione di ruolo.  
  
 **Descrizione**  
 Consente di visualizzare una descrizione della definizione di ruolo. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]questa descrizione viene visualizzata solo in questa pagina. In Gestione report questa descrizione aiuta gli utenti a stabilire se utilizzare il ruolo in un'assegnazione di ruolo.  
  
 **Attività**  
 Consente di visualizzare l'elenco di tutte le attività a livello di elemento che possono essere selezionate per la definizione di ruolo. È possibile aggiungere o rimuovere elementi dall'elenco di attività predefinite per specificare il modo in cui gli utenti accedono a un determinato elemento tramite questo ruolo. Non è possibile creare nuove attività, né modificare quelle esistenti. L'elenco di attività di una definizione di ruolo viene visualizzato solo in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Descrizione dell'attività**  
 Offre informazioni su ogni attività. Non è possibile modificare le descrizioni delle attività.  
  
## <a name="see-also"></a>Vedere anche  
 [Attività a livello di elemento](../../reporting-services/security/tasks-and-permissions-item-level-tasks.md)   
 [Definizioni di ruolo](../../reporting-services/security/role-definitions.md)   
 [Guida sensibile al contesto del server di report in Management Studio](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [Attività e autorizzazioni](../../reporting-services/security/tasks-and-permissions.md)   
 [Predefined Roles](../../reporting-services/security/role-definitions-predefined-roles.md)  
  
  
