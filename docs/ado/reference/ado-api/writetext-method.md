---
title: Metodo WriteText | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_WriteText
- _Stream::WriteText
helpviewer_keywords:
- WriteText method [ADO]
ms.assetid: 7a669048-13f4-4574-a2b1-985e089729d5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 64b7d8fd3f2220562e3695d6e31c83261daa2e60
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "67947491"
---
# <a name="writetext-method"></a>Metodo WriteText
Scrive una stringa di testo specificata in un oggetto [flusso](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Stream.WriteText Data, Options  
```  
  
#### <a name="parameters"></a>Parametri  
 *Dati*  
 Valore **stringa** che contiene il testo in caratteri da scrivere.  
  
 *Opzioni*  
 Facoltativa. Valore [StreamWriteEnum](../../../ado/reference/ado-api/streamwriteenum.md) che specifica se è necessario scrivere un carattere separatore di riga alla fine della stringa specificata.  
  
## <a name="remarks"></a>Osservazioni  
 Le stringhe specificate vengono scritte nell'oggetto **flusso** senza spazi o caratteri intermedi tra ogni stringa.  
  
 La [posizione](../../../ado/reference/ado-api/position-property-ado.md) corrente è impostata sul carattere che segue i dati scritti. Il metodo **WRITETEXT** non tronca il resto dei dati in un flusso. Se si desidera troncare questi caratteri, chiamare [SetEOS](../../../ado/reference/ado-api/seteos-method.md).  
  
 Se si scrive oltre la posizione [EOS](../../../ado/reference/ado-api/eos-property.md) corrente, le [dimensioni](../../../ado/reference/ado-api/size-property-ado-stream.md) del **flusso** verranno aumentate in modo da contenere nuovi caratteri e **EOS** passerà al nuovo ultimo byte nel **flusso**.  
  
> [!NOTE]
>  Il metodo **WRITETEXT** viene usato con i flussi di testo (il[tipo](../../../ado/reference/ado-api/type-property-ado-stream.md) è **adTypeText**). Per i flussi binari (**tipo** è **adTypeBinary**), usare [Write](../../../ado/reference/ado-api/write-method.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Write (metodo)](../../../ado/reference/ado-api/write-method.md)
