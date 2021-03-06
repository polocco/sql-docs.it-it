---
description: Proprietà Count (ADO)
title: Proprietà Count (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Collection::Count
helpviewer_keywords:
- Count property [ADO]
ms.assetid: da9ccd1f-d402-41a2-940c-45556fc5340d
author: rothja
ms.author: jroth
ms.openlocfilehash: b478a9f88d33503c5eda98bda11cfe0e0fcc8d6b
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88974522"
---
# <a name="count-property-ado"></a>Proprietà Count (ADO)
Indica il numero di oggetti in una raccolta.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un valore **Long** .  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare la proprietà **count** per determinare il numero di oggetti in una raccolta specificata.  
  
 Poiché la numerazione per i membri di una raccolta inizia con zero, è consigliabile usare sempre i cicli di codice che iniziano con il membro zero e terminano con il valore della proprietà **count** meno 1. Se si utilizza Microsoft Visual Basic e si desidera scorrere i membri di una raccolta senza selezionare la proprietà **count** , utilizzare l'oggetto **for each... Comando successivo** .  
  
 Se la proprietà **count** è zero, nella raccolta non sono presenti oggetti.  
  
## <a name="applies-to"></a>Si applica a  

:::row:::
    :::column:::
        [Raccolta Axes (ADO MD)](../ado-md-api/axes-collection-ado-md.md)  
        [Raccolta Columns (ADOX)](../adox-api/columns-collection-adox.md)  
        [Raccolta CubeDefs (ADO MD)](../ado-md-api/cubedefs-collection-ado-md.md)  
        [Raccolta Dimensions (ADO MD)](../ado-md-api/dimensions-collection-ado-md.md)  
        [Raccolta Errors (ADO)](./errors-collection-ado.md)  
        [Raccolta Fields (ADO)](./fields-collection-ado.md)  
        [Raccolta di Groups (ADOX)](../adox-api/groups-collection-adox.md)  
    :::column-end:::
    :::column:::
        [Raccolta Hierarchies (ADO MD)](../ado-md-api/hierarchies-collection-ado-md.md)  
        [Raccolta Indexes (ADOX)](../adox-api/indexes-collection-adox.md)  
        [Raccolta Keys (ADOX)](../adox-api/keys-collection-adox.md)  
        [Raccolta Levels (ADO MD)](../ado-md-api/levels-collection-ado-md.md)  
        [Raccolta Members (ADO MD)](../ado-md-api/members-collection-ado-md.md)  
        [Raccolta Parameters (ADO)](./parameters-collection-ado.md)  
    :::column-end:::
    :::column:::
        [Raccolta Positions (ADO MD)](../ado-md-api/positions-collection-ado-md.md)  
        [Raccolta Procedures (ADOX)](../adox-api/procedures-collection-adox.md)  
        [Raccolta Properties (ADO)](./properties-collection-ado.md)  
        [Raccolta Tables (ADOX)](../adox-api/tables-collection-adox.md)  
        [Raccolta Users (ADOX)](../adox-api/users-collection-adox.md)  
        [Raccolta Views (ADOX)](../adox-api/views-collection-adox.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà Count (VB)](./count-property-example-vb.md)   
 [Esempio di proprietà Count (VC + +)](./count-property-example-vc.md)   
 [Metodo Refresh (ADO)](./refresh-method-ado.md)