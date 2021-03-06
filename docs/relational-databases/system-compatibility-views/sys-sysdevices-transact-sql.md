---
description: sys.sysdevices (Transact-SQL)
title: Dispositivi sys.sys(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdevices
- sysdevices_TSQL
- sys.sysdevices
- sys.sysdevices_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysdevices compatibility view
- sysdevices system table
ms.assetid: ac5bcaf4-8fb6-4855-8856-d7643f469361
author: rothja
ms.author: jroth
ms.openlocfilehash: 6bcc481e595dc2c061d736a6bee12da6d918b7e8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88419795"
---
# <a name="syssysdevices-transact-sql"></a>sys.sysdevices (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Contiene una riga per ogni file di backup su disco, di backup su nastro e di database.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**nome**|**sysname**|Nome logico del file di backup o di database.|  
|**size**|**int**|Dimensioni del file in pagine da 2 KB.|  
|**basso**|**int**|Supportata per compatibilità con le versioni precedenti.|  
|**alta**|**int**|Supportata per compatibilità con le versioni precedenti.|  
|**Stato**|**smallint**|Mappa di bit che indica il tipo di dispositivo:<br /><br /> 1 = disco predefinito<br /><br /> 2 = disco fisico<br /><br /> 4 = disco logico<br /><br /> 8 = ignora intestazione<br /><br /> 16 = file di backup<br /><br /> 32 = scritture in serie<br /><br /> 4096= sola lettura|  
|**cntrltype**|**smallint**|Tipo di controller:<br /><br /> 0 = file di database non CD-ROM<br /><br /> 2 = file di backup su disco<br /><br /> 3 - 4 = file di backup su dischetto<br /><br /> 5 = file di backup su nastro<br /><br /> 6 = file named pipe|  
|**phyname**|**nvarchar(260)**|Nome del file fisico.|  
  
## <a name="see-also"></a>Vedere anche  
 [Mapping di tabelle di sistema a viste di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Viste della compatibilità &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
