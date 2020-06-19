---
title: MSSQLSERVER_-1 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "-1"
helpviewer_keywords:
- -1 (Database Engine error)
ms.assetid: bad25b91-eaed-46c0-a5b7-71117a32304c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bf33ef7895ebeae9af158e0b7d8c3c4447805893
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84969899"
---
# <a name="mssqlserver_-1"></a>MSSQLSERVER_-1
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|-1|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico||  
|Testo del messaggio|Si è verificato un errore durante il tentativo di stabilire una connessione al server.  Quando ci si connette a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], questo errore potrebbe essere provocato dal fatto che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non ammette connessioni remote sotto le impostazioni predefinite. (provider: interfacce di rete SQL, errore: 28 - Il server non supporta il protocollo richiesto) (Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Errore: -1)|  
  
## <a name="explanation"></a>Spiegazione  
 Non è possibile stabilire la connessione tra il client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e il server. L'errore può essere causato da uno dei problemi seguenti:  
  
-   Un nome di istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specificato non è valido.  
  
-   Il protocollo TCP o i protocolli named pipe non sono abilitati.  
  
-   La connessione è stata rifiutata dal firewall del server.  
  
-   Il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser (sqlbrowser) non è stato avviato.  
  
## <a name="user-action"></a>Azione dell'utente  
 Per risolvere l'errore, eseguire una delle operazioni seguenti:  
  
-   Controllare l'ortografia del nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specificato nella stringa di connessione.  
  
-   Usare lo strumento Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per consentire a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di accettare le connessioni remote tramite protocolli TCP o Named Pipes.  
  
-   Assicurarsi di avere configurato il firewall nell'istanza server di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per aprire porte per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e la porta di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser (UDP 1434).  
  
-   Assicurarsi che il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser sia stato avviato nel server.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare un Windows Firewall per l'accesso motore di database](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)   
 [Configurare i protocolli client](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Protocolli di rete e librerie di rete](../../sql-server/install/network-protocols-and-network-libraries.md)   
 [Configurazione della rete client](../../database-engine/configure-windows/client-network-configuration.md)   
 [Configurare i protocolli client](../../database-engine/configure-windows/configure-client-protocols.md)   
 [Abilitare o disabilitare un protocollo di rete del server](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)  
  
  
