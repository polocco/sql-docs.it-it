---
description: sys.database_usage (Database di SQL Azure)
title: sys.database_usage (database SQL di Azure) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- database_usage
- database_usage_TSQL
- sys.database_usage_TSQL
- sys.database_usage
dev_langs:
- TSQL
helpviewer_keywords:
- database_usage
- sys.database_usage
ms.assetid: be6820de-60bf-4ddd-ace7-4077893d630f
author: julieMSFT
ms.author: jrasnick
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: f0c8809138bfad5cc9b7c4866978e7f2c111e09a
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2020
ms.locfileid: "91809209"
---
# <a name="sysdatabase_usage-azure-sql-database"></a>sys.database_usage (Database di SQL Azure)
[!INCLUDE[Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/asdb-asdbmi.md)]

  **Nota: questa opzione si applica solo al database SQL di Azure V11.**  
  
 Elenca il numero, il tipo e la durata dei database nel [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Server.  
  
 La vista **sys.database_usage** contiene le colonne seguenti.  
  
|Nome colonna|Descrizione|  
|-----------------|-----------------|  
|time|Data di esecuzione degli eventi di utilizzo.|  
|sku|Tipo di livello di servizio per il database: **Web**, **Business**, **Basic**, **standard**, **Premium**|  
|quantity|Numero massimo di database di un tipo SKU presente durante il giorno.|  
  
## <a name="permissions"></a>Autorizzazioni  
 L'accesso in sola lettura a questa vista è disponibile per tutti gli utenti che dispongono delle autorizzazioni per connettersi al database **Master** .  
  
## <a name="remarks"></a>Osservazioni  
 La visualizzazione **sys.database_usage** restituisce una riga per ogni giorno della sottoscrizione.  
  
## <a name="see-also"></a>Vedere anche  
 [Dettagli prezzi del database SQL](https://go.microsoft.com/fwlink/?LinkID=394978)   
 [Account e fatturazione nel database SQL di Azure](/previous-versions/azure/ee621788(v=azure.100))  
  
