---
description: Evento FetchComplete (ADO)
title: Evento FetchComplete (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset::ExecuteComplete
- ExecuteComplete
helpviewer_keywords:
- FetchComplete event [ADO]
ms.assetid: a28d3858-566c-468d-b070-d1de4339fbea
author: rothja
ms.author: jroth
ms.openlocfilehash: 7ef8df9f6d4ea113d5cca9ad9ffba9c4888776d8
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88973352"
---
# <a name="fetchcomplete-event-ado"></a>Evento FetchComplete (ADO)
L'evento **FetchComplete** viene chiamato dopo che tutti i record di un'operazione asincrona lunga sono stati recuperati nel [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
FetchComplete pError, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parametri  
 *pError*  
 Oggetto [Error](../../../ado/reference/ado-api/error-object.md) . Viene descritto l'errore che si è verificato se il valore di **adStatus** è **adStatusErrorsOccurred**; in caso contrario, non è impostato.  
  
 *adStatus*  
 Valore di stato di [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) . Quando viene chiamato questo evento, questo parametro è impostato su **adStatusOK** se l'operazione che ha causato l'evento è riuscita o **adStatusErrorsOccurred** se l'operazione non è riuscita.  
  
 Prima della restituzione di questo evento, impostare questo parametro su **adStatusUnwantedEvent** per impedire le notifiche successive.  
  
 *pRecordset*  
 Oggetto **Recordset** . Oggetto per il quale sono stati recuperati i record.  
  
## <a name="remarks"></a>Osservazioni  
 Per usare **FetchComplete** con Microsoft Visual Basic, è necessario Visual Basic 6,0 o versione successiva.  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di modello di eventi ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Riepilogo dei gestori eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)
