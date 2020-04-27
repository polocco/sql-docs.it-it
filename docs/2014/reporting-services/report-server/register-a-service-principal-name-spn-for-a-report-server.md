---
title: Registrare un nome dell'entità servizio (SPN) per un server di report | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: dda91d4f-77cc-4898-ad03-810ece5f8e74
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c88d8dd92fcedac2facff27f52492be5ccb74269
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66103604"
---
# <a name="register-a-service-principal-name-spn-for-a-report-server"></a>Registrare un nome dell'entità servizio (SPN) per un server di report
  Se si distribuisce [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in una rete che utilizza il protocollo Kerberos per l'autenticazione reciproca, è necessario creare un nome dell'entità servizio (SPN) per il server di report se questo è configurato per l'esecuzione come account utente di dominio.  
  
## <a name="about-spns"></a>Informazioni sugli SPN  
 Un SPN è un identificatore univoco per un servizio in una rete che utilizza l'autenticazione Kerberos. Un SPN è costituito da una classe del servizio, un nome host e una porta. In una rete che utilizza l'autenticazione Kerberos un SPN per il server deve essere registrato con un account computer predefinito, ad esempio NetworkService o LocalSystem, o un account utente. Gli SPN vengono registrati automaticamente per gli account predefiniti. Quando, tuttavia, si esegue un servizio utilizzando un account utente di dominio, è necessario registrare manualmente l'SPN per l'account che si desidera utilizzare.  
  
 Per creare un SPN, è possibile usare l'utilità della riga di comando **SetSPN** . Per altre informazioni, vedere gli argomenti seguenti:  
  
-   [SetSPN](https://technet.microsoft.com/library/cc731241\(WS.10\).aspx) (https://technet.microsoft.com/library/cc731241(WS.10).aspx).  
  
-   [Sintassi SetSPN dei nomi dell'entità servizio (SPN, SetSPN. exe)](https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx) (https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx).  
  
 Per eseguire l'utilità nel controller di dominio, è necessario essere un amministratore di dominio.  
  
## <a name="syntax"></a>Sintassi  
 La sintassi del comando per l'utilizzo dell'utilità SetSPN per la creazione di un SPN per il server di report è analoga alla seguente:  
  
```  
Setspn -s http/<computername>.<domainname>:<port> <domain-user-account>  
```  
  
 **SetSPN** è disponibile in Windows Server. L'argomento `-s` aggiunge un nome SPN dopo avere verificato che non sono presenti duplicati. **NOTA:** -s è disponibile in Windows Server a partire da Windows Server 2008.  
  
 `HTTP` è la classe del servizio. Il servizio Web ReportServer viene eseguito in HTTP.SYS. Una conseguenza della creazione di un SPN per HTTP è che a tutte le applicazioni Web presenti nello stesso computer ed eseguite in HTTP.SYS, incluse le applicazioni ospitate in IIS, verranno concessi ticket basati sull'account utente di dominio. Se tali servizi vengono eseguiti con un account diverso, le richieste di autenticazione avranno esito negativo. Per evitare questo problema, assicurarsi di configurare tutte le applicazioni HTTP per l'esecuzione con lo stesso account oppure creare intestazioni host per ogni applicazione e quindi SPN distinti per ciascuna intestazione host. Quando si configurano le intestazioni host, è necessario apportare le modifiche DNS indipendentemente dalla configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 I valori specificati per \< *nomecomputer*>, \< *NomeDominio*> e \< *porta*> identificano l'indirizzo di rete univoco del computer che ospita il server di report. Può trattarsi di un nome host locale o di un nome di dominio completo (FQDN). Se è presente un solo dominio e si usa la porta 80, è possibile \<omettere *DomainName*> e \<la *porta*> dalla riga di comando. \<*Domain-User-account*> è l'account utente con cui viene eseguito il servizio del server di report e per il quale il nome SPN deve essere registrato.  
  
## <a name="register-an-spn-for-domain-user-account"></a>Registrare un SPN per l'account utente di dominio  
  
#### <a name="to-register-an-spn-for-a-report-server-service-running-as-a-domain-user"></a>Per registrare un SPN per un servizio del server di report eseguito come utente di dominio  
  
1.  Installare [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e configurare il servizio del server di report per l'esecuzione come account utente di dominio. Si noti che gli utenti non saranno in grado di connettersi al server di report fino a quando non vengono completati i passaggi seguenti.  
  
2.  Accedere al controller di dominio come amministratore di dominio.  
  
3.  Aprire una finestra del prompt dei comandi.  
  
4.  Copiare il comando seguente, sostituendo i valori segnaposto con quelli effettivi, validi per la rete in uso:  
  
    ```  
    Setspn -s http/<computer-name>.<domain-name>:<port> <domain-user-account>  
    ```  
  
     Ad esempio: `Setspn -s http/MyReportServer.MyDomain.com:80 MyDomainUser`  
  
5.  Eseguire il comando.  
  
6.  Aprire il file **RsReportServer.config** e individuare la sezione `<AuthenticationTypes>`.  
  
7.  Aggiungere `<RSWindowsNegotiate/>` come prima voce in questa sezione per abilitare NTLM.  
  
## <a name="see-also"></a>Vedi anche  
 [Configurare un account di servizio &#40;Configuration Manager SSRS&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)   
 [Configurare l'account del servizio del server di report &#40;Gestione configurazione SSRS&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Gestire un server di report in modalità nativa di Reporting Services](manage-a-reporting-services-native-mode-report-server.md)  
  
  
