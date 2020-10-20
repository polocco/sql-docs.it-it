---
description: Motore di database - Connetti al server (pagina Account di accesso)
title: Motore di database - Connetti al server (pagina Account di accesso)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.connecttosqlserver.login.f1
ms.assetid: e08cfbc3-bed5-4401-a13b-1c66d902fe32
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 04/07/2020
ms.openlocfilehash: fd86fd385e34d44f88aee3d9011a8bd929508359
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/14/2020
ms.locfileid: "92038729"
---
# <a name="connect-to-server-login-page-database-engine"></a>Motore di database - Connetti al server (pagina Account di accesso)

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Usare questa scheda per visualizzare o specificare le opzioni per la connessione al [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]. Nella maggior parte dei casi è possibile connettersi specificando il nome del computer del server di database nella casella **Nome server** e facendo clic su **Connetti**. Se si sta eseguendo la connessione a un'istanza denominata, usare il nome del computer seguito da una barra rovesciata e dal nome dell'istanza. Ad esempio: `mycomputer\myinstance`. Se ci si connette a [!INCLUDE[ssExpress](../../includes/ssexpress_md.md)], usare il nome del computer seguito da **\sqlexpress**.

Molti fattori possono incidere sulla possibilità di connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per informazioni, vedere le risorse seguenti:

- [Esercitazione - Lezione 1: Connessione al motore di database](../../relational-databases/lesson-1-connecting-to-the-database-engine.md)

- [Risolvere i problemi di connessione al motore di database di SQL Server](../../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)  

