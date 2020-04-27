---
title: Gestire spazi di tabella Oracle | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], managing tablespaces
- tablespaces [SQL Server replication]
ms.assetid: b8ea6c3b-01d6-4efc-bbfb-03b264530bbd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9a6bf22c7649646506b65628f556b52fead23375
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "63022292"
---
# <a name="manage-oracle-tablespaces"></a>Gestione di spazi di tabella Oracle
  Uno spazio di tabella è un'unità di archiviazione di database approssimativamente equivalente a un filegroup in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Gli spazi di tabella consentono l'archiviazione e la gestione di oggetti di database all'interno di singoli gruppi. Per ulteriori informazioni, vedere la documentazione di Oracle.  
  
 Quando si configura una tabella nell'ambito di una pubblicazione Oracle, è possibile specificare facoltativamente uno spazio di tabella Oracle esistente da utilizzare nell'archiviazione di informazioni di registrazione delle repliche. Se non specificato, lo spazio di tabella per gli oggetti di replica corrisponde allo spazio di tabella predefinito associato allo schema utente di amministrazione della replica che è stato configurato al momento della configurazione del server di pubblicazione.  
  
 **Per specificare uno spazio di tabella per una tabella di registrazione degli articoli**:  
  
-   Specificare uno spazio di tabella nella finestra di dialogo **Proprietà articolo** . Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Publication Properties](../publish/view-and-modify-publication-properties.md).  
  
-   Usare [sp_changearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql). Per utilizzare **sp_changearticle**, specificare quanto segue:  
  
    -   Nome del server di pubblicazione Oracle per il parametro **@publisher**.  
  
    -   Nome della pubblicazione Oracle per il parametro **@publication**.  
  
    -   Nome dell'articolo per il parametro **@article**.  
  
    -   Valore "tablespace" per il parametro **@property**.  
  
    -   Nome dello spazio di tabella per il parametro **@value**.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare un server di pubblicazione Oracle](configure-an-oracle-publisher.md)   
 [Oggetti creati nel server di pubblicazione Oracle](objects-created-on-the-oracle-publisher.md)  
  
  
