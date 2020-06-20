---
title: Crittografia di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- encryption [SQL Server], about encryption
- security [SQL Server], encryption
- cryptography [SQL Server], about cryptography
ms.assetid: ead0150e-4943-4ad5-84c8-36f85c7278f4
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 6fc68e6f3280a8e23d6a1bf4f364aadfffd69f85
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85060224"
---
# <a name="sql-server-encryption"></a>Crittografia di SQL Server
  La crittografia è il processo che consiste nell'offuscare i dati tramite l'utilizzo di una chiave o di una password. È in grado di rendere i dati inutilizzabili se non si dispone della chiave di decrittografia o password corrispondente. La crittografia non risolve i problemi relativi al controllo di accesso, ma migliora la sicurezza limitando la perdita di dati anche se il controllo di accesso viene eluso. Se, ad esempio, il computer host del database è configurato scorrettamente e un pirata informatico ottiene dati riservati, le informazioni sottratte potrebbero essere inutilizzabili se crittografate.  
  
 È possibile utilizzare la crittografia in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per connessioni, dati e stored procedure. Nella tabella seguente sono disponibili ulteriori informazioni sulla crittografia in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Sebbene la crittografia sia un strumento prezioso per garantire la sicurezza, se ne sconsiglia l'utilizzo per tutti i dati o le connessioni. Per decidere se implementare la crittografia oppure no, considerare le modalità di accesso ai dati utilizzate dagli utenti. Se per accedere gli utenti utilizzano una rete pubblica, la crittografia dei dati potrebbe essere necessaria per aumentare il livello di sicurezza. Tuttavia, se tutti accedono attraverso una configurazione di Intranet sicura, la crittografia potrebbe non essere necessaria. L'utilizzo della crittografia comporta anche l'adozione di una strategia di manutenzione per password, chiavi e certificati.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Gerarchia di crittografia](encryption-hierarchy.md)  
 Informazioni sulla gerarchia di crittografia in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Scelta di un algoritmo di crittografia](choose-an-encryption-algorithm.md)  
 Informazioni sulla selezione di un algoritmo di crittografia efficace.  
  
 [Transparent Data Encryption &#40;TDE&#41;](transparent-data-encryption.md)  
 Informazioni generali sulla crittografia trasparente dei dati.  
  
 [Chiavi di crittografia del database e di SQL Server &#40;Motore di database&#41;](sql-server-and-database-encryption-keys-database-engine.md)  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], le chiavi di crittografia sono costituite da una combinazione di chiavi pubbliche, private e simmetriche utilizzate per proteggere dati riservati. In questa sezione vengono illustrate l'implementazione e la gestione delle chiavi di crittografia.  
  
## <a name="related-content"></a>Contenuto correlato  
 [Sicurezza di SQL Server](../securing-sql-server.md)  
 Panoramica della sicurezza della piattaforma [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e del funzionamento con gli utenti e gli oggetti a protezione diretta.  
  
 [Funzioni di crittografia &#40;Transact-SQL&#41;](/sql/t-sql/functions/cryptographic-functions-transact-sql)  
 Informazioni sull'implementazione delle funzioni di crittografia.  
  
 [ENCRYPTBYPASSPHRASE &#40;Transact-SQL&#41;](/sql/t-sql/functions/encryptbypassphrase-transact-sql)  
 Informazioni sull'utilizzo di una password per la crittografia dei dati.  
  
 [ENCRYPTBYKEY &#40;Transact-SQL&#41;](/sql/t-sql/functions/encryptbykey-transact-sql)  
 Informazioni sull'utilizzo di una chiave simmetrica per la crittografia dei dati.  
  
 [ENCRYPTBYASYMKEY &#40;Transact-SQL&#41;](/sql/t-sql/functions/encryptbyasymkey-transact-sql)  
 Informazioni sull'utilizzo di una chiave simmetrica per la crittografia dei dati.  
  
 [ENCRYPTBYCERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/encryptbycert-transact-sql)  
 Informazioni sull'utilizzo di un certificato per la crittografia dei dati.  
  
## <a name="external-resources"></a>Risorse esterne  
 [10 passaggi per la sicurezza di SQL Server 2005](https://www.itprotoday.com/sql-server/10-steps-sql-server-2005-security)  
 Informazioni aggiornate sulla sicurezza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Vedere anche  
 [sys. key_encryptions &#40;&#41;Transact-SQL](/sql/relational-databases/system-catalog-views/sys-key-encryptions-transact-sql)   
 [SQL Server e chiavi di crittografia del database &#40;motore di database&#41;](sql-server-and-database-encryption-keys-database-engine.md)   
 [Eseguire il backup e il ripristino delle chiavi di crittografia di Reporting Services](../../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)  
  
  
