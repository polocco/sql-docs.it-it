---
description: sp_xtp_flush_temporal_history (Transact-SQL)
title: sp_xtp_flush_temporal_history | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sp_xtp_flush_temporal_history
- sp_xtp_flush_temporal_history_TSQL
- sys.sp_xtp_flush_temporal_history
- sys.sp_xtp_flush_temporal_history_TSQL
helpviewer_keywords:
- sp_xtp_flush_temporal_history
ms.assetid: 322e3170-93f8-468a-a123-104ce7bd7fad
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7c22e02aba01530059357b709a0c72be350ec7de
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2020
ms.locfileid: "89544693"
---
# <a name="sp_xtp_flush_temporal_history-transact-sql"></a>sp_xtp_flush_temporal_history (Transact-SQL)

[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

  Richiama l'attività di scaricamento dati per spostare tutte le righe di cui è stato eseguito il commit dalla tabella di staging in memoria alla tabella di cronologia basata su disco.  

 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sys.sp_xtp_flush_temporal_history @schema_name, @object_name  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *\@schema_name*  
 Nome dello schema per la tabella corrente o temporale  
  
 *\@object_name*  
 Nome della tabella corrente o temporale  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 0 (esito positivo) o >0 (esito negativo)  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede autorizzazioni db_owner.  
  
## <a name="see-also"></a>Vedere anche  
 [Considerazioni sulle prestazioni con le tabelle temporali con controllo delle versioni di sistema e ottimizzazione per la memoria](../../relational-databases/tables/memory-optimized-system-versioned-temporal-tables-performance.md)  
  
  
