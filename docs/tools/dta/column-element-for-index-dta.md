---
title: Elemento Column per Index (DTA)
description: Nell'utilità dta l'elemento Column per Index specifica le colonne sulle quali viene creato l'indice per una configurazione specificata dall'utente.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Column element
ms.assetid: ba9fac20-26bd-4333-940e-842c15241b46
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/09/2017
ms.openlocfilehash: 02900685d93eef62553d830494d25ec83ca83ce1
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831628"
---
# <a name="column-element-for-index-dta"></a>Elemento Column per Index (DTA)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Specifica le colonne sulle quali viene creato l'indice per una configurazione specificata dall'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Create>  
  <Index>  
    <Name>...</Name>  
    <Column [Type | SortOrder]>  
     ...code removed here...  
     </Column>  
```  
  
## <a name="element-attributes"></a>Attributi elemento  
  
 **Tipo**: Facoltativa. Specifica il tipo di colonna dell'indice. Usare un tipo di dati **string** per specificare questo attributo con uno dei valori consentiti seguenti:  
  
-   **KeyColumn**  
  
     Specifica che alla colonna viene fatto riferimento mediante una chiave di indice. Per impostare questo attributo, utilizzare la sintassi seguente:  
  
    ```  
    <Column Type="KeyColumn">  
    ```  
  
     Per altre informazioni sulle colonne chiave, vedere [Descrizione di indici cluster e non cluster](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md).  
  
-   **IncludedColumn**  
  
     Specifica che la colonna è una colonna inclusa, anziché una colonna chiave. Per impostare questo attributo, utilizzare la sintassi seguente:  
  
    ```  
    <Column Type="IncludedColumn">  
    ```  
  
     Per altre informazioni sulle colonne incluse, vedere [Creare indici con colonne incluse](../../relational-databases/indexes/create-indexes-with-included-columns.md).  
  
 **SortOrder**: Facoltativa. Specifica l'ordinamento della colonna. Usare un tipo di dati **string** per specificare un ordinamento **"Ascending"** o **"Descending"** come segue:  
  
```  
<Column SortOrder="Ascending">  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|No.|  
|**Valore predefinito**|No.|  
|**Occorrenza**|È possibile specificare un massimo di 1024 colonne per l'elemento **Index** .|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento Index &#40;DTA&#41;](../../tools/dta/index-element-dta.md)|  
|**Elementi figlio**|[Elemento Name per Column &#40;DTA&#41;](../../tools/dta/name-element-for-column-dta.md)|  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo di questo elemento, vedere [Esempio di file di input XML con configurazione specificata dall'utente &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML&#40; (Ottimizzazione guidata motore di database)&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
