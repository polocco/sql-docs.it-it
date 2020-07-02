---
title: Modifica di un assembly | Microsoft Docs
description: Utilizzare ALTER ASSEMBLY per aggiornare gli assembly registrati in SQL Server. È anche possibile modificare il set di autorizzazioni e aggiungere il codice sorgente o altri file per un assembly.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration], modifying
- permissions [CLR integration]
- altering assemblies
- ALTER ASSEMBLY statement
ms.assetid: 9e765fbd-f339-473c-8537-22f478e79696
author: rothja
ms.author: jroth
ms.openlocfilehash: d9ec69415e270770360b6901d8c3117790b5e16d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85717944"
---
# <a name="altering-an-assembly"></a>Modifica di un assembly
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  Gli assembly registrati in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] possono essere aggiornati da una versione più recente utilizzando l'istruzione ALTER ASSEMBLY. Per aggiornare un assembly, utilizzare l'istruzione ALTER ASSEMBLY con la sintassi seguente:  
  
```  
ALTER ASSEMBLY SQLCLRTest  
FROM 'C:\MyDBApp\SQLCLRTest.dll'  
```  
  
 ALTER ASSEMBLY non interrompe i processi in esecuzione che utilizzano l'assembly. L'esecuzione di tali processi continua con l'assembly non modificato. Non è possibile utilizzare ALTER ASSEMBLY per modificare le firme di funzioni, funzioni di aggregazione, stored procedure e trigger di CLR (Common Language Runtime). Nuovi metodi pubblici possono essere aggiunti all'assembly, i metodi privati possono essere modificati nel modo desiderato e i metodi pubblici possono essere modificati a condizione di non modificare le firme o gli attributi. Non è possibile modificare tramite ALTER ASSEMBLY i campi contenuti in un tipo definito dall'utente con serializzazione nativa, inclusi i membri dei dati o le classi base. Tutte le altre modifiche non sono supportate. Per ulteriori informazioni, vedere [ALTER ASSEMBLY &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-assembly-transact-sql.md).  
  
## <a name="changing-the-permission-set-of-an-assembly"></a>Modifica del set di autorizzazioni di un assembly  
 Il set di autorizzazioni di un assembly può essere anch'esso modificato utilizzando l'istruzione ALTER ASSEMBLY. L'istruzione seguente modifica il set di autorizzazioni dell'assembly SQLCLRTest in **EXTERNAL_ACCESS**.  
  
```  
ALTER ASSEMBLY SQLCLRTest  
WITH PERMISSION_SET = EXTERNAL_ACCESS   
```  
  
 Se il set di autorizzazioni di un assembly viene modificato da **Safe** a **EXTERNAL_ACCESS** o **unsafe**, è necessario innanzitutto creare una chiave asimmetrica e un account di accesso corrispondente con l'autorizzazione **External Access assembly** o **UNSAFE assembly** per l'assembly. Per altre informazioni, vedere [Creating an Assembly](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md).  
  
## <a name="adding-the-source-code-of-an-assembly"></a>Aggiunta del codice sorgente di un assembly.  
 La clausola ADD FILE nella sintassi ALTER ASSEMBLY non è presente in CREATE ASSEMBLY. È possibile utilizzarla per aggiungere codice sorgente o altri file associati a un assembly. I file vengono copiati dai percorsi originali e vengono archiviati nelle tabelle di sistema del database. In questo modo il codice sorgente o gli altri file saranno sempre disponibili nel caso in cui sia necessario ricreare o documentare la versione corrente del tipo definito dall'utente (UDT).  
  
 L'istruzione seguente aggiunge il codice sorgente della classe Point.cs per il tipo definito dall'utente Point. Il testo contenuto nel file Point.cs viene copiato e archiviato nel database con il nome "PointSource".  
  
 `ALTER ASSEMBLY Point`  
  
 `ADD FILE FROM 'C:\Projects\Point\Point.cs' AS PointSource`  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione degli assembly di integrazione CLR](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md)   
 [Creazione di un assembly](../../../relational-databases/clr-integration/assemblies/creating-an-assembly.md)   
 [Eliminazione di un assembly](../../../relational-databases/clr-integration/assemblies/dropping-an-assembly.md)   
 [ALTER ASSEMBLY &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-assembly-transact-sql.md)  
  
  
