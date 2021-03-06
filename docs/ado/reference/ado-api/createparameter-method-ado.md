---
description: Metodo CreateParameter (ADO)
title: Metodo CreateParameter (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::raw_CreateParameter
- Command15::CreateParameter
helpviewer_keywords:
- CreateParameter method [RDS]
ms.assetid: 9666fdcc-0544-4ed7-a97b-c415f2a56d7e
author: rothja
ms.author: jroth
ms.openlocfilehash: 8fd075dff5ae67c7965082a9b7d0f75f5c4d47eb
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88974482"
---
# <a name="createparameter-method-ado"></a>Metodo CreateParameter (ADO)
Crea un nuovo oggetto [Parameter](./parameter-object.md) con le proprietà specificate.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Set parameter = command.CreateParameter (Name, Type, Direction, Size, Value)  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un oggetto **Parameter** .  
  
#### <a name="parameters"></a>Parametri  
 *Nome*  
 Facoltativa. Valore **stringa** che contiene il nome dell'oggetto **Parameter** .  
  
 *Tipo*  
 Facoltativa. Valore [DataTypeEnum](./datatypeenum.md) che specifica il tipo di dati dell'oggetto **Parameter** .  
  
 *Direzione*  
 Facoltativa. Valore [ParameterDirectionEnum](./parameterdirectionenum.md) che specifica il tipo di oggetto **Parameter** .  
  
 *Dimensione*  
 Facoltativa. Valore **Long** che specifica la lunghezza massima del valore del parametro in caratteri o byte.  
  
 *Valore*  
 Facoltativa. **Variant** che specifica il valore per l'oggetto **Parameter** .  
  
## <a name="remarks"></a>Osservazioni  
 Usare il metodo **CreateParameter** per creare un nuovo oggetto **Parameter** con un nome, un tipo, una direzione, una dimensione e un valore specificati. Tutti i valori passati negli argomenti vengono scritti nelle proprietà dei **parametri** corrispondenti.  
  
 Questo metodo non aggiunge automaticamente l'oggetto **Parameter** alla raccolta **Parameters** di un oggetto [Command](./command-object-ado.md) . Ciò consente di impostare proprietà aggiuntive i cui valori ADO verranno convalidati quando si aggiunge l'oggetto **Parameter** alla raccolta.  
  
 Se si specifica un tipo di dati a lunghezza variabile nell'argomento *tipo* , è necessario passare un argomento *size* o impostare la proprietà [size](./size-property-ado-parameter.md) dell'oggetto **Parameter** prima di accodarlo alla raccolta **Parameters** . in caso contrario, si verifica un errore.  
  
 Se si specifica un tipo di dati numerico (**adNumeric** o **adDecimal**) nell'argomento *tipo* , è necessario impostare anche le proprietà [NumericScale](./numericscale-property-ado.md) e [Precision](./precision-property-ado.md) .  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Command (ADO)](./command-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodi Append e CreateParameter (VB)](./append-and-createparameter-methods-example-vb.md)   
 [Esempio di metodi Append e CreateParameter (VC + +)](./append-and-createparameter-methods-example-vc.md)   
 [Metodo Append (ADO)](./append-method-ado.md)   
 [Parameter (oggetto)](./parameter-object.md)   
 [Raccolta Parameters (ADO)](./parameters-collection-ado.md)