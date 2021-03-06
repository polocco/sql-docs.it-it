---
description: Metodo Seek
title: Metodo Seek | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset21::Seek
- Recordset21::raw_Seek
helpviewer_keywords:
- Seek method [ADO]
ms.assetid: 129293d2-19d3-4940-bf64-483ee72fb4a1
author: rothja
ms.author: jroth
ms.openlocfilehash: 3b2058751177d0498e89d1f9bd631a3151490c9d
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989162"
---
# <a name="seek-method"></a>Metodo Seek
Esegue una ricerca nell'indice di un [Recordset](./recordset-object-ado.md) per individuare rapidamente la riga che corrisponde ai valori specificati e imposta la posizione della riga corrente su quella riga.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
recordset.Seek KeyValues, SeekOption  
```  
  
#### <a name="parameters"></a>Parametri  
 *KeyValues*  
 Matrice di valori **Variant** . Un indice è costituito da una o più colonne e la matrice contiene un valore da confrontare con ogni colonna corrispondente.  
  
 *SeekOption*  
 Valore [SeekEnum](./seekenum.md) che specifica il tipo di confronto da eseguire tra le colonne dell'indice e i relativi *valori*di base.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il metodo **Seek** insieme alla proprietà [index](./index-property.md) se il provider sottostante supporta indici nell'oggetto **Recordset** . Utilizzare il metodo [Supports](./supports-method.md)**(adSeek)** per determinare se il provider sottostante supporta **Seek**e il metodo **Supports (adIndex)** per determinare se il provider supporta gli indici. Ad esempio, il [provider di OLE DB per Microsoft Jet](../../guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) supporta la **ricerca** e l' **Indice**.  
  
 Se **Seek** non trova la riga desiderata, non si verifica alcun errore e la riga viene posizionata alla fine del **Recordset**. Impostare la proprietà **index** sull'indice desiderato prima di eseguire questo metodo.  
  
 Questo metodo è supportato solo con i cursori sul lato server. La ricerca non è supportata quando il valore della proprietà [CursorLocation](./cursorlocation-property-ado.md) dell'oggetto **Recordset** è **adUseClient**.  
  
 Questo metodo può essere utilizzato solo quando l'oggetto **Recordset** è stato aperto con un valore [CommandTypeEnum](./commandtypeenum.md) di **adCmdTableDirect**.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodo Seek e proprietà index (VB)](./seek-method-and-index-property-example-vb.md)   
 [Esempio di metodo Seek e proprietà index (VC + +)](./seek-method-and-index-property-example-vc.md)   
 [Metodo Find (ADO)](./find-method-ado.md)   
 [Proprietà Index](./index-property.md)