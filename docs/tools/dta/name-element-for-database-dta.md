---
title: Elemento Name per Database (DTA)
description: Nell'utilità dta l'elemento Name per Database specifica il nome del database che si vuole ottimizzare.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Name element
ms.assetid: e871c4fa-3b57-46cf-b4f8-e3be86f92dc4
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 5bf14c3057fa2268e879e9dd2f39f287f1364f95
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85775046"
---
# <a name="name-element-for-database-dta"></a>Elemento Name per Database (DTA)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Specifica il nome del database che si desidera ottimizzare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Server>  
    <Database>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|**string**, lunghezza illimitata.|  
|**Valore predefinito**|No.|  
|**Occorrenza**|Obbligatorio una volta per ogni elemento di **Database** .|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento Database per Server &#40;DTA&#41;](../../tools/dta/database-element-for-server-dta.md)|  
|**Elementi figlio**|No.|  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo di questo elemento, vedere [Elemento Server &#40;DTA&#41;](../../tools/dta/server-element-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML&#40; (Ottimizzazione guidata motore di database)&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
