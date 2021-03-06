---
description: Proprietà Description (ADO MD)
title: Proprietà Description (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Member::Description
- Level::Description
- CubeDef::Description
- Hierarchy::Description
- Description
- Dimension::Description
helpviewer_keywords:
- Description property [ADO MD]
ms.assetid: 6d626d35-0bf3-4f24-9934-ad9c9c91273a
author: rothja
ms.author: jroth
ms.openlocfilehash: 726a49da64c36b487868068affad65164b9b3c5e
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88986902"
---
# <a name="description-property-ado-md"></a>Proprietà Description (ADO MD)
Restituisce una spiegazione del testo dell'oggetto corrente.  
  
## <a name="return-values"></a>Valori restituiti  
 Restituisce una **stringa** ed è di sola lettura.  
  
## <a name="remarks"></a>Osservazioni  
 Per gli oggetti [membro](./member-object-ado-md.md) , la **Descrizione** si applica solo ai membri delle formule e delle misure. **Description** restituisce una stringa vuota ("") per tutti gli altri tipi di membri. Per ulteriori informazioni sui vari tipi di membri, vedere la proprietà [Type](./type-property-ado-md.md) .  
  
 Questa proprietà è supportata solo su oggetti **membro** che appartengono a un oggetto [Level](./level-object-ado-md.md) . Si verifica un errore quando si fa riferimento a questa proprietà dagli oggetti **membro** che appartengono a un oggetto [position](./position-object-ado-md.md) .  
  
## <a name="applies-to"></a>Si applica a  

:::row:::
    :::column:::
        [Oggetto CubeDef (ADO MD)](./cubedef-object-ado-md.md)  
        [Oggetto Dimension (ADO MD)](./dimension-object-ado-md.md)  
    :::column-end:::
    :::column:::
        [Oggetto Hierarchy (ADO MD)](./hierarchy-object-ado-md.md)  
        [Oggetto Level (ADO MD)](./level-object-ado-md.md)  
    :::column-end:::
    :::column:::
        [Oggetto Member (ADO MD)](./member-object-ado-md.md)  
    :::column-end:::
:::row-end:::