---
description: sys.dm_column_encryption_enclave (Transact-SQL)
title: sys. dm_column_encryption_enclave (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/11/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: system-objects
ms.topic: language-reference
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 480215cc2157887eedbafd7a5cf4368f03e65c93
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88423285"
---
# <a name="sysdm_column_encryption_enclave-transact-sql"></a>sys.dm_column_encryption_enclave (Transact-SQL)
[!INCLUDE [sqlserver2019-windows-only](../../includes/applies-to-version/sqlserver2019-windows-only.md)]

Restituisce i contatori delle prestazioni per l'enclave protetta per Always Encrypted. Per altre informazioni, vedere [Always Encrypted con enclave sicuri](../security/encryption/always-encrypted-enclaves.md).

Se l'enclave è configurata ed è stata inizializzata correttamente dopo l'ultimo riavvio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , la vista contiene esattamente una riga. Se l'enclave non è configurato o non è stato inizializzato correttamente, la vista non restituisce alcuna riga. 

|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|current_enclave_session_count|**int**|Numero corrente di sessioni client che utilizzano l'enclave.|  
|current_column_encryption_key_count|**int**|Conteggio delle chiavi di crittografia della colonna attualmente contenute nell'enclave.|  
|current_memory_size_kb|**bigint**|Dimensioni memoria enclave in KB|  
|total_evicted_session_count|**bigint**|Conteggio totale delle sessioni dell'enclave eliminate dall'ultimo riavvio del server.|   
  
## <a name="permissions"></a>Autorizzazioni  
È richiesta l'autorizzazione `VIEW SERVER STATE`.   
  
## <a name="examples"></a>Esempi  
 
```sql  
SELECT * FROM sys.dm_column_encryption_enclave;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare il tipo di enclave per l'opzione di configurazione del server Always Encrypted](../../database-engine/configure-windows/configure-column-encryption-enclave-type.md)
  
  
