---
description: DOMAIN_CONSTRAINTS (Transact-SQL)
title: DOMAIN_CONSTRAINTS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- DOMAIN_CONSTRAINTS
- DOMAIN_CONSTRAINTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.DOMAIN_CONSTRAINTS view
- DOMAIN_CONSTRAINTS view
ms.assetid: 436c4480-f1e3-403f-b2bd-de04539afe3c
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 23ac7070651eb3422ded15d674dc520ee7495974
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2020
ms.locfileid: "89529954"
---
# <a name="domain_constraints-transact-sql"></a>DOMAIN_CONSTRAINTS (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Restituisce una riga per ogni tipo di dati alias nel database corrente a cui è associata una regola e a cui può accedere l'utente corrente.  
  
 Per recuperare informazioni da queste viste, specificare il nome completo del **INFORMATION_SCHEMA.** _view_name_.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**CONSTRAINT_CATALOG**|**nvarchar (** 128 **)**|Database in cui esiste la regola.|  
|**CONSTRAINT_SCHEMA**|**nvarchar (** 128 **)**|Nome dello schema che contiene il vincolo.<br /><br /> Importante non utilizzare viste INFORMATION_SCHEMA per determinare lo schema di un oggetto. <strong> \* \* \* \* </strong> INFORMATION_SCHEMA visualizzazioni rappresentano solo un subset dei metadati di un oggetto. L'unica modalità affidabile per cercare lo schema di un oggetto consiste nell'eseguire una query sulla vista del catalogo sys.objects.|  
|**CONSTRAINT_NAME**|**sysname**|Nome della regola.|  
|**DOMAIN_CATALOG**|**nvarchar (** 128 **)**|Database in cui è incluso il tipo di dati alias.|  
|**DOMAIN_SCHEMA**|**nvarchar (** 128 **)**|Nome dello schema che include il tipo di dati alias.<br /><br /> Importante non utilizzare viste INFORMATION_SCHEMA per determinare lo schema di un tipo di dati. <strong> \* \* \* \* </strong> L'unica modalità affidabile per cercare lo schema di un tipo consiste nell'utilizzare la funzione TYPEPROPERTY.|  
|**DOMAIN_NAME**|**sysname**|Tipo di dati alias.|  
|**IS_DEFERRABLE**|**varchar (** 2 **)**|Specifica se è possibile posticipare la verifica dei vincoli. Restituisce sempre NO.|  
|**INITIALLY_DEFERRED**|**varchar (** 2 **)**|Specifica se la verifica dei vincoli viene inizialmente posticipata. Restituisce sempre NO.|  
  
## <a name="see-also"></a>Vedere anche  
 [Viste di sistema &#40;&#41;Transact-SQL ](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Viste degli schemi delle informazioni &#40;&#41;Transact-SQL ](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)  
  
  
