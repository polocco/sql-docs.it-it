---
title: Proprietà DateCreated (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Table::get_DateCreated
- _Table::DateCreated
- _Table::GetDateCreated
helpviewer_keywords:
- DateCreated property [ADOX]
ms.assetid: 2bf4b00d-045c-444e-8af7-8af6297ed418
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0151b6388a19fc95227cbfa55a571e0a797d0acc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "67966579"
---
# <a name="datecreated-property-adox"></a>Proprietà DateCreated (ADOX)
Indica la data di creazione dell'oggetto.  
  
## <a name="return-values"></a>Valori restituiti  
 Restituisce un valore **Variant** che specifica la data di creazione. Il valore è null se **DateCreated** non è supportato dal provider.  
  
## <a name="remarks"></a>Osservazioni  
 La proprietà **DateCreated** è null per gli oggetti appena accodati. Dopo aver accodato una nuova [vista](../../../ado/reference/adox-api/view-object-adox.md) o [routine](../../../ado/reference/adox-api/procedure-object-adox.md), è necessario chiamare il metodo [Refresh](../../../ado/reference/ado-api/refresh-method-ado.md) della raccolta [views](../../../ado/reference/adox-api/views-collection-adox.md) o [Procedures](../../../ado/reference/adox-api/procedures-collection-adox.md) per ottenere i valori per la proprietà **DateCreated** .  
  
## <a name="applies-to"></a>Si applica a  
  
||||  
|-|-|-|  
|[Oggetto Procedure (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Oggetto Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[Oggetto View (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà DateCreated e DateModified (VB)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [Proprietà DateModified (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md)
