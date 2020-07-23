---
title: SQRT (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQRT function
- square root of given expression
ms.assetid: 54a75389-c501-4e22-87b8-905f66d6a3a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b12c303d12d0bc4dac23993b9da574409a8e3ae4
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2020
ms.locfileid: "86914938"
---
# <a name="sqrt-ssis-expression"></a>SQRT (espressione SSIS)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Restituisce la radice quadrata di un'espressione numerica.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SQRT(numeric_expression)  
```  
  
## <a name="arguments"></a>Argomenti  
 *numeric_expression*  
 Espressione numerica valida con qualsiasi tipo di dati numeric. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_R8  
  
## <a name="remarks"></a>Osservazioni  
 Se l'argomento è Null, SQRT restituirà Null.  
  
 Se l'argomento è un valore negativo, SQRT restituirà un errore.  
  
 Prima del calcolo della radice quadrata viene eseguito il cast dell'argomento al tipo di dati DT_R8.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio viene restituita la radice quadrata di un valore letterale numerico. Il risultato restituito è 12.  
  
```  
SQRT(144)  
```  
  
 In questo esempio viene restituita la radice quadrata di un'espressione, ovvero il risultato della sottrazione dei valori nelle colonne **Value1** e **Value2** .  
  
```  
SQRT(Value1 - Value2)  
```  
  
 In questo esempio viene restituita la lunghezza del terzo lato di un triangolo rettangolo, ottenuta applicando la funzione SQUARE a due variabili e quindi calcolando la radice quadrata della somma. Se **Side1** contiene 3 e **Side2** contiene 4, la funzione SQRT restituirà 5.  
  
```  
SQRT(SQUARE(@Side1) + SQUARE(@Side2))  
```  
  
> [!NOTE]  
>  Nelle espressioni i nomi delle variabili includono sempre il prefisso \@.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
