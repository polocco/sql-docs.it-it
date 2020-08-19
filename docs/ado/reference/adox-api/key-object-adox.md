---
description: Oggetto Key (ADOX)
title: Oggetto Key (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Key
helpviewer_keywords:
- Key object [ADOX]
ms.assetid: 55f116fe-4d56-4892-bffe-0cdd6fc727c9
author: rothja
ms.author: jroth
ms.openlocfilehash: d622adac64a37d956fc71ee1399c2d147b2f993a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88439863"
---
# <a name="key-object-adox"></a>Oggetto Key (ADOX)
Rappresenta un campo chiave primaria, esterna o univoca di una tabella di database.  
  
## <a name="remarks"></a>Osservazioni  
 Il codice seguente crea una nuova **chiave**:  
  
```  
Dim obj As New Key  
```  
  
 Con le proprietà e le raccolte di un oggetto **chiave** , è possibile:  
  
-   Identificare la chiave con la proprietà [Name](../../../ado/reference/adox-api/name-property-adox.md) .  
  
-   Determinare se la chiave è primaria, esterna o univoca con la proprietà [Type](../../../ado/reference/adox-api/type-property-key-adox.md) .  
  
-   Accedere alle colonne di database della chiave con la raccolta [Columns](../../../ado/reference/adox-api/columns-collection-adox.md) .  
  
-   Specificare il nome della tabella correlata con la proprietà [RelatedTable](../../../ado/reference/adox-api/relatedtable-property-adox.md) .  
  
-   Determinare l'azione eseguita per l'eliminazione o l'aggiornamento di una chiave primaria con le proprietà [DeleteRule](../../../ado/reference/adox-api/deleterule-property-adox.md) e [UpdateRule](../../../ado/reference/adox-api/updaterule-property-adox.md) .  
  
 Questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi dell'oggetto Key](../../../ado/reference/adox-api/key-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà Method Append, Key Type, RelatedColumn, RelatedTable e UpdateRule (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [Raccolta Columns (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Raccolta di oggetti Key (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)
