---
title: Sicurezza dall'accesso di codice per l'integrazione con CLR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- UNSAFE assemblies
- permissions [CLR integration]
- common language runtime [SQL Server], security
- SAFE assemblies
- code access security [CLR integration]
- EXTERNAL_ACCESS assemblies
ms.assetid: 2111cfe0-d5e0-43b1-93c3-e994ac0e9729
author: rothja
ms.author: jroth
ms.openlocfilehash: 75b283da2760b39349351802a83caae04e546c06
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84953448"
---
# <a name="clr-integration-code-access-security"></a>Sicurezza da accesso di codice dell'integrazione con CLR
  Common Language Runtime (CLR) supporta un modello di sicurezza definito sicurezza dall'accesso di codice per il codice gestito che prevede che le autorizzazioni vengano concesse agli assembly in base all'identità del codice. Per ulteriori informazioni, vedere la sezione relativa alla sicurezza da accesso di codice in .NET Framework SDK (Software Development Kit).  
  
 I criteri di sicurezza che determinano le autorizzazioni concesse agli assembly vengono definiti in tre punti diversi:  
  
-   Criteri del computer: criteri attivi per tutto il codice gestito in esecuzione sul computer nel quale viene installato [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Criteri utente: criteri attivi per il codice gestito ospitato da un processo. Per il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] servizio è in esecuzione.  
  
-   Criteri host: criteri impostati dall'host di CLR (in questo caso, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]), attivi per il codice gestito in esecuzione su quell'host.  
  
 Il meccanismo di sicurezza da accesso di codice supportato da CLR si basa sul presupposto che il runtime possa ospitare codice completamente o parzialmente attendibile. Le risorse protette dalla sicurezza dall'accesso di codice CLR vengono in genere incapsulate da interfacce di programmazione dell'applicazione gestite che requirethe l'autorizzazione corrispondente prima di consentire l'accesso alla risorsa. Demandfor l'autorizzazione viene soddisfatta solo se tutti i chiamanti (a livello di assembly) nello stack di chiamate dispongono dell'autorizzazione corrispondente per la risorsa.  
  
 Il set di autorizzazioni di sicurezza per l'accesso di codice che viene concesso al codice gestito durante l'esecuzione all'interno di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] concede un set di autorizzazioni a un assembly caricato in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , il set di autorizzazioni finale fornito al codice utente può essere ulteriormente limitato dai criteri a livello di utente e computer.  
  
## <a name="sql-server-host-policy-level-permission-sets"></a>Set di autorizzazioni a livello di criteri host di SQL Server  
 Il set di autorizzazioni della sicurezza da accesso di codice concesso agli assembly al livello di criteri host di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è determinato dal set di autorizzazioni specificato durante la creazione dell'assembly. Sono disponibili tre set di autorizzazioni: `SAFE` , `EXTERNAL_ACCESS` e `UNSAFE` (specificato utilizzando l'opzione **PERMISSION_SET** di[create assembly &#40;&#41;Transact-SQL ](/sql/t-sql/statements/create-assembly-transact-sql)).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Non è indicato per il dominio applicazione predefinito che sarebbe attivo quando [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] crea un'istanza di CLR.  
  
 Fixedpolicy per gli assembly di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sistema e i criteri specificati dall'utente per gli assembly utente.  
  
 I criteri fissi per gli assembly CLR e gli assembly di sistema di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] concedono loro l'attendibilità totale.  
  
 La parte dei criteri host di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] specificata dall'utente è basata su uno dei tre bucket di autorizzazione specificati per ogni assembly dal relativo proprietario. Per ulteriori informazioni sulle autorizzazioni di sicurezza elencate in basso, vedere .NET Framework SDK.  
  
### <a name="safe"></a>SAFE  
 È consentito solo il calcolo interno e l'accesso locale ai dati. `SAFE` è il set di autorizzazioni più restrittivo. Il codice eseguito da un assembly con autorizzazioni `SAFE` non può accedere a risorse di sistema esterne come file, la rete, variabili di ambiente o il Registro di sistema.  
  
 Gli assembly `SAFE` dispongono delle autorizzazioni e dei valori seguenti:  
  
|Autorizzazione|Valori/Descrizione|  
|----------------|-----------------------------|  
|`SecurityPermission`|`Execution:` autorizzazione a eseguire il codice gestito.|  
|`SqlClientPermission`|`Context connection = true`, `context connection = yes`: è possibile utilizzare solo la connessione di contesto e la stringa di connessione può specificare solo un valore "context connection=true" o "context connection=yes".<br /><br /> **AllowBlankPassword = false:**  Non sono consentite password vuote.|  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 Gli assembly EXTERNAL_ACCESS hanno le stesse autorizzazioni degli `SAFE` assembly, con la possibilità aggiuntiva di accedere a risorse di sistema esterne, ad esempio file, reti, variabili di ambiente e il registro di sistema.  
  
 Gli assembly `EXTERNAL_ACCESS` dispongono anche delle autorizzazioni e dei valori seguenti:  
  
