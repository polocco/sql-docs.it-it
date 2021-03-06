---
description: Proprietà FilterAxis (ADO MD)
title: Proprietà FilterAxis (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cellset::FilterAxis
- FilterAxis
helpviewer_keywords:
- FilterAxis property [ADO MD]
ms.assetid: 9c656963-531e-4cd1-b698-d5f42a9b7ba3
author: rothja
ms.author: jroth
ms.openlocfilehash: 13ede9a2780a55d79e1b8c53868a409599510688
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88986712"
---
# <a name="filteraxis-property-ado-md"></a>Proprietà FilterAxis (ADO MD)
Indica le informazioni sul filtro relative al [cellt](./cellset-object-ado-md.md)corrente.  
  
## <a name="return-values"></a>Valori restituiti  
 Restituisce un oggetto [Axis](./axis-object-ado-md.md) ed è di sola lettura.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare la proprietà **FilterAxis** per restituire informazioni sulle dimensioni utilizzate per sezionare i dati. La proprietà [DimensionCount](./dimensioncount-property-ado-md.md) dell' **asse** restituisce il numero di dimensioni del filtro dei dati. Questo asse è in genere costituito da una sola riga.  
  
 L' **asse** restituito da **FilterAxis** non è contenuto nella raccolta [Assis](./axes-collection-ado-md.md) per un oggetto [cellt](./cellset-object-ado-md.md) .  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Cellset (ADO MD)](./cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Axis (ADO MD)](./axis-object-ado-md.md)   
 [Oggetto Dimension (ADO MD)](./dimension-object-ado-md.md)   
 [Proprietà DimensionCount (ADO MD)](./dimensioncount-property-ado-md.md)