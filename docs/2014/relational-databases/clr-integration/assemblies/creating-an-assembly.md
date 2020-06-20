---
title: Creazione di un assembly | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- creating assemblies
- UNSAFE assemblies
- CREATE ASSEMBLY statement
- SAFE assemblies
- EXTERNAL_ACCESS assemblies
- assemblies [CLR integration], creating
ms.assetid: a2bc503d-b6b2-4963-8beb-c11c323f18e0
author: rothja
ms.author: jroth
ms.openlocfilehash: 995c3a621e6de5d1b878f28c7c0fffaae3311bd2
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84953876"
---
# <a name="creating-an-assembly"></a>Creazione di un assembly
  Gli oggetti di database gestiti, ad esempio le stored procedure o i trigger, vengono compilati e quindi distribuiti in unità denominate assembly. Gli assembly DLL gestiti devono essere registrati in [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] prima di poter utilizzare la funzionalità fornita dall'assembly. Per registrare l'assembly in un database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], utilizzare l'istruzione CREATE ASSEMBLY. In questo argomento viene descritto come registrare un assembly in un database tramite l'istruzione CREATE ASSEMBLY e specificare le impostazioni di sicurezza per l'assembly.  
  
## <a name="the-create-assembly-statement"></a>Istruzione CREATE ASSEMBLY  
 L'istruzione CREATE ASSEMBLY viene utilizzata per creare un assembly in un database. Esempio:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 La clausola FROM specifica il percorso dell'assembly da creare. Questo percorso può essere un percorso UNC (Universal Naming Convention) o un percorso di file fisico locale rispetto al computer.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non consente la registrazione di versioni diverse di un assembly con lo stesso nome, lingua e chiave pubblica.  
  
 È possibile creare assembly che fanno riferimento ad altri assembly. Quando viene creato un assembly in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , crea anche gli assembly a cui fa riferimento l'assembly a livello di radice, se gli assembly a cui si fa riferimento non sono già stati creati nel database.  
  
 Agli utenti del database o ai ruoli utente vengono concesse autorizzazioni per creare, e pertanto possedere, assembly in un database. Per creare assembly, l'utente o il ruolo del database deve disporre dell'autorizzazione CREATE ASSEMBLY.  
  
 Un assembly può fare riferimento ad altri assembly solo nei casi seguenti:  
  
-   L'assembly chiamato o cui si fa riferimento è di proprietà dello stesso utente o ruolo.  
  
-   L'assembly chiamato o cui si fa riferimento è stato creato nello stesso database.  
  
## <a name="specifying-security-when-creating-assemblies"></a>Configurazione della sicurezza durante la creazione di assembly  
 Quando si crea un assembly in un database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], è possibile specificare uno tra tre diversi livelli di sicurezza in cui eseguire il codice: `SAFE`, `EXTERNAL_ACCESS` o `UNSAFE`. Quando si esegue l'istruzione `CREATE ASSEMBLY`, nell'assembly di codice vengono effettuati alcuni controlli che possono impedire la registrazione dell'assembly nel server. Per ulteriori informazioni, vedere l'esempio di rappresentazione in [codeplex](https://msftengprodsamples.codeplex.com/).  
  
 `SAFE` è il set di autorizzazioni predefinito e può essere utilizzato nella maggior parte degli scenari. Per specificare un determinato livello di sicurezza, è necessario modificare la sintassi dell'istruzione CREATE ASSEMBLY come indicato di seguito:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = SAFE;  
```  
  
 È inoltre possibile creare un assembly con il set di autorizzazioni `SAFE` omettendo semplicemente la terza riga del codice precedente:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll';  
```  
  
 Quando il codice in un assembly viene eseguito utilizzando il set di autorizzazioni `SAFE`, può eseguire solo calcoli e accesso ai dati nel server tramite il provider gestito in-process.  
  
### <a name="creating-external_access-and-unsafe-assemblies"></a>Creazione di assembly EXTERNAL_ACCESS e UNSAFE  
 `EXTERNAL_ACCESS` consente di gestire scenari in cui il codice deve accedere a risorse esterne al server, ad esempio file, rete, Registro di sistema e variabili di ambiente. Ogni volta che il server accede a una risorsa esterna, rappresenta il contesto di sicurezza dell'utente che chiama il codice gestito.  
  
 L'autorizzazione `UNSAFE` per il codice è adatta in situazioni in cui un assembly non è effettivamente protetto o richiede accesso aggiuntivo a risorse limitate, ad esempio le API [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32.  
  
 Per creare un assembly `EXTERNAL_ACCESS` o `UNSAFE` in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], deve verificarsi una delle due condizioni seguenti:  
  
