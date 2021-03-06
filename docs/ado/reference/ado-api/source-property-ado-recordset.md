---
description: Proprietà Source (Recordset - ADO)
title: Proprietà Source (recordset ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::putref_Source
- Recordset15::Source
- Recordset15::PutSource
- Recordset15::get_Source
- Recordset15::GetSource
- Recordset15::PutRefSource
- Recordset15::put_Source
helpviewer_keywords:
- Source property [ADO Recordset]
ms.assetid: a05ba2c9-2821-4343-8607-4de9b764ec91
author: rothja
ms.author: jroth
ms.openlocfilehash: 3a71efe111a58ab8f799db512e77da4365ba5f48
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88988902"
---
# <a name="source-property-ado-recordset"></a>Proprietà Source (Recordset - ADO)
Indica l'origine dati per un oggetto [Recordset](./recordset-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Impostazioni e valori restituiti  
 Imposta un valore **stringa** o un riferimento all'oggetto [Command](./command-object-ado.md) ; restituisce solo un valore **stringa** che indica l'origine del **Recordset**.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare la proprietà **source** per specificare un'origine dati per un oggetto **Recordset** utilizzando uno dei seguenti elementi: una variabile oggetto **comando** , un'istruzione SQL, un stored procedure o un nome di tabella.  
  
 Se si imposta la **proprietà Source** su un oggetto **Command** , la proprietà [ActiveConnection](./activeconnection-property-ado.md) dell'oggetto **Recordset** erediterà il valore della proprietà **ActiveConnection** per l'oggetto **comando** specificato. Tuttavia, la lettura della proprietà **source** non restituisce un oggetto **Command** ; Restituisce invece la proprietà [CommandText](./commandtext-property-ado.md) dell'oggetto **Command** a cui si imposta la proprietà **source** .  
  
 Se la proprietà **source** è un'istruzione SQL, un stored procedure o un nome di tabella, è possibile ottimizzare le prestazioni passando l'argomento *options* appropriato con la chiamata al metodo [Open](./open-method-ado-recordset.md) .  
  
 La proprietà di **origine** è in lettura/scrittura per gli oggetti **Recordset** chiusi e in sola lettura per gli oggetti **Recordset** aperti.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà Source (VB)](./source-property-example-vb.md)   
 [Proprietà Source (errore ADO)](./source-property-ado-error.md)   
 [Proprietà Source (Record - ADO)](./source-property-ado-record.md)