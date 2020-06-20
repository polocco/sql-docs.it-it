---
title: Eliminare un gruppo di carico di lavoro | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- workload groups [SQL Server], delete
- Resource Governor, workload group delete
ms.assetid: d5902c46-5c28-4ac1-8b56-cb4ca2b072d0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 801a731db6c5b31bc479d1a3f6079c45ad9a7c04
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063612"
---
# <a name="delete-a-workload-group"></a>Eliminare un gruppo di carico di lavoro
  È possibile eliminare un gruppo di carico di lavoro o un pool di risorse utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o Transact-SQL.  
  
-   **Prima di iniziare:**  [Limitazioni e restrizioni](#LimitationsRestrictions), [Autorizzazioni](#Permissions)  
  
-   **Per eliminare un gruppo del carico di lavoro usando:**  [Esplora oggetti](#DelWGObjEx), [le proprietà di Resource Governor](#DelWGRGProp), [Transact-SQL](#DelWGTSQL)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Prima di iniziare  
 Non è possibile eliminare un gruppo di carico di lavoro contenente sessioni attive.  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Limitazioni e restrizioni  
 Se in un gruppo di carico di lavoro sono contenute sessioni attive, non sarà possibile eliminare o spostare tale gruppo in un pool di risorse diverso quando viene chiamata l'istruzione ALTER RESOURCE GOVERNOR RECONFIGURE per l'applicazione della modifica. Per evitare il problema, eseguire una delle azioni seguenti:  
  
-   Attendere la disconnessione di tutte le sessioni relative al gruppo interessato, quindi eseguire nuovamente l'istruzione ALTER RESOURCE GOVERNOR RECONFIGURE.  
  
-   Arrestare in modo esplicito le sessioni del gruppo interessato utilizzando il comando KILL, quindi eseguire nuovamente l'istruzione ALTER RESOURCE GOVERNOR RECONFIGURE. Se si decide di non arrestare in modo esplicito le sessioni dopo aver utilizzato **Elimina** ma prima di arrestare le sessioni attive, ricreare il gruppo utilizzando il nome originale e spostare il gruppo nel pool di risorse originale.  
  
-   Riavviare il server. Una volta completato il processo di riavvio, il gruppo eliminato non verrà creato e in un gruppo spostato verrà utilizzata la nuova assegnazione del pool di risorse.  
  
###  <a name="permissions"></a><a name="Permissions"></a> Autorizzazioni  
 Per eliminare un gruppo di carico di lavoro è necessaria l'autorizzazione CONTROL SERVER.  
  
##  <a name="delete-a-workload-group-using-object-explorer"></a><a name="DelWGObjEx"></a> Eliminare un gruppo di carico di lavoro utilizzando Esplora oggetti  
 **Per eliminare un gruppo di carico di lavoro utilizzando Esplora oggetti**  
  
1.  In[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]aprire Esplora oggetti ed espandere in modo ricorsivo il nodo **Gestione** fino a **Pool di risorse**incluso.  
  
2.  Espandere in modo ricorsivo **Pool di risorse** fino al nodo **Gruppi del carico di lavoro** incluso nel pool di risorse in cui è contenuto il gruppo di carico di lavoro da eliminare.  
  
3.  Fare clic con il pulsante destro del mouse sul gruppo di carico di lavoro e scegliere **Elimina**.  
  
4.  Nella finestra **Elimina oggetto** il gruppo di carico di lavoro viene indicato nell'elenco **Oggetto da eliminare** . Per eliminare il gruppo di carico di lavoro, fare clic su **OK**.  
  
##  <a name="delete-a-workload-group-using-resource-governor-properties"></a><a name="DelWGRGProp"></a> Eliminare un gruppo di carico di lavoro utilizzando Proprietà di Resource Governor  
 **Per eliminare un gruppo di carico di lavoro utilizzando la pagina Proprietà di Resource Governor**  
  
1.  In Esplora oggetti espandere in modo ricorsivo il nodo **Gestione** fino a **Pool di risorse**compreso.  
  
2.  Fare clic con il pulsante destro del mouse sul pool di risorse in cui è contenuto il gruppo di carico di lavoro da eliminare, quindi fare clic su **Proprietà**. Viene aperta la pagina **Proprietà di Resource Governor** .  
  
3.  Nella finestra **Gruppi del carico di lavoro per il pool di risorse** fare clic sulla riga del gruppo di carico di lavoro da eliminare, fare clic con il pulsante destro del mouse sulla freccia a destra sul lato sinistro della riga, quindi scegliere **Elimina**.  
  
4.  Per eliminare il gruppo di carico di lavoro, fare clic su **OK**.  
  
##  <a name="delete-a-workload-group-using-transact-sql"></a><a name="DelWGTSQL"></a> Eliminare un gruppo di carico di lavoro utilizzando Transact-SQL  
 **Per eliminare un gruppo di carico di lavoro utilizzando Transact-SQL**  
  
1.  Eseguire l'istruzione `DROP WORKLOAD GROUP` specificando il nome del gruppo di carico di lavoro da eliminare.  
  
2.  Prima di eseguire l'istruzione `ALTER RESOURCE GOVERNOR RECONFIGURE`, verificare che non siano presenti richieste attive nel gruppo di carico di lavoro che viene eliminato. Se sono presenti richieste attive, l'esecuzione dell'istruzione `ALTER RESOURCE GOVERNOR` non viene completata. Per evitare il problema, effettuare una delle azioni seguenti:  
  
    -   Attendere la disconnessione di tutte le sessioni dal gruppo del carico di lavoro.  
  
    -   Arrestare in modo esplicito le sessioni nel gruppo di carico di lavoro utilizzando il comando `KILL`.  
  
    -   Riavviare il server. Il gruppo di carico di lavoro non verrà ricreato.  
  
    -   In uno scenario in cui viene eseguita l'istruzione `DROP WORKLOAD GROUP` ma si decide di non arrestare in modo esplicito le sessioni per applicare la modifica, è possibile ricreare il gruppo utilizzando lo stesso nome presente prima dell'esecuzione dell'istruzione DROP, quindi spostare il gruppo nel pool di risorse originale.  
  
3.  Eseguire l' `ALTER RESOURCE GOVERNOR RECONFIGURE` istruzione.  
  
### <a name="example-transact-sql"></a>Esempio (Transact-SQL)  
 Nell'esempio seguente viene eliminato un gruppo di carico di lavoro denominato `groupAdhoc`.  
  
```  
DROP WORKLOAD GROUP groupAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Resource Governor](resource-governor.md)   
 [Creare un pool di risorse](create-a-resource-pool.md)   
 [Creare un gruppo di carico di lavoro](create-a-workload-group.md)   
 [Eliminare un pool di risorse](delete-a-resource-pool.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-workload-group-transact-sql)   
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-resource-pool-transact-sql)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
