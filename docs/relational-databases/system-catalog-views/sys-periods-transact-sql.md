---
description: sys. periods (Transact-SQL)
title: sys. periods (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 25e66ed3-2270-4c5c-9f5a-2c0f165a57ca
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c091649234826080054de942ed96272055a1b595
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2020
ms.locfileid: "91810324"
---
# <a name="sysperiods-transact-sql"></a>sys. periods (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Restituisce una riga per ogni tabella per cui sono stati definiti periodi.  
  
|Intestazione della colonna|Tipo di dati|Descrizione|  
|-------------------|---------------|-----------------|  
|name|**sysname**|Nome del periodo|  
|period_type|**tinyint**|Valore numerico che rappresenta il tipo di periodo:<br /><br /> 1 = periodo di tempo di sistema|  
|period_type_desc|**nvarchar(60)**|Descrizione testuale del tipo di colonna:<br /><br /> SYSTEM_TIME_PERIOD|  
|object_id|**int**|ID della tabella contenente la colonna period_type|  
|start_column_id|**int**|ID della colonna che definisce il limite del periodo inferiore|  
|end_column_id|**int**|ID della colonna che definisce il limite del periodo superiore|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste di sistema &#40;&#41;Transact-SQL ](../../t-sql/language-reference.md)   
 [Viste del catalogo dell'oggetto &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.all_columns &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.system_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-system-columns-transact-sql.md)   
 [Domande frequenti sull'esecuzione di query sul catalogo di sistema SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Tabelle temporali](../../relational-databases/tables/temporal-tables.md)  
  
