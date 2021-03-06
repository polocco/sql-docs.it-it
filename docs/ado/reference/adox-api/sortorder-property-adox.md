---
description: Proprietà SortOrder (ADOX)
title: Proprietà SortOrder (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Column::SortOrder
- _Column::PutSortOrder
- _Column::put_SortOrder
- _Column::get_SortOrder
- _Column::GetSortOrder
helpviewer_keywords:
- SortOrder property [ADOX]
ms.assetid: 04510b19-9cb2-4895-b23b-f7790123eb04
author: rothja
ms.author: jroth
ms.openlocfilehash: 4141e657fd0c7dfcda2de38c33446bcb3e7a27a2
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88983312"
---
# <a name="sortorder-property-adox"></a>Proprietà SortOrder (ADOX)
Indica la sequenza di ordinamento per la colonna (solo colonne indice).  
  
## <a name="settings-and-return-values"></a>Impostazioni e valori restituiti  
 Imposta e restituisce un valore **Long** che può essere una delle costanti [SortOrderEnum](./sortorderenum.md) . Il valore predefinito è **adSortAscending**.  
  
## <a name="remarks"></a>Osservazioni  
 Questa proprietà si applica solo agli oggetti [Column](./column-object-adox.md) nella raccolta [Columns](./columns-collection-adox.md) di un [Indice](./index-object-adox.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Column (ADOX)](./column-object-adox.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà SortOrder (VB)](./sortorder-property-example-vb.md)   
 [Raccolta Columns (ADOX)](./columns-collection-adox.md)   
 [Oggetto Index (ADOX)](./index-object-adox.md)