---
title: Connessione a SQL Server tramite un server proxy (Gestione configurazione SQL Server) | Microsoft Docs
description: Informazioni su come usare Gestione configurazione SQL Server per connettersi a SQL Server tramite un server proxy. Scoprire come usare WinSock remoto (RWS) per l'ascolto remoto.
ms.custom: ''
ms.date: 12/15/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Remote WinSock
- RWS
- LATs
- proxy servers [SQL Server]
- connections [SQL Server], proxy server
- Microsoft Proxy Server [SQL Server]
- local address tables [SQL Server]
ms.assetid: 39714de0-2a1f-4179-9091-5c3fa4612545
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 0b8e6c54a7f496f06067bb0393f83899f8df4253
ms.sourcegitcommit: 2f868a77903c1f1c4cecf4ea1c181deee12d5b15
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2020
ms.locfileid: "91670276"
---
# <a name="connect-to-sql-server-through-a-proxy-server-sql-server-configuration-manager"></a>Connessione a SQL Server tramite un server proxy (Gestione configurazione SQL Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  In questo argomento viene illustrato come connettersi a SQL Server tramite un server proxy in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando Gestione configurazione SQL Server. Per l'attesa da postazioni remote tramite Remote WinSock (RWS), definire la tabella di indirizzi locali (LAT, Local Address Table) per il server proxy, in modo che l'indirizzo del nodo di attesa non sia compreso nell'intervallo degli indirizzi della tabella LAT.  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> Utilizzo di Gestione configurazione SQL Server  
  
#### <a name="to-enable-connections-to-sql-server-through-microsoft-proxy-server"></a>Per consentire le connessioni a SQL Server tramite Microsoft Proxy Server  
  
1.  Seguire i passaggi in [Configurazione di un server per l'attesa su una porta TCP specifica &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port.md) per determinare le porte TCP/IP usate dal [!INCLUDE[ssDE](../../includes/ssde-md.md)] o per configurare il [!INCLUDE[ssDE](../../includes/ssde-md.md)] per l'uso della porta desiderata.  
  
2.  Nel server proxy definire la tabella di indirizzi locali (LAT) per il server proxy, affinché l'indirizzo del nodo di attesa non sia compreso nell'intervallo delle voci della tabella LAT. Per ulteriori informazioni, vedere la documentazione del server proxy.  
  
> [!NOTE]
>  Questo argomento si applica a [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]locale. Per i problemi di connessione correlati a [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], vedere [Risoluzione dei problemi di connessione al database SQL di Azure](/azure/sql-database/sql-database-troubleshoot-common-connection-issues).