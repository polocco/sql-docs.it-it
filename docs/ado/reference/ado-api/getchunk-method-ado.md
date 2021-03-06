---
description: Metodo GetChunk (ADO)
title: Metodo GetChunk (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field20::raw_GetChunk
- Field20::GetChunk
helpviewer_keywords:
- GetChunk method [ADO]
ms.assetid: fc268e22-205b-44a3-9038-ffed51e23e10
author: rothja
ms.author: jroth
ms.openlocfilehash: 196f41f7828be16c7c38b281edb85774569580a1
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88972912"
---
# <a name="getchunk-method-ado"></a>Metodo GetChunk (ADO)
Restituisce tutto o una parte del contenuto di un oggetto [campo](./field-object.md) di dati di testo o binario di grandi dimensioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
variable = field.GetChunk(Size)  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un oggetto **Variant**.  
  
#### <a name="parameters"></a>Parametri  
 *Dimensione*  
 Espressione **Long** uguale al numero di byte o caratteri che si desidera recuperare.  
  
## <a name="remarks"></a>Osservazioni  
 Usare il metodo **GetChunk** su un oggetto **campo** per recuperare parte o tutti i dati di tipo carattere o binario lungo. In situazioni in cui la memoria di sistema è limitata, è possibile usare il metodo **GetChunk** per modificare i valori Long in parti, anziché nel loro complesso.  
  
 I dati restituiti da una chiamata **GetChunk** sono assegnati alla *variabile*. Se le *dimensioni* sono maggiori dei dati rimanenti, il metodo **GetChunk** restituisce solo i dati rimanenti senza *variabile* di riempimento con spazi vuoti. Se il campo è vuoto, il metodo **GetChunk** restituisce un valore null.  
  
 Ogni chiamata a **GetChunk** successiva recupera i dati a partire dal punto in cui è stata interrotta la chiamata **GetChunk** precedente. Tuttavia, se si recuperano dati da un campo e si imposta o si legge il valore di un altro campo nel record corrente, ADO presuppone che il recupero dei dati dal primo campo sia stato completato. Se si chiama nuovamente il metodo **GetChunk** sul primo campo, ADO interpreta la chiamata come nuova operazione **GetChunk** e inizia la lettura dall'inizio dei dati. L'accesso ai campi di altri oggetti [Recordset](./recordset-object-ado.md) che non sono cloni del primo oggetto **Recordset** non interferisce con le operazioni **GetChunk** .  
  
 Se il bit **adFldLong** nella proprietà [Attributes](./attributes-property-ado.md) di un oggetto **Field** è impostato su **true**, è possibile usare il metodo **GetChunk** per quel campo.  
  
 Se non è presente alcun record corrente quando si usa il metodo **GetChunk** su un oggetto **campo** , viene generato l'errore 3021 (nessun record corrente).  
  
> [!NOTE]
>  Il metodo **GetChunk** non agisce sugli oggetti **campo** di un oggetto [record](./record-object-ado.md) . Non esegue alcuna operazione e produrrà un errore di run-time.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Field](./field-object.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodi AppendChunk e GetChunk (VB)](./appendchunk-and-getchunk-methods-example-vb.md)   
 [Esempio di metodi AppendChunk e GetChunk (VC + +)](./appendchunk-and-getchunk-methods-example-vc.md)   
 [Metodo AppendChunk (ADO)](./appendchunk-method-ado.md)   
 [Proprietà Attributes (ADO)](./attributes-property-ado.md)