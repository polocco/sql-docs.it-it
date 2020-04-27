---
title: Criteri password | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- ALTER LOGIN statement
- passwords [SQL Server], policy enforcement
- logins [SQL Server], passwords
- CHECK_EXPIRATION option
- complex passwords [SQL Server]
- passwords [SQL Server], expiration
- manual bad password count resets
- MUST_CHANGE option
- expiration [SQL Server]
- expired password [SQL Server]
- symbols [SQL Server]
- NetValidatePasswordPolicy() API
- passwords [SQL Server]
- password policy [SQL Server]
- resetting bad password counts
- security [SQL Server], passwords
- CHECK_POLICY option
- passwords [SQL Server], symbols
- bad password counts
- passwords [SQL Server], complexity
- characters [SQL Server], password policies
ms.assetid: c0040c0a-a18f-45b9-9c40-0625685649b1
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 7b28043d797585496686dea6fd0c5fad276f16b9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "63187964"
---
# <a name="password-policy"></a>Criteri password
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può usare i meccanismi di criteri password di Windows. I criteri password si applicano a un account di accesso che utilizza l'autenticazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e a un utente del database indipendente con password.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può applicare gli stessi criteri di complessità e scadenza utilizzati in Windows alle password all'interno di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa funzionalità dipende dall'API `NetValidatePasswordPolicy` .  
  
## <a name="password-complexity"></a>Complessità delle password  
 I criteri di complessità delle password sono progettati per fungere da deterrente agli attacchi a forza bruta aumentando il numero di password possibili. Quando vengono applicati i criteri di complessità delle password, le nuove password devono soddisfare i requisiti seguenti:  
  
-   Non devono contenere il nome account dell'utente.  
  
-   Devono essere composte da almeno otto caratteri.  
  
-   Devono contenere caratteri di almeno tre delle quattro categorie seguenti:  
  
    -   Lettere maiuscole dell'alfabeto latino (dalla A alla Z)  
  
    -   Lettere minuscole dell'alfabeto latino (dalla a alla z)  
  
    -   Numeri in base 10 (da 0 a 9)  
  
    -   Caratteri non alfanumerici, ad esempio punto esclamativo (!), dollaro ($), simbolo di cancelletto (#) o percentuale (%).  
  
 Le password possono contenere fino a 128 caratteri. È consigliabile utilizzare password più lunghe e complesse possibile.  
  
## <a name="password-expiration"></a>Scadenza delle password  
 I criteri di scadenza delle password consentono di gestire l'intervallo di validità di una password. Se in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono applicati i criteri di scadenza delle password, gli utenti ricevono un promemoria per la modifica delle vecchie password e gli account con password scadute vengono disabilitati.  
  
## <a name="policy-enforcement"></a>Applicazione dei criteri  
 L'applicazione dei criteri password può essere configurata separatamente per ogni account di accesso di SQL Server. Usare [ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) per configurare i criteri password di un account di accesso di SQL Server. Le regole seguenti sono valide per la configurazione dell'applicazione dei criteri password:  
  
-   Quando l'opzione CHECK_POLICY viene impostata su ON, si ottiene il comportamento seguente:  
  
    -   Anche CHECK_EXPIRATION viene impostato su ON, a meno che non lo si imposti esplicitamente su OFF.  
  
    -   La cronologia delle password viene inizializzata con il valore dell'hash della password corrente.  
  
    -   Vengono inoltre abilitate le opzioni**Durata blocco account**, **Soglia di blocchi dell'account**e **Reimposta blocco account dopo** .  
  
-   Quando l'opzione CHECK_POLICY viene impostata su OFF, si ottiene il comportamento seguente:  
  
    -   Anche l'opzione CHECK_EXPIRATION viene impostata su OFF.  
  
    -   Viene cancellata la cronologia delle password.  
  
    -   Viene reimpostato il valore di `lockout_time` .  
  
 Alcune combinazioni di criteri non sono supportate.  
  
-   Se si specifica MUST_CHANGE, è necessario impostare CHECK_EXPIRATION e CHECK_POLICY su ON. In caso contrario, l'istruzione non verrà eseguita correttamente.  
  
-   Se l'opzione CHECK_POLICY è impostata su OFF, non è possibile impostare CHECK_EXPIRATION su ON. Un'istruzione ALTER LOGIN che presenta questa combinazione di opzioni avrà esito negativo.  
  
 L'impostazione di CHECK_POLICY su ON impedirà la creazione di password:  
  
-   Null o vuote  
  
-   Equivalenti al nome del computer o dell'account di accesso  
  
-   Equivalenti a parole quali "password", "admin", "administrator", "sa", "sysadmin"  
  
 I criteri di sicurezza possono essere impostati in Windows o essere ricevuti dal dominio. Per visualizzare i criteri password nel computer, usare lo snap-in MMC Criteri di sicurezza locali (**secpol.msc**).  
  
## <a name="related-tasks"></a>Attività correlate  
 [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)  
  
 [ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql)  
  
 [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql)  
  
 [ALTER USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-user-transact-sql)  
  
 [Creazione di un account di accesso](authentication-access/create-a-login.md)  
  
 [Creazione di un utente di database](authentication-access/create-a-database-user.md)  
  
## <a name="related-content"></a>Contenuto correlato  
 [Password complesse](strong-passwords.md)  
  
  
