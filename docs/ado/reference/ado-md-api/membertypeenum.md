---
description: MemberTypeEnum
title: MemberTypeEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- MemberTypeEnum
helpviewer_keywords:
- MemberTypeEnum enumeration [ADO MD]
ms.assetid: 5d8132c0-7ca2-4f86-8336-1b34213869ad
author: rothja
ms.author: jroth
ms.openlocfilehash: 441430cd164be017779afc54ba9af866edaea874
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88986262"
---
# <a name="membertypeenum"></a>MemberTypeEnum
Specifica l'impostazione per la proprietà [Type](./type-property-ado-md.md) di un oggetto [membro](./member-object-ado-md.md) .  
  
|Costante|Valore|Descrizione|  
|--------------|-----------|-----------------|  
|**adMemberAll**|4|Indica che l'oggetto **membro** rappresenta tutti i membri del livello.|  
|**adMemberFormula**|3|Indica che l'oggetto **membro** viene calcolato utilizzando un'espressione di formula.|  
|**adMemberMeasure**|2|Indica che l'oggetto **membro** appartiene alla dimensione Measures e rappresenta un attributo quantitativo.|  
|**adMemberRegular**|1|Valore predefinito. Indica che l'oggetto **membro** rappresenta un'istanza di un'entità business.|  
|**adMemberUnknown**|0|Impossibile determinare il tipo del membro.|