---
description: Metodo Requery
title: Metodo Requery | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Requery
- Recordset15::raw_Requery
helpviewer_keywords:
- Requery method [ADO]
ms.assetid: d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1
author: rothja
ms.author: jroth
ms.openlocfilehash: 12f60b295d569119a356631dc445bd034916665a
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989552"
---
# <a name="requery-method"></a>Metodo Requery
Aggiorna i dati in un oggetto [Recordset](./recordset-object-ado.md) eseguendo nuovamente la query su cui è basato l'oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
recordset.Requery Options  
```  
  
#### <a name="parameters"></a>Parametri  
 *Opzioni*  
 Facoltativa. Maschera di maschera che contiene i valori [ExecuteOptionEnum](./executeoptionenum.md) e [CommandTypeEnum](./commandtypeenum.md) che interessano questa operazione.  
  
> [!NOTE]
>  Se *options* è impostato su **adAsyncExecute**, questa operazione viene eseguita in modo asincrono e viene emesso un evento [RecordsetChangeComplete](./willchangerecordset-and-recordsetchangecomplete-events-ado.md) alla conclusione. I valori **ExecuteOpenEnum** di **adExecuteNoRecords** o **adExecuteStream** non devono essere utilizzati con la **riesecuzione della query**.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il metodo **Requery** per aggiornare l'intero contenuto di un oggetto **Recordset** dall'origine dati rilasciando il comando originale e recuperando i dati una seconda volta. La chiamata a questo metodo equivale alla chiamata dei metodi [Close](./close-method-ado.md) e [Open](./open-method-ado-recordset.md) in successione. Se si modifica il record corrente o si aggiunge un nuovo record, si verificherà un errore.  
  
 Mentre l'oggetto **Recordset** è aperto, le proprietà che definiscono la natura del cursore ([CursorType](./cursortype-property-ado.md), [LockType](./locktype-property-ado.md), [maxRecords](./maxrecords-property-ado.md)e così via) sono di sola lettura. Pertanto, il metodo **Requery** può aggiornare solo il cursore corrente. Per modificare le proprietà del cursore e visualizzare i risultati, è necessario utilizzare il metodo [Close](./close-method-ado.md) in modo che le proprietà diventino di nuovo in lettura/scrittura. È quindi possibile modificare le impostazioni delle proprietà e chiamare il metodo [Open](./open-method-ado-recordset.md) per riaprire il cursore.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodi Execute, Requery e Clear (VB)](./execute-requery-and-clear-methods-example-vb.md)   
 [Esempio di metodi Execute, Requery e Clear (VBScript)](./execute-requery-and-clear-methods-example-vbscript.md)   
 [Esempio di metodi Execute, Requery e Clear (VC + +)](./execute-requery-and-clear-methods-example-vc.md)   
 [Proprietà CommandText (ADO)](./commandtext-property-ado.md)