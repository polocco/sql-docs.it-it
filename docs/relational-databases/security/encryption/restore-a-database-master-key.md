---
title: Ripristinare la chiave master di un database | Microsoft Docs
description: Informazioni su come ripristinare la chiave master del database in SQL Server usando SQL Server Management Studio con Transact-SQL.
ms.custom: ''
ms.date: 01/02/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], importing
ms.assetid: 16897cc5-db8f-43bb-a38e-6855c82647cf
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 9860b952751937b18ca5e95e92ac959bb86abd23
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85892245"
---
# <a name="restore-a-database-master-key"></a>Ripristino di una chiave master del database
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  In questo argomento viene descritto come ripristinare una chiave master del database in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
## <a name="before-you-begin"></a>Prima di iniziare  
  
### <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
  
- Quando si ripristina la chiave master, in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vengono decrittografate tutte le chiavi crittografate con la chiave master attiva corrente. Tali elementi venogno poi crittografati nuovamente con la chiave master ripristinata. Si tratta di un'operazione che utilizza molte risorse e pertanto dovrebbe essere pianificata in periodi di carico ridotto. L'operazione di ripristino avrà esito negativo se la chiave master del database corrente non è aperta e non è possibile aprirla, oppure se non è possibile decrittografare le eventuali chiavi crittografate con tale chiave master.  
  
- In caso di esito negativo di una qualsiasi delle operazioni di decrittografia, il ripristino avrà esito negativo. È possibile utilizzare l'opzione FORCE per ignorare eventuali errori, ma in questo caso andranno perduti tutti i dati che non possono essere decrittografati.  
  
- Se la chiave master è stata crittografata con la chiave master del servizio, anche la chiave master ripristinata verrà crittografata con la chiave master del servizio.  
  
- Se il database corrente non include alcuna chiave master, con l'esecuzione di RESTORE MASTER KEY verrà creata una chiave master. La nuova chiave master non verrà crittografata automaticamente con la chiave master del servizio.  
  
## <a name="security"></a>Sicurezza  
  
### <a name="permissions"></a>Autorizzazioni
È richiesta l'autorizzazione CONTROL per il database.  
  
## <a name="using-sql-server-management-studio-with-transact-sql"></a>Utilizzo di SQL Server Management Studio con Transact-SQL  
  
### <a name="to-restore-the-database-master-key"></a>Per ripristinare la chiave master del database  
  
1. Recuperare una copia della chiave master del database da un supporto di backup fisico o da una directory nel file system locale.  
  
2. In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
3. Sulla barra Standard fare clic su **Nuova query**.  
  
4. Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  

    ```sql
    -- Restores the database master key of the AdventureWorks2012 database.  
    USE AdventureWorks2012;  
    GO  
    RESTORE MASTER KEY   
        FROM FILE = 'c:\backups\keys\AdventureWorks2012_master_key'   
        DECRYPTION BY PASSWORD = '3dH85Hhk003#GHkf02597gheij04'   
        ENCRYPTION BY PASSWORD = '259087M#MyjkFkjhywiyedfgGDFD';  
    GO  
    ```  
  
    > [!NOTE]  
    > Il percorso del file della chiave e della password della chiave (se esistente) sarà diverso da quello indicato in precedenza. Assicurarsi che entrambi siano specifici della configurazione della chiave e del server in uso.  
  
 Per altre informazioni, vedere [RESTORE MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/restore-master-key-transact-sql.md)  
