---
description: Metodo Open (ADO MD)
title: Metodo Open (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Open
- Cellset::Open
helpviewer_keywords:
- Open method [ADO MD]
ms.assetid: a87d8080-a238-45e5-bc80-9a8625b3810f
author: rothja
ms.author: jroth
ms.openlocfilehash: 5c7b403ed89ae9933b4169af4e53921205318ccd
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88986232"
---
# <a name="open-method-ado-md"></a>Metodo Open (ADO MD)
Recupera i risultati di una query multidimensionale e restituisce i risultati a un tipo di [cella](./cellset-object-ado-md.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Cellset.Open Source, ActiveConnection  
```  
  
#### <a name="parameters"></a>Parametri  
 *Origine*  
 Facoltativa. **Variante** che restituisce una query multidimensionale valida, ad esempio una query MDX (Multidimensional Expression). L'argomento di *origine* corrisponde alla proprietà di [origine](./source-property-ado-md.md) . Per ulteriori informazioni su MDX, vedere la documentazione relativa alla [OLE DB per l'elaborazione analitica in linea (OLAP)](/previous-versions/windows/desktop/ms717005(v=vs.85)) in Microsoft Data Access Components SDK.  
  
 *ActiveConnection*  
 Facoltativa. **Variante** che restituisce una stringa che specifica un nome di variabile oggetto di [connessione](../ado-api/connection-object-ado.md) ADO o una definizione per una connessione. L'argomento *ActiveConnection* specifica la connessione in cui aprire l'oggetto [cellt](./cellset-object-ado-md.md) . Se si passa una definizione di connessione per questo argomento, ADO apre una nuova connessione usando i parametri specificati. L'argomento *ActiveConnection* corrisponde alla proprietà [ActiveConnection](./activeconnection-property-ado-md.md) .  
  
## <a name="remarks"></a>Osservazioni  
 Il metodo **Open** genera un errore se uno dei parametri viene omesso e il valore della proprietà corrispondente non è stato impostato prima di tentare di aprire il set di **celle**.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Cellset (ADO MD)](./cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di celle (VB)](./cellset-example-vb.md)   
 [Proprietà ActiveConnection (ADO MD)](./activeconnection-property-ado-md.md)   
 [Metodo Close (ADO MD)](./close-method-ado-md.md)   
 [Oggetto Connection (ADO)](../ado-api/connection-object-ado.md)   
 [Proprietà Source (ADO MD)](./source-property-ado-md.md)   
 [Proprietà State (ADO MD)](./state-property-ado-md.md)