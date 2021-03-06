---
description: Metodo DeleteRecord (ADO)
title: Metodo DeleteRecord (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_DeleteRecord
- _Record::DeleteRecord
helpviewer_keywords:
- DeleteRecord method [ADO]
ms.assetid: 2726498c-dbd8-4266-983b-ae7d62c39142
author: rothja
ms.author: jroth
ms.openlocfilehash: 634e28fb1bcc6d246de72164f33d3d252f63505a
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88974002"
---
# <a name="deleterecord-method-ado"></a>Metodo DeleteRecord (ADO)
Elimina un'entità rappresentata da un [record](../../../ado/reference/ado-api/record-object-ado.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Record.DeleteRecord Source, Async  
```  
  
#### <a name="parameters"></a>Parametri  
 *Origine*  
 Facoltativa. Valore **stringa** che contiene un URL che identifica l'entità, ad esempio il file o la directory, da eliminare. Se *source* viene omesso o specifica una stringa vuota, l'entità rappresentata dal [record](../../../ado/reference/ado-api/record-object-ado.md) corrente viene eliminata. Se il record è un record di raccolta ([RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md) di **adCollectionRecord**, ad esempio una directory), verranno eliminati anche tutti gli elementi figlio, ad esempio le sottodirectory.  
  
 *Asincrona*  
 Facoltativa. Valore **booleano** che, se impostato su **true**, specifica che l'operazione di eliminazione è asincrono.  
  
## <a name="remarks"></a>Osservazioni  
 Le operazioni sull'oggetto rappresentato da questo **record** possono avere esito negativo dopo il completamento di questo metodo. Dopo la chiamata a **DeleteRecord**, il **record** deve essere chiuso perché il comportamento del **record** può diventare imprevedibile in base al momento in cui il provider aggiorna il **record** con l'origine dati.  
  
 Se questo **record** è stato ottenuto da un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), i risultati di questa operazione non verranno riflessi immediatamente nel **Recordset**. Per aggiornare il **Recordset** , chiuderlo e riaprirlo oppure eseguire il metodo di [ripetizione della query](../../../ado/reference/ado-api/requery-method.md) del **Recordset** , il metodo [Update](../../../ado/reference/ado-api/update-method.md) o il metodo [Resync](../../../ado/reference/ado-api/resync-method.md) .  
  
> [!NOTE]
>  Gli URL che usano lo schema http richiameranno automaticamente il [provider di Microsoft OLE DB per la pubblicazione Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Per ulteriori informazioni, vedere [URL assoluto e relativo](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo Delete (raccolta di campi ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Metodo Delete (raccolta Parameters ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Metodo Delete (Recordset - ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)
