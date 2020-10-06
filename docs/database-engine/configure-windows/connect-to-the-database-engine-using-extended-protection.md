---
title: Connessione al motore di database mediante la protezione estesa | Microsoft Docs
description: Scoprire come la protezione estesa usa l'associazione al servizio e l'associazione di canale per impedire un attacco di tipo relay per l'autenticazione. Informazioni su come abilitare questa funzionalità.
ms.custom: ''
ms.date: 05/21/2019
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- spoofing attacks
- service binding
- luring attacks
- Schannel
- channel binding
- Extended Protection
ms.assetid: ecfd783e-7dbb-4a6c-b5ab-c6c27d5dd57f
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 22b1d58bac2433f9f5bae7dac5a6568050e38daf
ms.sourcegitcommit: 2f868a77903c1f1c4cecf4ea1c181deee12d5b15
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2020
ms.locfileid: "91670284"
---
# <a name="connect-to-the-database-engine-using-extended-protection"></a>Connessione al motore di database mediante la protezione estesa
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il supporto per la **protezione estesa** è disponibile a partire da [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]. La**protezione estesa per l'autenticazione** è una funzionalità dei componenti di rete implementata dal sistema operativo. La**protezione estesa** è supportata in Windows 7 e in Windows Server 2008 R2 La**protezione estesa** è inclusa nei Service Pack per i sistemi operativi [!INCLUDE[msCoName](../../includes/msconame-md.md)] meno recenti. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è più sicuro quando le connessioni vengono effettuate tramite **protezione estesa**.  
  
> [!IMPORTANT]  
> Per impostazione predefinita, in Windows la **protezione estesa** non è abilitata. Per informazioni su come abilitare la **protezione estesa** in Windows, vedere la pagina relativa alla [protezione estesa per l'autenticazione](/dotnet/framework/wcf/feature-details/extended-protection-for-authentication-overview).
  
## <a name="description-of-extended-protection"></a>Descrizione della protezione estesa  
 La**protezione estesa** utilizza l'associazione al servizio e l'associazione di canale per impedire un attacco di tipo relay per l'autenticazione. In un attacco di questo tipo un client che può eseguire l'autenticazione NTLM, ad esempio Esplora risorse, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Outlook, un'applicazione .NET SqlClient e così via, si connette all'autore dell'attacco, ad esempio un file server CIFS dannoso. L'autore usa le credenziali del client per mascherarsi ed eseguire l'autenticazione per un servizio, ad esempio un'istanza del servizio [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 Questo attacco presenta due varianti:  
  
-   In un attacco luring il client viene adescato per eseguire una connessione volontaria all'autore dell'attacco.  
  
-   In un attacco di tipo spoofing il client tenta di connettersi a un servizio valido, ma non è in grado di rilevare che uno o entrambi i routing DNS e IP sono stati danneggiati in modo da eseguire il reindirizzamento della connessione all'autore dell'attacco.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta l'associazione al servizio e l'associazione di canale per ridurre tali attacchi sulle istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="service-binding"></a>associazione al servizio  
 L'associazione al servizio risolve il problema degli attacchi luring richiedendo a un client di inviare un nome SPN firmato del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] al quale il client intende connettersi. Come parte della risposta di autenticazione, il servizio verifica che il nome SPN ricevuto nel pacchetto corrisponda al proprio nome SPN. Se viene adescato per connettersi all'autore di un attacco, il client includerà il nome SPN firmato di tale autore. L'autore dell'attacco non può inoltrare il pacchetto per l'autenticazione del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] reale come client, in quanto includerebbe il nome SPN dell'autore dell'attacco. L'associazione al servizio comporta un costo trascurabile una tantum, ma non neutralizza gli attacchi di spoofing. Si verifica l'associazione al servizio quando un'applicazione client non utilizza la crittografia per connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="channel-binding"></a>associazione di canale  
 L'associazione di canale stabilisce un canale sicuro (Schannel) tra un client e un'istanza del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Il servizio verifica l'autenticità del client confrontando il token CBT (Channel Binding Token) del client specifico di tale canale con il proprio CBT. L'associazione di canale neutralizza sia gli attacchi luring che di spoofing. Comporta tuttavia costi di runtime maggiori in quanto richiede la crittografia TLS (Transport Layer Security) di tutto il traffico della sessione. Si verifica l'associazione di canale quando un'applicazione client utilizza la crittografia per connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], indipendentemente dal fatto che la crittografia venga imposta dal client o dal server.  
  
> [!WARNING]  
>  I provider di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e [!INCLUDE[msCoName](../../includes/msconame-md.md)] per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supportano TLS 1.0 e SSL 3.0. Se si applica un protocollo diverso, ad esempio TLS 1.1 o TLS 1.2, apportando modifiche nel livello SChannel del sistema operativo, le connessioni a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] potrebbero non riuscire.  
  
