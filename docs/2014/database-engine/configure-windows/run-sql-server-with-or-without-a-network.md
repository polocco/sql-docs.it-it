---
title: Eseguire SQL Server in rete o non in rete | Microsoft docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- verifying Server service has been started
- net start [SQL Server]
- command prompt [SQL Server], connections
- SQL Server services, networks
- status information [SQL Server], Server service
- running SQL Server
- networking [SQL Server], SQL Server with or without
- services [SQL Server], networks
- starting Server service
- SQL Server, running
ms.assetid: 54eac961-5c7a-4481-982d-f93a64b5c2f4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a80e7e4d42f322bc42d0c67c57e3a1f9bddb87a0
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935095"
---
# <a name="run-sql-server-with-or-without-a-network"></a>Esecuzione di SQL Server in rete o non in rete
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può essere eseguito in rete o può funzionare anche senza una rete.  
  
## <a name="running-sql-server-on-a-network"></a>Esecuzione di SQL Server in rete  
 Affinché [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possa comunicare in rete, è necessario che il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sia in esecuzione. Per impostazione predefinita, il servizio [!INCLUDE[msCoName](../../includes/msconame-md.md)] viene avviato automaticamente tramite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows. Per verificare che il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sia stato avviato, al prompt dei comandi digitare il comando seguente:  
  
 **net start**  
  
 Se i servizi associati a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono stati avviati, nell'output di **net start** vengono visualizzati i servizi seguenti:  
  
-   Analysis Services (MSSQLSERVER)  
  
-   SQL Server (MSSQLSERVER)  
  
-   SQL Server Agent (MSSQLSERVER)  
  
## <a name="running-sql-server-without-a-network"></a>Esecuzione di SQL Server non in rete  
 Quando si esegue un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non in rete, non è necessario avviare il servizio predefinito [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Poiché [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], Gestione configurazione SQL Server e i comandi **net start** e **net stop** funzionano anche senza una rete, le procedure per l'avvio e l'arresto di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono identiche per operazioni in rete e in modalità autonoma.  
  
 Quando ci si connette a un'istanza autonoma di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da un client locale quale **sqlcmd**, la connessione alla rete viene ignorata e si accede direttamente all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite una pipe locale. La pipe locale e la pipe di rete vengono utilizzate rispettivamente quando non si utilizza e si utilizza la rete. Salvo diversa indicazione, le pipe locali e quelle di rete stabiliscono una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite la pipe standard (\\\\.\pipe\sql\query).  
  
 Quando si esegue la connessione a un'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] senza specificare il nome di un server, si utilizza una pipe locale. Quando si esegue la connessione a un'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e si specifica un nome di server, si utilizza una pipe di rete o un altro meccanismo IPC (InterProcess Communication) di rete, ad esempio IPX/SPX (Internetwork Packet Exchange/Sequenced Packet Exchange), a condizione che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sia stato configurato per l'utilizzo di più reti. Poiché un'istanza autonoma di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non supporta le pipe di rete, è necessario omettere l'argomento non necessario **/** _<nome_server>_ quando ci si connette all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da un client. Ad esempio, per connettersi a un'istanza autonoma di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da **osql**, digitare:  
  
 **osql/Usa/p**_\<saPassword>_  
  
  