- [Solving Connectivity errors to SQL Server](https://support.microsoft.com/help/4009936/solving-connectivity-errors-to-sql-server) (Risoluzione di errori di connettività a SQL Server)

> [!NOTE]
> Per connettersi con l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , è necessario che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sia configurato in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e nella modalità di autenticazione di Windows. Per altre informazioni su come determinare e modificare la modalità di autenticazione, vedere [Procedura: Modifica della modalità di autenticazione del server](../../database-engine/configure-windows/change-server-authentication-mode.md).  

## <a name="options"></a>Opzioni

**Tipo di server** Per la registrazione di un server da Esplora oggetti, selezionare il tipo di server a cui connettersi: [!INCLUDE[ssDE](../../includes/ssde_md.md)], Analysis Services, Reporting Services o Integration Services. Nelle altre parti della finestra di dialogo vengono visualizzate solo le opzioni applicabili al tipo di server selezionato. Durante la registrazione di un server da Server registrati, la casella **Tipo server** è di sola lettura e corrisponde al tipo di server visualizzato nel componente Server registrati. Per registrare un tipo diverso di server, selezionare [!INCLUDE[ssDE](../../includes/ssde_md.md)], Analysis Services, Reporting Services o Integration Services nella barra degli strumenti Server registrati prima di avviare la registrazione di un nuovo server.

Quando si esegue una connessione a un'istanza del motore di database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], è necessario usare l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e specificare un database nella scheda **Proprietà connessione** della finestra di dialogo **Connetti al server** . Assicurarsi di selezionare la casella di controllo **Crittografa connessione** .

Per impostazione predefinita, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si connette al **master**. Se si specifica un database utente, si vedranno solo quel database e i relativi oggetti in Esplora oggetti. Se si esegue la connessione al **master**, si è in grado di vedere tutti i database. Per altre informazioni, vedere la [panoramica di database SQL di Microsoft Azure](/azure/sql-database/sql-database-technical-overview/).

**Nome server** Selezionare l'istanza del server a cui connettersi. Per impostazione predefinita verrà visualizzata l'ultima istanza del server a cui è stata effettuata la connessione.  

**Autenticazione** La versione corrente di SSMS offre cinque modalità di autenticazione quando si esegue la connessione a un'istanza di [!INCLUDE[ssDE](../../includes/ssde_md.md)]. Se la finestra di dialogo Autenticazione non corrisponde all'elenco seguente, scaricare la versione più recente di SSMS da [Scaricare SQL Server Management Studio (SSMS)](../download-sql-server-management-studio-ssms.md).

Quando si esegue una connessione a un'istanza del motore di database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite [!INCLUDE[ssSDS](../../includes/sssds-md.md)], è necessario usare l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e specificare un database nella scheda **Proprietà connessione** della finestra di dialogo **Connetti al server** . Assicurarsi di selezionare la casella di controllo **Crittografa connessione** .

Per impostazione predefinita, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si connette al **master**. Se si specifica un database utente quando si esegue una connessione a [!INCLUDE[ssSDS](../../includes/sssds-md.md)], si vedranno solo quel database e i relativi oggetti in Esplora oggetti. Se si esegue la connessione al **master**, si è in grado di vedere tutti i database. Per altre informazioni, vedere la [panoramica di database SQL di Microsoft Azure](/azure/sql-database/sql-database-technical-overview/).

> **Autenticazione di Windows**  
> [!INCLUDE[msCoName](../../includes/msconame_md.md)] Tale modalità consente di connettersi tramite un account utente di Windows.  
>
> **Autenticazione di SQL Server**  
> Quando un utente si connette con un nome account di accesso e una password specifici da una connessione non affidabile, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esegue l'autenticazione verificando che sia impostato un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e che la password specificata corrisponda a quella registrata in precedenza. Se non è stato impostato alcun account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , l'autenticazione non viene completata e viene segnalato un errore all'utente. Se possibile, usare l'autenticazione di Windows.  
>
> **Active Directory - Universale con supporto MFA**  
> Active Directory - Universale con supporto MFA è un flusso di lavoro interattivo che supporta Azure Multi-Factor Authentication (MFA). Azure MFA consente di salvaguardare l'accesso a dati e applicazioni soddisfacendo l'aspettativa dell'utente all'uso di un processo di accesso semplice. Offre autenticazione avanzata con una gamma di opzioni di verifica semplice, ad esempio telefonate, SMS, smart card con pin o notifiche di app mobili, consentendo agli utenti di scegliere il metodo preferito. Quando l'account utente è configurato per MFA il flusso di lavoro di autenticazione interattiva richiede intervento aggiuntivo dell'utente in finestre di dialogo popup, nell'uso di smart card e così via. Quando l'account utente è configurato per MFA, l'utente deve selezionare Autenticazione universale di Azure per la connessione. Se l'account utente non richiede MFA, l'utente può comunque usare le altre due opzioni di autenticazione di Azure Active Directory. Per altre informazioni, vedere [Supporto di SQL Server Management Studio (SSMS) per l'autenticazione MFA di Azure AD con il database SQL e Azure Synapse Analytics](/azure/azure-sql/database/authentication-mfa-ssms-overview). Se necessario, è possibile modificare il dominio che esegue l'autenticazione dell'accesso facendo clic su **Opzioni**, selezionando la scheda **Proprietà connessione** e quindi completando la casella **ID tenant o nome di dominio AD**.
>
> **Active Directory - Password**  
> L'autenticazione di Azure Active Directory è un meccanismo di connessione a [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] tramite identità in Azure Active Directory (Azure AD).  Usare questo metodo per la connessione a [!INCLUDE[ssSDS](../../includes/sssds-md.md)] se si è connessi a Windows con le credenziali di un dominio che non è federato con Azure o se si usa l'autenticazione di Azure AD tramite Azure AD basata sul dominio iniziale o client. Per altre informazioni, vedere [Connessione al database SQL tramite l'autenticazione di Azure Active Directory](/azure/azure-sql/database/authentication-aad-overview).  
>
> **Active Directory - Integrata** L'autenticazione di Azure Active Directory è un meccanismo di connessione a [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] tramite identità in Azure Active Directory (Azure AD). Usare questo metodo per la connessione a [!INCLUDE[ssSDS](../../includes/sssds-md.md)] se si è connessi a Windows con le credenziali di Azure Active Directory da un dominio federato. Per altre informazioni, vedere [Connessione al database SQL tramite l'autenticazione di Azure Active Directory](/azure/azure-sql/database/authentication-aad-overview).  
  
**Nome utente**: nome utente di Windows per la connessione. Questa opzione è disponibile solo se si è scelto di connettersi tramite **Autenticazione della password Active Directory**. È di sola lettura quando si seleziona **Autenticazione di Windows** o l'autenticazione **Active Directory - Integrata**.

**Account di accesso**: immettere l'account di accesso da usare per la connessione. Questa opzione è disponibile solo se si è scelto di connettersi tramite Autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o Autenticazione della password di Active Directory.

**Password**: immettere la password per l'account di accesso. Questa opzione è modificabile solo se si è scelto di connettersi tramite Autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o Autenticazione della password di Active Directory.

**Memorizza password**: selezionare questa opzione per fare in modo che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] archivi la password immessa. Questa opzione viene visualizzata solo se si è scelto di utilizzare l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per la connessione.

**Connetti**: fare clic per connettersi al server.  

**Opzioni**: fare clic per visualizzare le schede **Proprietà connessione** e **Parametri aggiuntivi per la connessione**.