---
description: sysmergesubsetfilters (Transact-SQL)
title: sysmergesubsetfilters (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysmergesubsetfilters
- sysmergesubsetfilters_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergesubsetfilters system table
ms.assetid: f91d1c6c-3132-47f6-926c-88f56848cafe
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 932a237037073f81564b9a5f1a2cba89ba4d892b
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2020
ms.locfileid: "89542854"
---
# <a name="sysmergesubsetfilters-transact-sql"></a>sysmergesubsetfilters (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Contiene informazioni sui filtri di join per gli articoli partizionati. Questa tabella è archiviata nei database di pubblicazione e di sottoscrizione.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**NomeFiltro**|**sysname**|Nome del filtro utilizzato per creare l'articolo.|  
|**join_filterid**|**int**|ID dell'oggetto che rappresenta il filtro join.|  
|**pubid**|**uniqueidentifier**|ID della pubblicazione.|  
|**artid**|**uniqueidentifier**|ID dell'articolo.|  
|**art_nickname**|**int**|Nome alternativo dell'articolo.|  
|**join_articlename**|**sysname**|Nome della tabella da unire in join per determinare l'appartenenza della riga.|  
|**join_nickname**|**int**|Nome alternativo della tabella da unire in join per determinare l'appartenenza della riga.|  
|**join_unique_key**|**int**|Indica un join su una chiave univoca di **join_tablename**:<br /><br /> 0 = diverso da chiave univoca.<br /><br /> 1 = chiave univoca.|  
|**expand_proc**|**sysname**|Nome della stored procedure utilizzata dall'agente di merge per l'identificazione delle righe da inviare o rimuovere da un Sottoscrittore.|  
|**join_filterclause**|**nvarchar (1000)**|Clausola di filtro utilizzata per il join.|  
|**filter_type**|**tinyint**|Specifica il tipo di filtro. Può essere uno dei tipi seguenti:<br /><br /> 1 = filtro join.<br /><br /> 2 = collegamento di record logico.<br /><br /> 3 = filtro join e collegamento di record logico.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
