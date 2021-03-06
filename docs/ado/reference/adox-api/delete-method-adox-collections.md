---
description: Metodo Delete (raccolte ADOX)
title: Metodo Delete (raccolte ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Views::Delete
- Groups::Delete
- Indexes::raw_Delete
- Columns::raw_Delete
- Tables::Delete
- Keys::Delete
- Users::Delete
- Users::raw_Delete
- Keys::raw_Delete
- Procedures::raw_Delete
- Views::raw_Delete
- Indexes::Delete
- Procedures::Delete
- Groups::raw_Delete
- Tables::raw_Delete
- Columns::Delete
helpviewer_keywords:
- delete method [ADOX]
ms.assetid: e6b6e3a4-8952-4d79-81f4-51019c338374
author: rothja
ms.author: jroth
ms.openlocfilehash: e92cbe56bb7823b5c6cfd2485d887f3e3c56a8e5
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88984622"
---
# <a name="delete-method-adox-collections"></a>Metodo Delete (raccolte ADOX)
Rimuove un oggetto da una raccolta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Collection.Delete Name  
```  
  
#### <a name="parameters"></a>Parametri  
 *Nome*  
 **Variant** che specifica il nome o la posizione ordinale (indice) dell'oggetto da eliminare.  
  
## <a name="remarks"></a>Osservazioni  
 Si verificherà un errore se il *nome* non esiste nella raccolta.  
  
 Per le raccolte di [tabelle](./tables-collection-adox.md) e [utenti](./users-collection-adox.md) , si verificherà un errore se il provider non supporta rispettivamente l'eliminazione di tabelle o utenti. Per [le raccolte procedure](./procedures-collection-adox.md) e [viste](./views-collection-adox.md) , l' **eliminazione** avrà esito negativo se il provider non supporta la persistenza dei comandi.  
  
## <a name="applies-to"></a>Si applica a  

:::row:::
    :::column:::
        [Raccolta Columns (ADOX)](./columns-collection-adox.md)  
        [Raccolta di Groups (ADOX)](./groups-collection-adox.md)  
        [Raccolta Indexes (ADOX)](./indexes-collection-adox.md)  
    :::column-end:::
    :::column:::
        [Raccolta Keys (ADOX)](./keys-collection-adox.md)  
        [Raccolta Procedures (ADOX)](./procedures-collection-adox.md)  
        [Raccolta Tables (ADOX)](./tables-collection-adox.md)  
    :::column-end:::
    :::column:::
        [Raccolta Users (ADOX)](./users-collection-adox.md)  
        [Raccolta Views (ADOX)](./views-collection-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Vedere anche  
 [Esempio di metodo Delete delle procedure (VB)](./procedures-delete-method-example-vb.md)   
 [Esempio del metodo Delete di Views (VB)](./views-delete-method-example-vb.md)