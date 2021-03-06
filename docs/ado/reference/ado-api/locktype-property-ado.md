---
description: Proprietà LockType (ADO)
title: Proprietà LockType (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::LockType
helpviewer_keywords:
- LockType property [ADO]
ms.assetid: 9920c14e-033a-4de1-8149-0ce9737a3246
author: rothja
ms.author: jroth
ms.openlocfilehash: 74e86b054ac9d63527cc0f142ee50aa81acbe4b4
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990692"
---
# <a name="locktype-property-ado"></a>Proprietà LockType (ADO)
Indica il tipo di blocchi inseriti nei record durante la modifica.  
  
## <a name="settings-and-return-values"></a>Impostazioni e valori restituiti  
 Imposta o restituisce un valore [LockTypeEnum](./locktypeenum.md) . Il valore predefinito è **adLockReadOnly**.  
  
## <a name="remarks"></a>Osservazioni  
 Impostare la proprietà **LockType** prima di aprire un [Recordset](./recordset-object-ado.md) per specificare il tipo di blocco che il provider deve utilizzare per l'apertura. Leggere la proprietà per restituire il tipo di blocco in uso in un oggetto **Recordset** aperto.  
  
 I provider potrebbero non supportare tutti i tipi di blocco. Se un provider non è in grado di supportare l'impostazione **LockType** richiesta, verrà sostituito un altro tipo di blocco. Per determinare l'effettiva funzionalità di blocco disponibile in un oggetto **Recordset** , utilizzare il metodo [Supports](./supports-method.md) con **ADUpdate** e **adUpdateBatch**.  
  
 L'impostazione **adLockPessimistic** non è supportata se la proprietà [CursorLocation](./cursorlocation-property-ado.md) è impostata su **adUseClient**. Se viene impostato un valore non supportato, non verrà generato alcun errore. verrà invece usato il **LockType** supportato più vicino.  
  
 La proprietà **LockType** è in lettura/scrittura quando il **Recordset** è chiuso e in sola lettura quando è aperto.  
  
> [!NOTE]
>  **Utilizzo servizio dati remoto** Se utilizzata su un oggetto **Recordset** sul lato client, la proprietà **LockType** può essere impostata solo su **adLockBatchOptimistic**.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà CursorType, LockType e EditMode (VB)](./cursortype-locktype-and-editmode-properties-example-vb.md)   
 [Esempio di proprietà CursorType, LockType e EditMode (VC + +)](./cursortype-locktype-and-editmode-properties-example-vc.md)   
 [Metodo CancelBatch (ADO)](./cancelbatch-method-ado.md)   
 [Metodo UpdateBatch](./updatebatch-method.md)