1.  L'assembly è firmato con nome sicuro o dispone di firma Authenticode con un certificato. Questo nome sicuro (o certificato) viene creato in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] come chiave asimmetrica (o certificato) e dispone di un account di accesso corrispondente con autorizzazione `EXTERNAL ACCESS ASSEMBLY` (per assembly di accesso esterni) o `UNSAFE ASSEMBLY` (per assembly non protetti).  
  
2.  Il proprietario del database (DBO) dispone dell' `EXTERNAL ACCESS ASSEMBLY` autorizzazione (per `EXTERNAL ACCESS` gli assembly) o `UNSAFE ASSEMBLY` (per `UNSAFE` gli assembly) e il database dispone della [proprietà di database TRUSTWORTHY](../../security/trustworthy-database-property.md) impostata su `ON` .  
  
 Le due condizioni elencate in precedenza vengono verificate in fase di caricamento dell'assembly (fase che include l'esecuzione). Per caricare l'assembly, è necessario che si verifichi almeno una delle due condizioni.  
  
 Si consiglia di non impostare la [Proprietà Trustworthy del database](../../security/trustworthy-database-property.md) in un database solo per l' `ON` esecuzione del codice Common Language Runtime (CLR) nel processo server. È invece consigliabile creare una chiave asimmetrica dal file di assembly nel database master. È quindi necessario creare un account di accesso con mapping alla chiave asimmetrica e concedere a tale account di accesso l'autorizzazione `EXTERNAL ACCESS ASSEMBLY` o `UNSAFE ASSEMBLY`.  
  
 Le [!INCLUDE[tsql](../../../includes/tsql-md.md)] istruzioni seguenti prima di eseguire l'istruzione CREATE assembly.  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll'     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey     
GRANT EXTERNAL ACCESS ASSEMBLY TO SQLCLRTestLogin;   
GO   
```  
  
> [!NOTE]  
>  È necessario creare un nuovo account di accesso da associare alla chiave asimmetrica. Questo account di accesso viene utilizzato solo per concedere le autorizzazioni e non è necessario che sia associato a un utente o utilizzato nell'applicazione.  
  
 Per creare un assembly `EXTERNAL ACCESS`, è necessario disporre dell'autorizzazione `EXTERNAL ACCESS`. Questa autorizzazione viene specificata durante la creazione dell'assembly:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
```  
  
 Le [!INCLUDE[tsql](../../../includes/tsql-md.md)] istruzioni seguenti prima di eseguire l'istruzione CREATE assembly.  
  
```  
USE master;   
GO    
  
CREATE ASYMMETRIC KEY SQLCLRTestKey FROM EXECUTABLE FILE = 'C:\MyDBApp\SQLCLRTest.dll';     
CREATE LOGIN SQLCLRTestLogin FROM ASYMMETRIC KEY SQLCLRTestKey ;    
GRANT UNSAFE ASSEMBLY TO SQLCLRTestLogin ;  
GO  
```  
  
 Per indicare che un assembly viene caricato con l'autorizzazione `UNSAFE`, è necessario specificare il set di autorizzazioni `UNSAFE` durante il caricamento dell'assembly nel server:  
  
```  
CREATE ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
WITH PERMISSION_SET = UNSAFE;  
```  
  
 Per ulteriori informazioni sulle autorizzazioni per ognuna delle impostazioni, vedere sicurezza dell' [integrazione con CLR](../security/clr-integration-security.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione degli assembly di integrazione CLR](managing-clr-integration-assemblies.md)   
 [Modifica di un assembly](altering-an-assembly.md)   
 [Eliminazione di un assembly](dropping-an-assembly.md)   
 [Sicurezza dall'accesso di codice per l'integrazione con CLR](../security/clr-integration-code-access-security.md)   
 [Proprietà di database TRUSTWORTHY](../../security/trustworthy-database-property.md)   
 [Accettazione di chiamanti parzialmente attendibili](../../../database-engine/dev-guide/allowing-partially-trusted-callers.md)  
  
