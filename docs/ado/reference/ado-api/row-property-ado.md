---
description: Proprietà Row (ADO)
title: Proprietà Row (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordConstruction::PutRow
- ADORecordConstruction::GetRow
- ADORecordConstruction::get_Row
- ADORecordConstruction::Row
- ADORecordConstruction::put_Row
helpviewer_keywords:
- Row property [ADO]
ms.assetid: 21019d89-2dd1-4a26-ac6f-384b81d66949
author: rothja
ms.author: jroth
ms.openlocfilehash: b2862e3f082d42c444b052fcf4a5b493bd192bfe
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989392"
---
# <a name="row-property-ado"></a>Proprietà Row (ADO)
Ottiene o imposta un oggetto OLE DB **riga** da o su un oggetto di [Interfaccia ADORecordConstruction](./adorecordconstruction-interface.md) . Quando si utilizza **put_Row** per impostare un oggetto **riga** , una riga viene trasformata in un oggetto **record** ADO.  
  
## <a name="readwritesyntax"></a>Lettura/scrittura. Sintassi  
  
```  
HRESULT get_Row([out, retval] IUnknown** ppRow);  
HRESULT put_Row([in] IUnknown* pRow);  
```  
  
## <a name="parameters"></a>Parametri  
 *ppRow*  
 Puntatore a un oggetto OLE DB **riga** .  
  
 *Prua*  
 Oggetto OLE DB **riga** .  
  
## <a name="return-values"></a>Valori restituiti  
 Questo metodo di proprietà restituisce i valori HRESULT standard, inclusi S_OK e E_FAIL.  
  
## <a name="applies-to"></a>Si applica a  
 [Interfaccia ADORecordConstruction](./adorecordconstruction-interface.md)