|Autorizzazione|Valori/Descrizione|  
|----------------|-----------------------------|  
|`DistributedTransactionPermission`|`Unrestricted:`Sono consentite transazioni distribuite.|  
|`DNSPermission`|`Unrestricted:`Autorizzazione per richiedere informazioni ai server dei nomi di dominio.|  
|`EnvironmentPermission`|`Unrestricted:` l'accesso completo alle variabili di sistema e di ambiente dell'utente è consentito.|  
|`EventLogPermission`|`Administer:` consente di eseguire diverse operazioni. Esse sono: creare un'origine eventi, leggere i log esistenti, eliminare i log o le origini eventi, rispondere alle immissioni, cancellare un log eventi, mettersi in attesa di eventi e accedere a una raccolta di tutti i log eventi.|  
|`FileIOPermission`|`Unrestricted:` l'accesso completo a file e cartelle è consentito.|  
|`KeyContainerPermission`|`Unrestricted:` l'accesso completo ai contenitori di chiavi è consentito.|  
|`NetworkInformationPermission`|`Access:` l'esecuzione del ping è consentita.|  
|`RegistryPermission`|Concede diritti di lettura a `HKEY_CLASSES_ROOT`, `HKEY_LOCAL_MACHINE`, `HKEY_CURRENT_USER`, `HKEY_CURRENT_CONFIG` e `HKEY_USERS.`|  
|`SecurityPermission`|`Assertion:` capacità di asserire che tutti i chiamanti del codice dispongono dell'autorizzazione necessaria per l'operazione.<br /><br /> `ControlPrincipal:` capacità di manipolare l'oggetto Principal.<br /><br /> `Execution:` autorizzazione a eseguire il codice gestito.<br /><br /> `SerializationFormatter:` capacità di fornire servizi di serializzazione.|  
|**SmtpPermission**|`Access:` le connessioni in uscita alla porta 25 dell'host SMTP sono consentite.|  
|`SocketPermission`|`Connect:` le connessioni in uscita (tutte le porte, tutti i protocolli) su un indirizzo di trasporto sono consentite.|  
|`SqlClientPermission`|`Unrestricted:` l'accesso completo all'origine dati è consentito.|  
|`StorePermission`|`Unrestricted:` l'accesso completo agli archivi certificati X.509 è consentito.|  
|`WebPermission`|`Connect:` le connessioni in uscita a risorse Web sono consentite.|  
  
### <a name="unsafe"></a>UNSAFE  
 UNSAFE concede agli assembly libero accesso a risorse interne ed esterne a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il codice eseguito all'interno di un assembly `UNSAFE` può chiamare anche il codice non gestito.  
  
 Agli assembly `UNSAFE` viene concessa l'autorizzazione `FullTrust`.  
  
> [!IMPORTANT]  
>  `SAFE` rappresenta l'impostazione di autorizzazione consigliata per gli assembly che eseguono attività di calcolo e di gestione di dati senza accedere alle risorse all'esterno di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. `EXTERNAL_ACCESS`per impostazione predefinita, gli assembly [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vengono eseguiti come account del servizio. l'autorizzazione per `EXTERNAL_ACCESS` l'esecuzione deve essere assegnata solo agli account di accesso attendibili per l'esecuzione come account del servizio. Dal punto di vista della sicurezza, gli assembly `EXTERNAL_ACCESS` e `UNSAFE` sono identici. Gli assembly `EXTERNAL_ACCESS` offrono tuttavia una protezione e un'affidabilità maggiore rispetto agli assembly `UNSAFE`. Se `UNSAFE` si specifica, il codice nell'assembly può eseguire operazioni non valide su [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Per ulteriori informazioni sulla creazione di assembly CLR in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , vedere [gestione degli assembly di integrazione CLR](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md).  
  
## <a name="accessing-external-resources"></a>Accesso a risorse esterne  
 Se un tipo definito dall'utente, una stored procedure o un altro tipo di assembly del costrutto viene registrato con il set di autorizzazioni `SAFE`, il codice gestito in esecuzione nel costrutto non è in grado di accedere alle risorse esterne. Se tuttavia i set di autorizzazioni `EXTERNAL_ACCESS` o `UNSAFE` vengono specificati, e il codice gestito tenta di accedere a risorse esterne, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] applica le regole seguenti:  
  
|Se|Risultato|  
|--------|----------|  
|Il contesto di esecuzione corrisponde a un account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|I tentativi di accesso a risorse esterne vengono negati e viene generata un'eccezione di sicurezza.|  
|Il contesto di esecuzione corrisponde a un account di accesso di Windows e rappresenta il chiamante originale.|L'accesso alla risorsa esterna viene effettuato nel contesto di sicurezza dell'account di servizio di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|Il chiamante non è il chiamante originale.|L'accesso viene negato e viene generata un'eccezione di sicurezza.|  
|Il contesto di esecuzione corrisponde a un account di accesso di Windows e rappresenta il chiamante originale, mentre il chiamante è stato rappresentato.|L'accesso verrà effettuato nel contesto di sicurezza del chiamante e non in quello dell'account del servizio.|  
  
## <a name="permission-set-summary"></a>Riepilogo dei set di autorizzazioni  
 Nel grafico seguente sono riepilogate le restrizioni e le autorizzazioni concesse ai set di autorizzazioni `SAFE`, `EXTERNAL_ACCESS` e `UNSAFE`.  
  
|||||  
|-|-|-|-|  
||`SAFE`|`EXTERNAL_ACCESS`|`UNSAFE`|  
|`Code Access Security Permissions`|Sola esecuzione|Esecuzione più accesso a risorse esterne|Senza restrizioni (incluso P/Invoke)|  
|`Programming model restrictions`|Sì|Sì|Nessuna restrizione|  
|`Verifiability requirement`|Sì|Sì|No|  
|`Local data access`|Sì|Sì|Sì|  
|`Ability to call native code`|No|No|Sì|  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza dell'integrazione con CLR](clr-integration-security.md)   
 [Attributi di protezione host e programmazione dell'integrazione con CLR](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Restrizioni del modello di programmazione dell'integrazione con CLR](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Ambiente CLR](../clr-integration-architecture-clr-hosted-environment.md)  
  
  
