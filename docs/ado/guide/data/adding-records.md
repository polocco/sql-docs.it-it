---
description: Aggiunta di record a un recordset
title: Aggiunta di record | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- AddNew method [ADO]
- ADO, editing data
- editing data [ADO], AddNew method
- editing data [ADO], adding data
ms.assetid: dd34669e-6f06-403b-9241-1c85c82aecc2
author: rothja
ms.author: jroth
ms.openlocfilehash: b833bc78a75d09c8f58ae12532f446ec94a097e0
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991752"
---
# <a name="adding-records-to-a-recordset"></a>Aggiunta di record a un recordset
Utilizzare il metodo **AddNew** per creare e inizializzare un nuovo record in un **Recordset**esistente. È possibile utilizzare il metodo **Supports** con un valore **CursorOptionEnum** di **adAddNew** per verificare se è possibile aggiungere record all'oggetto **Recordset** corrente.

 Dopo aver chiamato il metodo **AddNew** , il nuovo record diventa il record corrente e rimane aggiornato dopo la chiamata al metodo **Update** . Se l'oggetto **Recordset** non supporta i segnalibri, potrebbe non essere possibile accedere al nuovo record dopo lo spostamento in un altro record. Pertanto, a seconda del tipo di cursore, potrebbe essere necessario chiamare il metodo **Requery** per rendere accessibile il nuovo record.

 Se si chiama **AddNew** durante la modifica del record corrente o durante l'aggiunta di un nuovo record, ADO chiama il metodo **Update** per salvare le modifiche e quindi crea il nuovo record.

 In questa sezione vengono trattati gli argomenti seguenti.

-   [Aggiunta di record con AddNew](./adding-records-using-addnew.md)

-   [Aggiunta di più campi](./adding-multiple-fields.md)

-   [Determinazione della modalità di modifica](./determining-edit-mode.md)

-   [Uso di AddNew in modalità batch e immediata](./using-addnew-in-immediate-and-batch-modes.md)