---
description: Proprietà Type (Stream - ADO)
title: Proprietà Type (flusso ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Type
- _Stream::get_Type
- _Stream::put_Type
helpviewer_keywords:
- Type property [ADO Stream]
ms.assetid: f6a17e8c-7a28-48d0-bded-76b9e0cf7639
author: rothja
ms.author: jroth
ms.openlocfilehash: a72fb3afba9ff1455cba3fde8ada4cf82cb6cd3d
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88988302"
---
# <a name="type-property-ado-stream"></a>Proprietà Type (Stream - ADO)
Indica il tipo di dati contenuti nel [flusso](./stream-object-ado.md) (binario o testo).  
  
## <a name="settings-and-return-values"></a>Impostazioni e valori restituiti  
 Imposta o restituisce un valore [StreamTypeEnum](./streamtypeenum.md) che specifica il tipo di dati contenuti nell'oggetto **flusso** . Il valore predefinito è **adTypeText**. Tuttavia, se inizialmente i dati binari vengono scritti in un nuovo **flusso**vuoto, il **tipo** verrà modificato in **adTypeBinary**.  
  
## <a name="remarks"></a>Osservazioni  
 La proprietà **Type** è di lettura/scrittura solo quando la posizione corrente si trova all'inizio del **flusso** ([position](./position-property-ado.md) è 0) e di sola lettura in qualsiasi altra posizione.  
  
 La proprietà**Type** determina i metodi da utilizzare per la lettura e la scrittura del **flusso**. Per i **flussi**di testo, usare [READTEXT](./readtext-method.md) e [WRITETEXT](./writetext-method.md). Per i **flussi**binari, usare [lettura](./read-method.md) e [scrittura](./write-method.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Stream (ADO)](./stream-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà RecordType (ADO)](./recordtype-property-ado.md)   
 [Proprietà Type (ADO)](./type-property-ado.md)