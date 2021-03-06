---
description: MSpublisher_databases (Transact-SQL)
title: MSpublisher_databases (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpublisher_databases
- MSpublisher_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpublisher_databases system table
ms.assetid: 59b0166e-a64c-46b8-befc-c222fa1ccce2
author: markingmyname
ms.author: maghan
ms.openlocfilehash: caba0fa6bf5bee0d00b182a82fc2add0c5061720
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2020
ms.locfileid: "89550979"
---
# <a name="mspublisher_databases-transact-sql"></a>MSpublisher_databases (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  La tabella **MSpublisher_databases** contiene una riga per ogni coppia server di pubblicazione/database di pubblicazione gestita dal server di distribuzione locale. Questa tabella è archiviata nel database di distribuzione.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|ID del server di pubblicazione.|  
|**publisher_db**|**sysname**|Nome del database del server di pubblicazione.|  
|**id**|**int**|ID della riga|  
|**publisher_engine_edition**|**int**|L'edizione del server di pubblicazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], che può essere una delle seguenti:<br /><br /> **10** = Personal Edition<br /><br /> **11** = Desktop Engine (MSDE)<br /><br /> **20** = standard<br /><br /> **21** = gruppo di lavoro<br /><br /> **30** = Enterprise (valutazione)<br /><br /> **31** = sviluppatore<br /><br /> **40** = Express (Express non può essere un server di pubblicazione. Questo valore è presente per motivi di completezza).|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
