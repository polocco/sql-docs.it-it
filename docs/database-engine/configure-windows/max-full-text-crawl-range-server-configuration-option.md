---
title: Opzione di configurazione del server max full-text crawl range | Microsoft Docs
description: Informazioni sull'opzione "max full-text crawl range". Scoprire come ottimizza l'uso della CPU di SQL Server per migliorare le prestazioni della ricerca per indicizzazione durante una ricerca per indicizzazione completa.
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- crawls [full-text search]
- max full-text crawl range option
ms.assetid: a49de86b-0891-4dcd-89c0-ead30aab00e0
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 73a6223467b2da09d26e351c2cf2eb1a12576d80
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85680841"
---
# <a name="max-full-text-crawl-range-server-configuration-option"></a>Opzione di configurazione del server max full-text crawl range
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  L'opzione **max full-text crawl range** consente di ottimizzare l'utilizzo della CPU, migliorando quindi le prestazioni della ricerca per indicizzazione completa. L'opzione consente di specificare il numero di partizioni usate da [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durante una ricerca per indicizzazione completa. Se, ad esempio, sono presenti più CPU il cui utilizzo non è ottimizzato, è possibile aumentare il valore massimo dell'opzione. Oltre a questa opzione, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizza diversi altri elementi, ad esempio il numero di righe nella tabella e il numero di CPU, per determinare il numero effettivo di partizioni utilizzate.  
  
 Il valore predefinito per questa opzione è 4, il valore minimo è 1 e il valore massimo è 256. Le modifiche apportate a questa opzione influiscono solo sulle ricerche per indicizzazione successive. Le ricerche per indicizzazione in corso non sono interessate da una modifica apportata all'impostazione dell'opzione.  
  
 L'opzione **max full-text crawl range** è un'opzione avanzata. Se si usa la stored procedure di sistema **sp_configure** per modificare l'impostazione, è possibile modificare **max full-text crawl range** solo quando il valore di **show advanced options** è impostato su 1. L'impostazione diventa effettiva immediatamente e non richiede il riavvio del server.  
  
## <a name="see-also"></a>Vedere anche  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
