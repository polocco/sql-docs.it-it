---
title: sys. dm_pdw_component_health_status (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 68cc3f7a-693c-4d5d-a76b-455352af8d7f
author: stevestein
ms.author: sstein
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 51e364650f8b8f8dae386126bdc820f9c72e571c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "67899515"
---
# <a name="sysdm_pdw_component_health_status-transact-sql"></a>sys. dm_pdw_component_health_status (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Include informazioni sull'integrità corrente dei componenti dell'appliance.  
  
|Nome colonna|Tipo di dati|Descrizione|Range|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**||Non NULL|  
|component_id|INT|ID del componente. Vedere [sys. pdw_health_components &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).<br /><br /> pdw_node_id, component_id, property_id e component_instance_id formano la chiave per questa visualizzazione.|Non NULL|  
|property_id|**int**|ID della proprietà. Vedere [sys. pdw_health_component_properties &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-pdw-health-component-properties-transact-sql.md).|NOT NULL|  
|component_instance_id|**nvarchar(255)**|Identifica un'istanza di un componente. Ad esempio, un'istanza di una CPU può essere identificata da component_instance_id =' CPU1'.<br /><br /> pdw_node_id, component_id, property_id e component_instance_id formano la chiave per questa visualizzazione.|NOT NULL|  
|property_value|**nvarchar(255)**|Valore della proprietà corrente.|NULL|  
|update_time|**datetime**|Data e ora dell'ultimo aggiornamento della metrica.|NOT NULL|  
  
## <a name="see-also"></a>Vedi anche  
 [SQL Data Warehouse e Parallel data warehouse viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
