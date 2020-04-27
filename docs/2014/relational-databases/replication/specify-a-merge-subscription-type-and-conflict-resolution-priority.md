---
title: Specificare una sottoscrizione di tipo merge e la priorità per la risoluzione dei conflitti (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], merge subscription resolvers
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 2b828d83-2341-4924-b92a-4f81a22246c0
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0ef72b3c36e1cfc7d59792056e080d1cbf2d5c55
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "63156356"
---
# <a name="specify-a-merge-subscription-type-and-conflict-resolution-priority-sql-server-management-studio"></a>Impostazione di una sottoscrizione di tipo merge e della priorità per la risoluzione dei conflitti (SQL Server Management Studio)
  Specificare una sottoscrizione di tipo merge e la priorità per la risoluzione dei conflitti nella pagina **Tipo di sottoscrizione** della Creazione guidata nuova sottoscrizione. Per ulteriori informazioni sull'utilizzo di questa procedura guidata, vedere [Create a Pull Subscription](create-a-pull-subscription.md) e [Create a Push Subscription](create-a-push-subscription.md).  
  
 Dopo la creazione di una sottoscrizione non è più possibile modificarne il tipo. È tuttavia possibile modificare la priorità per il tipo di sottoscrizione del server nella finestra di dialogo **Proprietà sottoscrizione - \<ServerPubblicazione>: \<DatabasePubblicazione>**. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) e [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md).  
  
### <a name="to-specify-a-merge-subscription-type-and-conflict-resolution-priority"></a>Per specificare una sottoscrizione di tipo merge e la priorità per la risoluzione dei conflitti  
  
1.  Nella pagina **Tipo di sottoscrizione** della Creazione guidata sottoscrizione selezionare **Client** o **Server** per l'opzione **Tipo di sottoscrizione** .  
  
2.  Se si seleziona un tipo di sottoscrizione **Server**, immettere anche un valore compreso tra 0,00 e 99,99 per l'opzione **Priorità per la risoluzione dei conflitti** .  
  
### <a name="to-modify-the-conflict-resolution-priority"></a>Per modificare la priorità per la risoluzione dei conflitti  
  
1.  Nella finestra di dialogo **Proprietà sottoscrizione - \<ServerPubblicazione>: \<DatabasePubblicazione>** visualizzata nel server di pubblicazione immettere un valore compreso tra 0,00 e 99,99 per l'opzione **Priorità**.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedi anche  
 [Rilevamento e risoluzione dei conflitti di replica di tipo merge avanzati](merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Subscribe to Publications](subscribe-to-publications.md)  
  
  
