---
title: LEN (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- LEN function
- number of characters
ms.assetid: d961398b-e4d0-4936-be17-8f4c5882a640
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 605b6cc30d0b711239c6005e6fc8474aff05b7d3
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84967311"
---
# <a name="len-ssis-expression"></a>LEN (espressione SSIS)
  Viene restituito il numero di caratteri in un'espressione di caratteri. Se la stringa contiene spazi vuoti iniziali e finali, la funzione li includerà nel conteggio. Per una stessa stringa rappresentata con caratteri a uno e due byte, LEN restituisce valori identici.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
LEN(character_expression)  
```  
  
## <a name="arguments"></a>Argomenti  
 *character_expression*  
 Espressione da valutare.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_I4  
  
## <a name="remarks"></a>Osservazioni  
 L'argomento *character_expression* può essere un tipo di dati DT_WSTR, DT_TEXT, DT_NTEXT o DT_IMAGE. Per altre informazioni, vedere [Tipi di dati di Integration Services](../data-flow/integration-services-data-types.md).  
  
 Se *character_expression* è un valore letterale stringa o una colonna di dati con tipo di dati DT_STR, prima di eseguire l'operazione prevista da LEN verrà eseguito il cast implicito al tipo di dati DT_WSTR. Per gli altri tipi di dati è necessario il cast esplicito al tipo di dati DT_WSTR. Per altre informazioni, vedere [Cast &#40;espressione SSIS&#41;](cast-ssis-expression.md).  
  
 Se l'argomento passato alla funzione LEN ha un tipo di dati BLOB (Binary Large Object), ad esempio DT_TEXT, DT_NTEXT o DT_IMAGE, la funzione restituirà il numero dei byte.  
  
 Se l'argomento è Null, LEN restituirà Null.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio viene restituita la lunghezza di un valore letterale stringa. Il risultato restituito è 12.  
  
```  
LEN("Ball Bearing")  
```  
  
 In questo esempio viene restituita la differenza tra le lunghezze dei valori nelle colonne **FirstName** e **LastName** .  
  
```  
LEN(FirstName) - LEN(LastName)  
```  
  
 In questo esempio viene restituita la lunghezza di un nome di computer usando la variabile di sistema **MachineName**.  
  
```  
LEN(@MachineName)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni &#40;espressione SSIS&#41;](functions-ssis-expression.md)  
  
  