### <a name="operating-system-support"></a>Supporto nei sistemi operativi  
 Nei collegamenti seguenti vengono fornite ulteriori informazioni sul supporto della **protezione estesa**in Windows:  
  
-   [Integrated Windows Authentication with Extended Protection](/previous-versions/visualstudio/visual-studio-2008/dd639324(v=vs.90))  
  
-   [Microsoft Security Advisory (973811), Extended Protection for Authentication](/security-updates/SecurityAdvisories/2009/973811)
  
## <a name="settings"></a>Impostazioni  
 Sono disponibili tre impostazioni di connessione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che influiscono sull'associazione al servizio e sull'associazione di canale. Tali impostazioni possono essere configurate tramite Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o WMI e possono essere visualizzate utilizzando il facet **Impostazioni installazione server** della gestione basata su criteri.  
  
-   **Forza crittografia**  
  
     I valori possibili sono **Attivata** e **Disattivata**. Per utilizzare l'associazione di canale, è necessario impostare **Forza crittografia** su **Attivata**in modo da forzare la crittografia su tutti i client. Se impostata su **Disattivata**, viene garantita solo l'associazione al servizio. **Forza crittografia** è disponibile in **Proprietà - Protocolli per MSSQLSERVER (scheda Flag)** in Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   **Protezione estesa**  
  
     I valori possibili sono **Disattivata**, **Consentita**e **Obbligatoria**. La variabile relativa alla **Protezione estesa** consente agli utenti di configurare il livello di **protezione estesa** per ogni istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . **Protezione estesa** è disponibile in **Proprietà - Protocolli per MSSQLSERVER (scheda Avanzate)** in Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    -   Se impostata su **Disattivata**, la **protezione estesa** è disabilitata. L'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accetterà connessioni da qualsiasi client, protetto o non protetto. Il valore**Disattivata** è compatibile con i sistemi operativi precedenti e senza patch installate, sebbene sia meno sicuro. Utilizzare questa impostazione quando si è sicuri che i sistemi operativi dei client non supportano la protezione estesa.  
  
    -   Se impostata su **Consentita**, la **protezione estesa** è obbligatoria per le connessioni da sistemi operativi che supportano la **protezione estesa**. **Protezione estesa** viene invece ignorata per le connessioni da sistemi operativi che non supportano **tale caratteristica**. Le connessioni da applicazioni client non protette in esecuzione su sistemi operativi client protetti vengono rifiutate. Sebbene sia più sicura di **Disattivata**, questa impostazione non garantisce il livello più elevato di sicurezza. Utilizzare questa impostazione negli ambienti misti, dove alcuni sistemi operativi supportano la **protezione estesa** e altri no.  
  
    -   Se impostata su **Obbligatoria**, vengono accettate solo le connessioni da applicazioni protette su sistemi operativi protetti. Questa impostazione è la più sicura, ma le connessioni a **da sistemi operativi o applicazioni che non supportano la** protezione estesa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]non riuscirà.  
  
