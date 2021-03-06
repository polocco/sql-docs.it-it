---
description: Metodo Close (ADO MD)
title: Metodo Close (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Close
- Cellset::Close
helpviewer_keywords:
- Close method [ADO MD]
ms.assetid: a3aa594d-f9d4-4654-8625-ec20153ff5d9
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f4f0c1613b1ca0e33a4f325dbe3e326d56f76e6
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88987112"
---
# <a name="close-method-ado-md"></a>Metodo Close (ADO MD)
Chiude un celle aperto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Cellset.Close  
```  
  
## <a name="remarks"></a>Osservazioni  
 Se si utilizza il metodo **Close** per chiudere un oggetto di un [celle](./cellset-object-ado-md.md) , i dati associati vengono rilasciati, inclusi i dati in tutti gli oggetti [Cell](./cell-object-ado-md.md), [Axis](./axis-object-ado-md.md), [position](./position-object-ado-md.md)o [member](./member-object-ado-md.md) correlati. La chiusura di un **celle** non viene rimossa dalla memoria; è possibile modificare le impostazioni delle proprietà e riaprirle in un secondo momento. Per eliminare completamente un oggetto dalla memoria, impostare la variabile oggetto su **Nothing**.  
  
 In un secondo momento è possibile chiamare il metodo [Open](./open-method-ado-md.md) per riaprire il **cellt** usando la stessa stringa di origine o un'altra. Mentre l'oggetto di **celle** è chiuso, il recupero di qualsiasi proprietà o la chiamata di metodi che fanno riferimento ai dati o ai metadati sottostanti genera un errore.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Cellset (ADO MD)](./cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Axis (ADO MD)](./axis-object-ado-md.md)   
 [Oggetto Cell (ADO MD)](./cell-object-ado-md.md)   
 [Oggetto member (ADO MD)](./member-object-ado-md.md)   
 [Metodo Open (ADO MD)](./open-method-ado-md.md)   
 [Oggetto Position (ADO MD)](./position-object-ado-md.md)   
 [Proprietà State (ADO MD)](./state-property-ado-md.md)