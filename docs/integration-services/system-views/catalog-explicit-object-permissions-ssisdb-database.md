---
description: catalog.explicit_object_permissions (database SSISDB)
title: catalog.explicit_object_permissions (database SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 49b09e0f-06e8-451f-b979-a0d91000bfe3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e7052caddf7087239e734d6474c4d829f13e9948
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88422085"
---
# <a name="catalogexplicit_object_permissions-ssisdb-database"></a>catalog.explicit_object_permissions (database SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Vengono visualizzate solo le autorizzazioni assegnate in modo esplicito all'utente.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|object_type|**smallint**|Tipo di oggetto a protezione diretta. Nei tipi di oggetti a protezione diretta sono inclusi cartelle (`1`), progetti (`2`), ambienti (`3`) e operazioni (`4`).|  
|object_id|**bigint**|Identificatore (ID) univoco o chiave primaria dell'oggetto protetto.|  
|principal_id|**int**|ID dell'entità di database.|  
|permission_type|**smallint**|Tipo di autorizzazione.|  
|is_deny|**bit**|Viene indicato se l'autorizzazione è stata negata o concessa. Quando il valore è `1`, l'autorizzazione è stata negata. In caso contrario, il valore è `0`.|  
|grantor_id|**int**|ID dell'entità a cui è stata concessa l'autorizzazione.|  
  
## <a name="remarks"></a>Osservazioni  
 In questa vista vengono visualizzati i tipi di autorizzazione elencati nella tabella seguente:  
  
|Valore di permission_type|Nome dell'autorizzazione|Descrizione dell'autorizzazione|Tipi di oggetti applicabili|  
|----------------------------|---------------------|----------------------------|-----------------------------|  
|`1`|READ|Consente all'entità di leggere le informazioni considerate parte dell'oggetto, ad esempio le proprietà. Non consente all'entità di enumerare o leggere il contenuto di altri oggetti inseriti all'interno dell'oggetto.|Cartella, progetto, ambiente, operazione|  
|`2`|MODIFY|Consente all'entità di modificare le informazioni considerate parte dell'oggetto, ad esempio le proprietà. Non consente all'entità di modificare gli altri oggetti contenuti all'interno dell'oggetto.|Cartella, progetto, ambiente, operazione|  
|`3`|EXECUTE|Consente all'entità di eseguire tutti i pacchetti nel progetto.|Project|  
|`4`|MANAGE_PERMISSIONS|Consente all'entità di assegnare autorizzazioni agli oggetti.|Cartella, progetto, ambiente, operazione|  
|`100`|CREATE_OBJECTS|Consente all'entità di creare oggetti nella cartella.|Cartella|  
|`101`|READ_OBJECTS|Consente all'entità di leggere tutti gli oggetti nella cartella.|Cartella|  
|`102`|MODIFY_OBJECTS|Consente all'entità di modificare tutti gli oggetti nella cartella.|Cartella|  
|`103`|EXECUTE_OBJECTS|Consente all'entità di eseguire tutti i pacchetti di tutti i progetti contenuti nella cartella.|Cartella|  
|`104`|MANAGE_OBJECT_PERMISSIONS|Consente all'entità di gestire le autorizzazioni su tutti gli oggetti nella cartella.|Cartella|  
  
## <a name="permissions"></a>Autorizzazioni  
 In questa vista non sono riportate tutte le autorizzazioni per l'entità corrente. L'utente deve controllare anche se l'entità è membro di ruoli e gruppi a cui sono state assegnate autorizzazioni.  
  
  
