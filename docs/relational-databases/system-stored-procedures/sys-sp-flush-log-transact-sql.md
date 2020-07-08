---
title: sys. sp_flush_log (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_flush_log_TSQL
- sys.sp_flush_log
- sys.sp_flush_log_TSQL
- sp_flush_log
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_flush_log
ms.assetid: 75cc9f52-3b1f-4754-b1e7-ce0dd3323bc9
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: cbcb731a4396829b38596619e4b52babcb6f9425
ms.sourcegitcommit: 703968b86a111111a82ef66bb7467dbf68126051
ms.contentlocale: it-IT
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052721"
---
# <a name="syssp_flush_log-transact-sql"></a>sys.sp_flush_log (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Scarica su disco il log delle transazioni del database corrente, finalizzando in questo modo tutte le transazioni durevoli posticipate sottoposte a commit in precedenza.  
  
 Se si sceglie di utilizzare la durabilità delle transazioni posticipate a causa dei vantaggi a livello di prestazioni, ma si desidera disporre anche di un limite garantito sulla quantità di dati che vengono persi per un arresto anomalo del server o per un failover, eseguire `sys.sp_flush_log` regolarmente. Se, ad esempio, si desidera assicurarsi di non perdere più di x secondi di dati, è necessario eseguire `sp_flush_log` ogni x secondi.  
  
 L'esecuzione di `sys.sp_flush_log` garantisce che tutte le transazioni durevoli posticipate sottoposte a commit in precedenza vengono rese durevoli. Per ulteriori informazioni, vedere l'argomento concettuale [controllo della durabilità delle transazioni](../../relational-databases/logs/control-transaction-durability.md) .  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
  
sys.sp_flush_log  
  
```  
  
#### <a name="parameters"></a>Parametri  
 No.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 Un codice restituito pari a 1 indica esito positivo.  Qualsiasi altro valore indica esito negativo.  
  
## <a name="result-sets"></a>Set di risultati  
 No.  
  
## <a name="sample-code"></a>Codice di esempio  
  
```sql  
.  
EXECUTE sys.sp_flush_log  
  
```  
  
  
