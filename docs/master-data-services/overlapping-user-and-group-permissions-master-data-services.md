---
title: Autorizzazioni utenti e gruppi sovrapposte
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- users [Master Data Services], resolving permissions
- permissions [Master Data Services], user and group overlaps
- groups [Master Data Services], resolving permissions
ms.assetid: 31c3cf7d-17d4-4474-b6a7-ffcb9fc45b37
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2df45ce2a08e545bc7da11ab3f97df8aa86b0c26
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "73727941"
---
# <a name="overlapping-user-and-group-permissions-master-data-services"></a>Autorizzazioni utenti e gruppi sovrapposte (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Le autorizzazioni di un utente si basano su:  
  
-   Autorizzazioni ereditate dalle appartenenze a gruppi.  
  
-   Autorizzazioni assegnate in modo esplicito all'utente.  
  
 Se un utente è un membro di più gruppi e questi gruppi dispongono dell'accesso a [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], si applicano le regole seguenti:  
  
-   **Nega** esegue l'override di tutte le altre autorizzazioni. Se l'autorizzazione per gli oggetti è **Deny** in un gruppo, l'autorizzazione effettiva è deny.  
  
-   L'autorizzazioni di accesso è un'unione di tutte le autorizzazioni valide per un gruppo. Se l'autorizzazione per gli oggetti è **Create** da un gruppo e **Update** da altro gruppo, l'autorizzazione valida è **Create** e **Update**.  
  
 Queste regole si applicano a entrambe le schede **Modelli** e **Membri gerarchia** . Le autorizzazioni vengono risolte per ogni scheda e quindi combinate. Per altre informazioni, vedere [Modalità di determinazione delle autorizzazioni &#40;Master Data Services&#41;](../master-data-services/how-permissions-are-determined-master-data-services.md).  
  
> [!NOTE]  
>  Nell'interfaccia utente è possibile visualizzare la risoluzione delle autorizzazioni di utenti e gruppi sovrapposte. Nelle schede **Modelli** e **Membri gerarchia** è presente un elenco a discesa da cui è possibile scegliere **Valide** per visualizzare le autorizzazioni valide.  
  
## <a name="example-1"></a>Esempio 1  
 ![mds_conc_user_group_ex_1](../master-data-services/media/mds-conc-user-group-ex-1.gif "mds_conc_user_group_ex_1")  
  
 L'utente appartiene al Gruppo 1 e al Gruppo 2.  
  
 L'utente ha l'autorizzazione **Read** per l'entità Product.  
  
 Il gruppo 1 ha l'autorizzazione **Update** per l'entità Product.  
  
 Il gruppo 2 ha l'autorizzazione **Read** per l'entità Product.  
  
 Risultato: l'autorizzazione valida dell'utente è **Update** per l'entità Product.  
  
## <a name="example-2"></a>Esempio 2  
 ![mds_conc_user_group_ex_2](../master-data-services/media/mds-conc-user-group-ex-2.gif "mds_conc_user_group_ex_2")  
  
 L'utente appartiene al Gruppo 1 e al Gruppo 2.  
  
 L'utente ha l'autorizzazione **Read** per l'entità Product.  
  
 Il gruppo 1 ha l'autorizzazione **Update** per l'entità Product.  
  
 Il gruppo 2 ha l'autorizzazione **Deny** per l'entità Product.  
  
 Risultato: l'autorizzazione valida dell'utente è **Deny** per l'entità Product.  
  
## <a name="example-3"></a>Esempio 3  
 ![mds_conc_user_group_ex_3](../master-data-services/media/mds-conc-user-group-ex-3.gif "mds_conc_user_group_ex_3")  
  
 L'utente appartiene al Gruppo 1 e al Gruppo 2.  
  
 L'utente dispone dell'autorizzazione **Update** per un gruppo di membri in un nodo gerarchia.  
  
 Il gruppo 1 ha l'autorizzazione **Read** per un gruppo di membri in un nodo gerarchia.  
  
 Il gruppo 2 ha l'autorizzazione **Read** per un gruppo di membri in un nodo gerarchia.  
  
 Risultato: l'autorizzazione utente valida è **Update** per i membri.  
  
## <a name="see-also"></a>Vedere anche  
 [Modalità di determinazione delle autorizzazioni &#40;Master Data Services&#41;](../master-data-services/how-permissions-are-determined-master-data-services.md)   
 [Autorizzazioni per modelli e membri sovrapposte &#40;Master Data Services&#41;](../master-data-services/overlapping-model-and-member-permissions-master-data-services.md)  
  
  
