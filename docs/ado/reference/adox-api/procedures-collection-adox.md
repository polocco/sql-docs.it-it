---
description: Raccolta Procedures (ADOX)
title: Raccolta Procedures (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Procedures
- Catalog::Procedures
helpviewer_keywords:
- Procedures collection [ADOX]
ms.assetid: dc7a38e1-93b9-4034-9af2-ff419e8fb2a3
author: rothja
ms.author: jroth
ms.openlocfilehash: b3f98420fc85cabd2ccc584817ac6ca9a9203081
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88983572"
---
# <a name="procedures-collection-adox"></a>Raccolta Procedures (ADOX)
Contiene tutti gli oggetti [procedure](./procedure-object-adox.md) di un catalogo.  
  
## <a name="remarks"></a>Osservazioni  
 Il metodo [Append](./append-method-adox-procedures.md) per una raccolta **Procedures** è univoco per ADOX. È possibile:  
  
-   Aggiungere una nuova routine alla raccolta con il metodo **Append** .  
  
 Le proprietà e i metodi rimanenti sono standard per le raccolte ADO. È possibile:  
  
-   Accedere a una routine della raccolta con la proprietà [Item](../ado-api/item-property-ado.md) .  
  
-   Restituisce il numero di routine contenute nella raccolta con la proprietà [count](../ado-api/count-property-ado.md) .  
  
-   Rimuovere una routine dalla raccolta con il metodo [Delete](./delete-method-adox-collections.md) .  
  
-   Aggiornare gli oggetti della raccolta in modo che corrispondano allo schema del database corrente con il metodo [Refresh](../ado-api/refresh-method-ado.md) .  
  
 Questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi della raccolta Indexes](./indexes-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà Command e CommandText (VB)](./command-and-commandtext-properties-example-vb.md)   
 [Raccolta Parameters, esempio di proprietà Command (VB)](./parameters-collection-command-property-example-vb.md)   
 [Esempio di metodo Append di procedure (VB)](./procedures-append-method-example-vb.md)   
 [Esempio di metodo Delete delle procedure (VB)](./procedures-delete-method-example-vb.md)   
 [Esempio di metodo Refresh di Procedures (VB)](./procedures-refresh-method-example-vb.md)   
 [Proprietà, metodi ed eventi della raccolta Procedures](./procedures-collection-properties-methods-and-events.md)   
 [Oggetto Catalog (ADOX)](./catalog-object-adox.md)   
 [Oggetto Procedure (ADOX)](./procedure-object-adox.md)