---
description: DATEPART (espressione SSIS)
title: DATEPART (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], DATEPART
- DATEPART function
ms.assetid: 3e590094-fc49-4144-805f-fdc1bf2fe509
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3d4509e356193391b903b764771dca170c06026d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88348247"
---
# <a name="datepart-ssis-expression"></a>DATEPART (espressione SSIS)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Restituisce un valore integer che rappresenta una parte di una data.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DATEPART(datepart, date)  
```  
  
## <a name="arguments"></a>Argomenti  
 *datepart*  
 Parametro che consente di specificare per quale parte della data si desidera restituire un nuovo valore.  
  
 *date*  
 Espressione che restituisce una data valida o una stringa con formato di data.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_I4  
  
## <a name="remarks"></a>Commenti  
 Se l'argomento è Null, DATEPART restituirà Null.  
  
 Per i valori letterali di data è necessario eseguire il cast esplicito a uno dei tipi di dati date. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Nella tabella seguente sono elencate le parti della data e le abbreviazioni riconosciute dall'analizzatore di espressioni. Per i nomi delle parti della data non viene fatta distinzione tra maiuscole e minuscole.  
  
|parte di una data|Abbreviazioni|  
|--------------|-------------------|  
|Year|yy, yyyy|  
|Quarter|qq, q|  
|Month|mm, m|  
|Dayofyear|dy, y|  
|Giorno|dd, d|  
|Settimana|wk, ww|  
|Giorno della settimana|dw|  
|Ora|Hh|  
|Minuto|mi, n|  
|Second|ss, s|  
|Millisecond|Ms|  
  
## <a name="ssis-expression-examples"></a>Esempi di espressione SSIS  
 In questo esempio viene restituito un valore integer che rappresenta il mese in un valore letterale data. Se la data è in formato "mm/gg/aaaa", l'esempio restituirà 11.  
  
```  
DATEPART("month", (DT_DBTIMESTAMP)"11/04/2002")  
```  
  
 In questo esempio viene restituito un Integer che rappresenta il giorno nella colonna **ModifiedDate** .  
  
```  
DATEPART("dd", ModifiedDate)  
```  
  
 In questo esempio viene restituito un valore integer che rappresenta l'anno nella data corrente.  
  
```  
DATEPART("yy",GETDATE())  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DATEADD &#40;espressione SSIS&#41;](../../integration-services/expressions/dateadd-ssis-expression.md)   
 [DATEDIFF &#40;espressione SSIS&#41;](../../integration-services/expressions/datediff-ssis-expression.md)   
 [DAY &#40;espressione SSIS&#41;](../../integration-services/expressions/day-ssis-expression.md)   
 [MONTH &#40;espressione SSIS&#41;](../../integration-services/expressions/month-ssis-expression.md)   
 [YEAR &#40;espressione SSIS&#41;](../../integration-services/expressions/year-ssis-expression.md)   
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