-   **SPN NTLM accettati**  
  
     La variabile relativa ai nomi **SPN NTLM accettati** è necessaria quando un server è noto con più nomi SPN. Se un client tenta di connettersi al server tramite un nome SPN valido sconosciuto al server, l'associazione al servizio non riuscirà. Per evitare questo problema, gli utenti possono specificare diversi nomi SPN che rappresentano il server utilizzando **SPN NTLM accettati**. L'impostazione**SPN NTLM accettati** è costituita da una serie di nomi SPN separati da punti e virgola. Per consentire, ad esempio, l'uso dei nomi **MSSQLSvc/ HostName1.Contoso.com** e **MSSQLSvc/ HostName2.Contoso.com**, digitare **MSSQLSvc/HostName1.Contoso.com;MSSQLSvc/HostName2.Contoso.com** nella casella **SPN NTLM accettati** . La lunghezza massima della variabile è di 2048 caratteri. **SPN NTLM accettati** è disponibile in **Proprietà - Protocolli per MSSQLSERVER (scheda Avanzate)** in Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="enabling-extended-protection-for-the-database-engine"></a>Abilitazione della protezione estesa per il motore di database  
 Per utilizzare la **protezione estesa**, è necessario disporre sia sul server che sul client di un sistema operativo che supporti **questa caratteristica**. È inoltre necessario che la **protezione estesa** sia abilitata nel sistema operativo. Per ulteriori informazioni sull'abilitazione della **protezione estesa** per il sistema operativo in uso, vedere [Protezione estesa per l'autenticazione](/dotnet/framework/wcf/feature-details/extended-protection-for-authentication-overview).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il supporto per la **protezione estesa** è disponibile a partire da [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]. La**protezione estesa** per alcune versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verrà resa disponibile negli aggiornamenti futuri. Dopo aver abilitato la **protezione estesa** nel server, effettuare i passaggi seguenti per abilitarla **protezione estesa**:  
  
1.  Dal menu **Start** scegliere **Tutti i programmi**, **Microsoft SQL Server** , quindi fare clic su **Gestione configurazione SQL Server**.  
  
2.  Espandere **Configurazione di rete SQL Server** e quindi fare clic con il pulsante destro del mouse su **Protocolli per** _\<_InstanceName*>* e scegliere **Proprietà**.  
  
3.  Sia per l'associazione di canale che per l'associazione al servizio, nella scheda **Avanzate** configurare l'impostazione adatta per **Protezione estesa** .  
  
4.  Facoltativamente, quando un server è noto con più nomi SPN, nella scheda **Avanzate** configurare il campo **SPN NTLM accettati** come descritto nella sezione "Impostazioni".  
  
5.  Per l'associazione di canale, nella scheda **Flag** impostare **Forza crittografia** su **Attivata**.  
  
6.  Riavviare il servizio [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
## <a name="configuring-other-sql-server-components"></a>Configurazione degli altri componenti di SQL Server  
 Per altre informazioni su come configurare [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vedere [Protezione estesa per l'autenticazione con Reporting Service](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md).  
  
 Quando si utilizza IIS per accedere ai dati di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilizzando una connessione HTTP o HTTPs, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] può usufruire della protezione estesa fornita da IIS. Per ulteriori informazioni sulla configurazione di IIS per l'utilizzo della protezione estesa, vedere l'articolo relativo alla [configurazione della protezione estesa in IIS 7.5](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee909472(v=ws.10)).  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di rete del server](../../database-engine/configure-windows/server-network-configuration.md)   
 [Configurazione di rete dei client](../../database-engine/configure-windows/client-network-configuration.md)   
 [Extended Protection for Authentication Overview](/previous-versions/dotnet/netframework-3.5/dd767318(v=vs.90))   
 [Integrated Windows Authentication with Extended Protection](/previous-versions/visualstudio/visual-studio-2008/dd639324(v=vs.90))  
  
