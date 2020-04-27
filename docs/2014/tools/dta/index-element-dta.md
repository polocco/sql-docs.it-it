---
title: Elemento Index (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Index element (DTA)
ms.assetid: 447d3964-b387-40f6-9189-71386774c29e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 59650edbef55b7bb433c6003c9ddc0f203ca7c5e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "63229000"
---
# <a name="index-element-dta"></a>Index - elemento (DTA)
  Contiene informazioni su un indice che si desidera creare o eliminare per una configurazione specificata dall'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Recommendation>  
  <Create>  
    <Index [Clustered | Unique | Online | IndexSizeInMB | NumberOfRows             | QUOTED_IDENTIFIER | ARITHABORT | CONCAT_NULL_YIELDS_NULL             | ANSI_NULLS | ANSI_PADDING | ANSI_WARNINGS  
            | NUMERIC_ROUNDABORT]  
     ...code removed here...  
    </Index>  
```  
  
## <a name="element-attributes"></a>Attributi elemento  
  
|Attributo Index|Tipo di dati|Descrizione|  
|---------------------|---------------|-----------------|  
|`Clustered`|`boolean`|Facoltativo. Specifica un indice cluster. Impostare su "true" o "false", ad esempio:<br /><br /> `<Index Clustered="true">`<br /><br /> Per impostazione predefinita, questo attributo è impostato su "false".|  
|`Unique`|`boolean`|Facoltativo. Specifica un indice univoco. Impostare su "true" o "false", ad esempio:<br /><br /> `<Index Unique="true">`<br /><br /> Per impostazione predefinita, questo attributo è impostato su "false".|  
|`Online`|`boolean`|Facoltativa. Specifica un indice in grado di eseguire operazioni che richiedono spazio su disco temporaneo mentre il server è online. Impostare su "true" o "false", ad esempio:<br /><br /> `<Index Online="true">`<br /><br /> Per impostazione predefinita, questo attributo è impostato su "false".<br /><br /> Per altre informazioni, vedere [Perform Index Operations Online](../../relational-databases/indexes/perform-index-operations-online.md).|  
|`IndexSizeInMB`|`double`|Facoltativo. Specifica le dimensioni massime dell'indice in megabyte, ad esempio:<br /><br /> `<Index IndexSizeInMB="873.75">`<br /><br /> Nessuna impostazione predefinita.|  
|`NumberOfRows`|`integer`|Facoltativo. Simula diverse dimensioni di indice, che rispecchiano in maniera efficiente diverse dimensioni di tabella, ad esempio:<br /><br /> `<Index NumberOfRows="3000">`<br /><br /> Nessuna impostazione predefinita.|  
|`QUOTED_IDENTIFIER`|`boolean`|Facoltativo. Fa [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in modo che segua le regole ISO relative alle virgolette che delimitano gli identificatori e le stringhe letterali. È necessario attivare questo attributo se l'indice è definito in una colonna calcolata o in una vista. La sintassi seguente, ad esempio, consente di attivare l'attributo:<br /><br /> `<Index QUOTED_IDENTIFIER [...]>`<br /><br /> Per impostazione predefinita, l'attributo è disattivato.<br /><br /> Per altre informazioni, vedere [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql).|  
|`ARITHABORT`|`boolean`|Facoltativo. Interrompe una query quando si verifica un errore di divisione per zero o di overflow durante l'esecuzione della query stessa. È necessario attivare questo attributo se l'indice è definito in una colonna calcolata o in una vista. La sintassi seguente, ad esempio, consente di attivare l'attributo:<br /><br /> `<Index ARITHABORT [...]>`<br /><br /> Per impostazione predefinita, l'attributo è disattivato.<br /><br /> Per altre informazioni, vedere [SET ARITHABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-arithabort-transact-sql).|  
|`CONCAT_NULL_YIELDS_`<br /><br /> `NULL`|`boolean`|Facoltativa. Controlla se i risultati di concatenazione vengono considerati valori Null o stringhe vuote. È necessario attivare questo attributo se l'indice è definito in una colonna calcolata o in una vista. La sintassi seguente, ad esempio, consente di attivare l'attributo:<br /><br /> `<Index CONCAT_NULL_YIELDS_NULL [...]>`<br /><br /> Per impostazione predefinita, l'attributo è disattivato.<br /><br /> Per altre informazioni, vedere [SET CONCAT_NULL_YIELDS_NULL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-concat-null-yields-null-transact-sql).|  
|`ANSI_NULLS`|`boolean`|Facoltativo. Specifica il comportamento conforme allo standard ISO degli operatori di confronto uguale a (=) e diverso da (<>) quando questi vengono utilizzati con valori Null. È necessario attivare questo attributo se l'indice è definito in una colonna calcolata o in una vista. La sintassi seguente, ad esempio, consente di attivare l'attributo:<br /><br /> `<Index ANSI_NULLS [...]>`<br /><br /> Per impostazione predefinita, l'attributo è disattivato.<br /><br /> Per altre informazioni, vedere [SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql).|  
|`ANSI_PADDING`|`boolean`|Facoltativo. Controlla la modalità di archiviazione nella colonna dei valori di dimensioni minori rispetto alle dimensioni definite. È necessario attivare questo attributo se l'indice è definito in una colonna calcolata o in una vista. La sintassi seguente, ad esempio, consente di attivare l'attributo:<br /><br /> `<Index ANSI_PADDING [...]>`<br /><br /> Per impostazione predefinita, l'attributo è disattivato.<br /><br /> Per altre informazioni, vedere [SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql).|  
|`ANSI_WARNINGS`|`boolean`|Facoltativo. Specifica il funzionamento standard ISO in varie condizioni di errore. È necessario attivare questo attributo se l'indice è definito in una colonna calcolata o in una vista. La sintassi seguente, ad esempio, consente di attivare l'attributo:<br /><br /> `<Index ANSI_WARNING [...]>`<br /><br /> Per impostazione predefinita, l'attributo è disattivato.<br /><br /> Per altre informazioni, vedere [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-warnings-transact-sql).|  
|`NUMERIC_ROUNDABORT`|`boolean`|Facoltativo. Specifica il livello di segnalazione degli errori generato quando l'arrotondamento in un'espressione comporta una perdita di precisione. È necessario disattivare questo attributo se l'indice è definito in una colonna calcolata o in una vista.<br /><br /> La sintassi seguente consente di attivare questo attributo:<br /><br /> `<Index ANSI_WARNING [...]>`<br /><br /> Per impostazione predefinita, l'attributo è disattivato.<br /><br /> Per altre informazioni, vedere [SET NUMERIC_ROUNDABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-numeric-roundabort-transact-sql).|  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Nessuno.|  
|**Valore predefinito**|Nessuno.|  
|**Occorrenza**|Obbligatorio una sola volta per ogni elemento `Create` o `Drop` se non è specificata nessun'altra struttura di progettazione fisica tramite gli elementi `Statistics` o `Heap`.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento Create &#40;DTA&#41;](create-element-dta.md)<br /><br /> Elemento `Drop`. Per ulteriori informazioni, vedere l'XML Schema di Ottimizzazione guidata motore di database.|  
|**Elementi figlio**|[Elemento Name per Index &#40;DTA&#41;](name-element-for-index-dta.md)<br /><br /> [Elemento Column per Index &#40;DTA&#41;](column-element-for-index-dta.md)<br /><br /> Elemento `PartitionScheme`. Per ulteriori informazioni, vedere l'XML Schema di Ottimizzazione guidata motore di database.<br /><br /> Elemento `PartitionColumn`. Per ulteriori informazioni, vedere l'XML Schema di Ottimizzazione guidata motore di database.<br /><br /> [Elemento Filegroup per Index &#40;DTA&#41;](filegroup-element-for-index-dta.md)<br /><br /> Elemento `NumberOfReferences`. Per ulteriori informazioni, vedere l'XML Schema di Ottimizzazione guidata motore di database.<br /><br /> Elemento `PercentUsage`. Per ulteriori informazioni, vedere l'XML Schema di Ottimizzazione guidata motore di database.|  
  
## <a name="example"></a>Esempio  
 Per un esempio di questo elemento, vedere [Esempio di file di input XML con configurazione specificata dall'utente &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Vedi anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
