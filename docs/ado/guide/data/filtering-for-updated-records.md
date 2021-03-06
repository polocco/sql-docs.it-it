---
description: Filtro per i record aggiornati
title: Filtro per i record aggiornati | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- filtering for updated records [ADO]
ms.assetid: 4a798921-d7bb-47c9-a252-550fd9463ec9
author: rothja
ms.author: jroth
ms.openlocfilehash: cd97232b83b355948f449fefb57aa748bbc2db40
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991252"
---
# <a name="filtering-for-updated-records"></a>Filtro per i record aggiornati
Prima di chiamare UpdateBatch, è possibile utilizzare la proprietà filtro Recordset per visualizzare solo i record che sono stati modificati dopo l'apertura del recordset o l'ultima chiamata a UpdateBatch. A tale scopo, impostare Filter uguale a adFilterPendingRecords per determinare il numero di record che verranno aggiornati, come illustrato nell'esempio di codice nella sezione successiva.  
  
## <a name="remarks"></a>Osservazioni  
 Questo esempio estende l'esempio precedente di UpdateBatch filtrando il recordset immediatamente prima di chiamare il UpdateBatch, mostrando all'utente quali record verranno modificati e consentendo di annullare l'aggiornamento (usando il metodo CancelBatch).  
  
```  
'BeginFilterPend  
    '...  
    objRs1.Open strSQL, strConn, adOpenStatic, adLockBatchOptimistic, adCmdText  
  
    ' Change value of Phone field for first record in Recordset, saving value  
    ' for later restoration.  
    intId = objRs1("ShipperId")  
    sPhone = objRs1("Phone")  
  
    objRs1("Phone") = "(111) 555-1111"  
  
    'Add two new records  
    For i = 0 To 1  
        objRs1.AddNew  
        objRs1(1) = "New Shipper #" & CStr((i + 1))  
        objRs1(2) = "(nnn) 555-" & i & i & i & i  
    Next i  
  
    objRs1.Filter = adFilterPendingRecords  
  
    MsgBox "There are " & objRs1.RecordCount & " records pending.", _  
            , "Filter Pending"  
  
    ' Cancel the updates  
    objRs1.CancelBatch  
'EndFilterPend  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Modalità batch](./batch-mode.md)