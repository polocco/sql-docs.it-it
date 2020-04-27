---
title: Configurare l'account di esecuzione automatica (Gestione configurazione SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- no credentials option [Reporting Services]
- security [Reporting Services], unattended report processing
- unattended report processing [Reporting Services]
- credentials [Reporting Services]
- external data sources [Reporting Services]
- accounts [Reporting Services]
- reports [Reporting Services], processing
ms.assetid: 4e50733e-bd8c-4bf6-8379-98b1531bb9ca
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 42299bce176f3fa93b9a145204ff95e292aed542
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108884"
---
# <a name="configure-the-unattended-execution-account-ssrs-configuration-manager"></a>Configurare l'account di esecuzione automatica (Gestione configurazione SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] offre un account speciale da usare per l'elaborazione automatica dei report e per l'invio di richieste di connessione in rete. L'account viene utilizzato nei modi seguenti:  
  
-   Inviare richieste di connessione in rete per i report che utilizzano l'autenticazione del database oppure connettersi a origini dati del report esterne che non richiedono né utilizzano l'autenticazione. Per altre informazioni, vedere [Specificare le credenziali e le informazioni sulla connessione per le origini dati del report](../../integration-services/connection-manager/data-sources.md) nella documentazione online di SQL Server.  
  
-   Recuperare file di immagine esterni utilizzati nel report. Se si desidera utilizzare un file di immagine che non è accessibile tramite l'accesso anonimo, sarà possibile configurare l'account per l'esecuzione automatica dei report e concedere a tale account l'autorizzazione di accesso al file desiderato.  
  
 L'esecuzione automatica del report si riferisce a qualsiasi processo di esecuzione del report avviato da un evento che può essere sia un evento determinato dalla pianificazione, sia un evento di aggiornamento dei dati, piuttosto che da una richiesta dell'utente. Il server di report utilizza l'account per l'esecuzione automatica del report per accedere al computer che ospita l'origine dei dati esterna. Tale account è necessario perché le credenziali dell'account del servizio del server di report non vengono mai utilizzate per la connessione ad altri computer.  
  
> [!IMPORTANT]  
>  La configurazione di questo account è facoltativa. Se tuttavia si sceglie di non configurarlo, si disporrà di un minor numero di opzioni per la connessione ad alcune origini dei dati e potrebbe risultare impossibile recuperare file di immagine da computer remoti. Se si configura l'account, sarà necessario mantenerlo aggiornato. In particolare, se si consente la scadenza delle password oppure le informazioni dell'account vengono modificate in Active Directory, alla successiva elaborazione di un report verrà visualizzato l'errore seguente: "Accesso non riuscito (rsLogonFailed) Errore durante l'accesso: nome utente sconosciuto o password errata". La corretta manutenzione dell'account per l'elaborazione automatica dei report è essenziale, anche se non si intende recuperare immagini esterne o inviare richieste di connessione a computer esterni. Se si configura l'account ma successivamente ci si accorge che non viene utilizzato, sarà possibile eliminarlo per evitare di svolgere le attività di manutenzione di routine per gli account.  
  
