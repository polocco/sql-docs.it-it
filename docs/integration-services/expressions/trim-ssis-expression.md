---
description: TRIM (espressione SSIS)
title: TRIM (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- leading blanks
- TRIM function
- trailing blanks
ms.assetid: 7dd9081d-a3d4-483a-bf7e-bf2bd7692d39
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d725f4cc6921a1f468bf36ae64d202a31b384e80
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88484384"
---
# <a name="trim-ssis-expression"></a>TRIM (espressione SSIS)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Restituisce un'espressione di caratteri dopo aver rimosso gli spazi iniziali e finali.  
  
> [!NOTE]  
>  TRIM non rimuove altri caratteri spazio quali i caratteri di tabulazione o avanzamento riga. Unicode offre elementi di codice per molti tipi diversi di spazi, ma questa funzione riconosce solo l'elemento di codice Unicode 0x0020. Quando stringhe DBCS (Double-Byte Character Set) vengono convertite in Unicode, possono includere caratteri spazio diversi da 0x0020 e la funzione non può rimuovere tali spazi. Per rimuovere qualsiasi tipo di spazi, è possibile utilizzare il metodo Microsoft Visual Basic .NET Trim in uno script eseguito dal componente Script.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
TRIM(character_expression)  
```  
  
## <a name="arguments"></a>Argomenti  
 *character_expression*  
 Espressione di caratteri da cui rimuovere gli spazi.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_WSTR  
  
## <a name="remarks"></a>Osservazioni  
 Se l'argomento è Null, TRIM restituirà Null.  
  
 È possibile utilizzare TRIM solo con il tipo di dati DT_WSTR. Se l'argomento *character_expression* è un valore letterale stringa o una colonna di dati con tipo di dati DT_STR, prima di eseguire l'operazione prevista da TRIM verrà eseguito il cast implicito al tipo di dati DT_WSTR. Per gli altri tipi di dati è necessario il cast esplicito al tipo di dati DT_WSTR. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md) e [Cast &#40;espressione SSIS&#41;](../../integration-services/expressions/cast-ssis-expression.md).  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio vengono rimossi gli spazi iniziali e finali da un valore letterale stringa. Il risultato restituito è "New York".  
  
```  
TRIM("   New York   ")  
```  
  
 In questo esempio vengono rimossi gli spazi iniziali e finali dal risultato della concatenazione delle colonne **FirstName** e **LastName** . La stringa vuota tra **FirstName** e **LastName** non viene rimossa.  
  
```  
TRIM(FirstName + " "+ LastName)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [LTRIM &#40;espressione SSIS&#41;](../../integration-services/expressions/ltrim-ssis-expression.md)   
 [RTRIM &#40;espressione SSIS&#41;](../../integration-services/expressions/rtrim-ssis-expression.md)   
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
