---
description: sp_syscollector_upload_collection_set (Transact-SQL)
title: sp_syscollector_upload_collection_set (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_upload_collection_set
- sp_syscollector_upload_collection_set_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_upload_collection_set
- data collector [SQL Server], stored procedures
ms.assetid: eed9232c-2b0a-4b6a-8ba0-76b7c99f48dc
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 13c21075035a499b21bede95f28e5bf4a00a9161
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2020
ms.locfileid: "89534822"
---
# <a name="sp_syscollector_upload_collection_set-transact-sql"></a>sp_syscollector_upload_collection_set (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Avvia un caricamento di dati del set di raccolta se il set di raccolta è abilitato.  
  
> [!IMPORTANT]  
>  Questa stored procedure può essere utilizzata solo per i set di raccolta configurati per la raccolta e il caricamento dei dati in modalità memorizzata nella cache.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_syscollector_upload_collection_set [[ @collection_set_id = ] collection_set_id ]  
          , [[ @name = ] 'name' ]   
```  
  
## <a name="arguments"></a>Argomenti  
`[ @collection_set_id = ] collection_set_id` Identificatore locale univoco per il set di raccolta. *collection_set_id* è di **tipo int** e deve avere un valore se *Name* è null.  
  
`[ @name = ] 'name'` Nome del set di raccolta. *Name* è di **tipo sysname** e deve avere un valore se *collection_set_id* è null.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 Il *collection_set_id* o il *nome* deve avere un valore. entrambi non possono essere NULL.  
  
 Questa procedura può essere utilizzata per l'avvio di un caricamento su richiesta per un set di raccolta in esecuzione. La procedura può essere utilizzata solo per i set di raccolta configurati per la raccolta e il caricamento dei dati in modalità memorizzata nella cache. Questo consente a un utente di ottenere i dati da analizzare senza dover aspettare un caricamento pianificato.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per eseguire questa procedura, è richiesta l'appartenenza al ruolo predefinito del database **dc_operator** (con autorizzazione Execute).  
  
## <a name="example"></a>Esempio  
 Esegue un caricamento su richiesta di un set di raccolta denominato `Simple Collection Set`.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_upload_collection_set @name = 'Simple Collection Set' ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Raccolta dati](../../relational-databases/data-collection/data-collection.md)  
  
  