## <a name="how-to-configure-the-account"></a>Come configurare l'account  
 È necessario utilizzare un account utente di dominio. Affinché possa essere utilizzato per lo scopo previsto, questo account deve essere diverso da quello utilizzato per l'esecuzione del servizio del server di report. Utilizzare un account con autorizzazioni minime (è sufficiente l'accesso in sola lettura con autorizzazioni di connessione di rete) e accesso limitato ai soli computer in cui risiedono le origini dati e le risorse utilizzate dal server di report. Per altre informazioni, vedere [Gestione configurazione Reporting Services &#40;modalità nativa&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 Per specificare l'account, è possibile usare lo strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] o l'utilità **rsconfig** . Il modo più semplice per configurare l'account di esecuzione automatica consiste nell'utilizzare lo strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e specificare le credenziali nella pagina Account di esecuzione.  
  
1.  Avviare lo strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e connettersi all'istanza del server di report da configurare. Per le istruzioni, vedere [Gestione configurazione Reporting Services &#40;modalità nativa&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
2.  Nella pagina Account di esecuzione selezionare **Specifica account di esecuzione**.  
  
3.  Digitare account e password, digitare nuovamente la password e quindi fare clic su **Applica**.  
  
### <a name="using-rsconfig-utility"></a>Utilizzo dell'utilità RSCONFIG  
 Un altro modo per impostare l'account consiste nell'usare l'utilità **rsconfig** . Per specificare l'account, usare l'argomento **-e** di **rsconfig**. Se si specifica l'argomento **-e** per **rsconfig** , si indica all'utilità di scrivere le informazioni relative all'account nel file di configurazione. Non è necessario specificare un percorso per RSreportserver.config. Per configurare l'account, effettuare le seguenti operazioni:  
  
1.  Creare o selezionare un account di dominio che abbia accesso ai computer e ai server che forniscono dati o servizi a un server di report. È consigliabile utilizzare un account che disponga di autorizzazioni limitate, ad esempio autorizzazioni di sola lettura.  
  
2.  Aprire il prompt dei comandi: nel menu **Start** scegliere **Esegui**, digitare **cmd** e quindi fare clic su **OK**.  
  
3.  Digitare il comando seguente per configurare l'account su un'istanza del server di report locale:  
  
     **rsconfig -e -u\<dominio/nome utente> -p\<password>**  
  
 **rsconfig -e** supporta argomenti aggiuntivi. Per altre informazioni sulla sintassi ed esempi di comandi, vedere [Utilità rsconfig &#40;SSRS&#41;](../tools/rsconfig-utility-ssrs.md) nella documentazione online di SQL Server.  
  
### <a name="how-account-information-is-stored"></a>Modalità di archiviazione delle informazioni sull'account  
 Quando si imposta l'account, le impostazioni seguenti vengono specificate come valori crittografati nel file RSreportserver.config in un'istanza locale o remota del server di report:  
  
```  
<UnattendedExecutionAccount>  
     <UserName></UserName>  
     <Password></Password>  
     <Domain></Domain>  
</UnattendedExecutionAccount>  
```  
  
 Dopo aver impostato i valori, non è possibile decrittografarli per visualizzare i valori in testo normale. Se si digitano i valori in modo errato o si dimenticano i valori specificati, è necessario usare lo strumento Configurazione di Reporting Services oppure eseguire **rsconfig -e** per ricominciare.  
  
## <a name="how-to-use-the-unattended-report-processing-account"></a>Come utilizzare l'account per l'elaborazione automatica dei report  
 Per recuperare file di immagine, il server di report utilizza automaticamente l'account e non è necessario alcun intervento specifico dell'utente. Per usare l'account per connettersi a origini dati esterne che forniscono dati ai report, è necessario specificare l'opzione **Tipo di credenziali** nella pagina delle proprietà dell'origine dati del report o dell'origine dati condivisa:  
  
-   In Gestione report o in un sito di SharePoint, selezionare l'opzione **credenziali non necessarie** .  
  
 L'account per l'elaborazione automatica dei report viene utilizzato principalmente per la connessione a server esterni e non come account di accesso a server di database. Se si desidera utilizzare le credenziali dell'account per accedere a un database, è necessario specificarle nella stringa di connessione. È possibile specificare **Integrated Security=SSPI** se il server di database supporta la sicurezza integrata di Windows e l'account usato per l'elaborazione automatica dei report è autorizzato a leggere il database. In caso contrario, è necessario immettere il nome e la password dell'utente nella stringa di connessione, in cui verranno visualizzati come testo non crittografato da tutti gli utenti che dispongono dell'autorizzazione necessaria per modificare le proprietà di connessione dell'origine dati.  
  
 È possibile ma non consigliabile utilizzare l'account per l'elaborazione automatica dei report per recuperare dati dopo aver stabilito la connessione. L'account è progettato per funzioni molto specifiche. Se lo si utilizza per il recupero dei dati, non potrà più essere utilizzato per lo scopo a cui è destinato.  
  
## <a name="how-to-maintain-the-unattended-report-processing-account"></a>Come gestire l'account per l'elaborazione automatica dei report  
 Dopo aver definito l'account è necessario garantire che l'account e la relativa password siano sempre aggiornati. Per aggiornare le impostazioni di configurazione in cui sono archiviate le informazioni sull'account, è possibile usare lo strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
1.  Avviare lo strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e connettersi all'istanza del server di report da configurare.  
  
2.  Nella pagina Account di esecuzione verificare che sia selezionata l'opzione **Specifica account di esecuzione** .  
  
3.  Immettere il nuovo account o la nuova password, digitare nuovamente la password e quindi fare clic su **Applica**.  
  
## <a name="how-to-delete-the-unattended-report-processing-account"></a>Come eliminare l'account per l'elaborazione automatica dei report  
 Se l'account non viene utilizzato, sarà possibile eliminarlo per evitare di svolgere le attività di manutenzione di routine per gli account.  
  
1.  Avviare lo strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e connettersi all'istanza del server di report da configurare.  
  
2.  Nella pagina Account di esecuzione deselezionare **Specifica account di esecuzione**.  
  
3.  Fare clic su **Applica**.  
  
 Le informazioni relative all'account vengono rimosse dal file RSReportServer.config.  
  
## <a name="see-also"></a>Vedi anche  
 [Reporting Services Configuration Manager &#40;del&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
