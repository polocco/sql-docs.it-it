---
description: Metodo GetRows (ADO)
title: Metodo GetRows (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::GetRows
- Recordset15::raw_GetRows
helpviewer_keywords:
- Getrows method [ADO]
ms.assetid: 14b92860-4171-47d9-a413-dd60dd6a8880
author: rothja
ms.author: jroth
ms.openlocfilehash: 666eabf1a375c6a86826bc94600846bd10a0ecfe
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990912"
---
# <a name="getrows-method-ado"></a>Metodo GetRows (ADO)
Recupera più record di un oggetto [Recordset](./recordset-object-ado.md) in una matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
array = recordset.GetRows(Rows, Start, Fields )  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce una **variante** il cui valore è una matrice bidimensionale.  
  
#### <a name="parameters"></a>Parametri  
 *prime righe*  
 Facoltativa. Valore [GetRowsOptionEnum](./getrowsoptionenum.md) che indica il numero di record da recuperare. Il valore predefinito è **adGetRowsRest**.  
  
 *Inizia*  
 Facoltativa. Valore **stringa** o **variante** che restituisce il segnalibro per il record da cui deve iniziare l'operazione **GetRows** . È anche possibile usare un valore [BookmarkEnum](./bookmarkenum.md) .  
  
 *Fields*  
 Facoltativa. **Variant** che rappresenta un nome di campo singolo o una posizione ordinale o una matrice di nomi di campo o numeri di posizione ordinale. ADO restituisce solo i dati in questi campi.  
  
## <a name="remarks"></a>Osservazioni  
 Usare il metodo **GetRows** per copiare record da un **Recordset** in una matrice bidimensionale. Il primo indice identifica il campo e il secondo identifica il numero di record. La variabile di *matrice* viene dimensionata automaticamente con le dimensioni corrette quando il metodo **GetRows** restituisce i dati.  
  
 Se non si specifica un valore per l'argomento *Rows* , il metodo **GetRows** recupera automaticamente tutti i record nell'oggetto **Recordset** . Se si richiedono più record di quanti siano disponibili, **GetRows** restituisce solo il numero di record disponibili.  
  
 Se l'oggetto **Recordset** supporta segnalibri, è possibile specificare in quale record il metodo **GetRows** deve iniziare a recuperare i dati passando il valore della proprietà [segnalibro](./bookmark-property-ado.md) di tale record nell'argomento *iniziale* .  
  
 Se si desidera limitare i campi restituiti dalla chiamata **GetRows** , è possibile passare un nome/numero di campo singolo o una matrice di nomi di campo/numeri nell'argomento *Fields* .  
  
 Dopo aver chiamato **GetRows**, il successivo record non letto diventa il record corrente oppure la proprietà [EOF](./bof-eof-properties-ado.md) è impostata su **true** se non sono presenti altri record.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodo GetRows (VB)](./getrows-method-example-vb.md)   
 [Esempio del metodo GetRows (VC++)](./getrows-method-example-vc.md)