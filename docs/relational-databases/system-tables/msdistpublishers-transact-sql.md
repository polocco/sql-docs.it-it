---
description: MSdistpublishers (Transact-SQL)
title: MSdistpublishers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdistpublishers
- MSdistpublishers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistpublishers system table
ms.assetid: 31844099-4b33-4dc9-84b4-bac70aa82598
author: markingmyname
ms.author: maghan
ms.openlocfilehash: aa3f8872775f9d82a23d9ba2eb33a892696ca792
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2020
ms.locfileid: "89550993"
---
# <a name="msdistpublishers-transact-sql"></a>MSdistpublishers (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  La tabella **MSdistpublishers** contiene una riga per ogni server di pubblicazione remoto supportato dal server di distribuzione locale. Questa tabella è archiviata nel database **msdb** .  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**nome**|**sysname**|Nome del server di pubblicazione remoto supportato dal server di distribuzione locale.|  
|**distribution_db**|**sysname**|Nome del database di distribuzione.|  
|**working_directory**|**nvarchar(255)**|Nome della directory di lavoro utilizzata per archiviare i file dei dati e di schema per la pubblicazione|  
|**security_mode**|**int**|Modalità di sicurezza implementata nel server di distribuzione.<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autenticazione 0.<br /><br /> **1** = autenticazione di Windows.|  
|**accesso**|**sysname**|ID dell'account di accesso per l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**password**|**nvarchar (524)**|Password (crittografata) per l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**active**|**bit**|Indica se il server di distribuzione locale viene utilizzato dal server di pubblicazione remoto.|  
|**trusted**|**bit**|Indica se il server di pubblicazione remoto utilizza la stessa password del server di distribuzione locale:<br /><br /> **0** = per la connessione al server di distribuzione è necessaria una password nel server di pubblicazione remoto.<br /><br /> **1** = non è necessaria alcuna password.|  
|**third_party**|**bit**|Indica se il server di pubblicazione è un computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installazione.** 1** = origine dati eterogenea.|  
|**publisher_type**|**sysname**|Tipo di server di pubblicazione:<br /><br /> **MSSQLSERVER**  =  MSSQLSERVER [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Pubblicazione.<br /><br /> **Oracle** = server di pubblicazione Oracle standard.<br /><br /> **Oracle Gateway** = server di pubblicazione Oracle Gateway.|  
|**storage_connection_string**|**nvarchar (779)**|Valore della stringa di connessione di archiviazione del database SQL di Azure.|  

  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
