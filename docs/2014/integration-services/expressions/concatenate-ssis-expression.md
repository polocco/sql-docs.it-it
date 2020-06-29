---
title: + (concatenazione) (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- concatenation [Integration Services]
- + (concatenate operator)
- concatenate operator (+)
ms.assetid: 0fed6334-7a4f-42dc-a611-191fcaa0e443
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3597f70682b346dc0c2ae5e2bbfa4bef5cc14412
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "85428988"
---
# <a name="-concatenate-ssis-expression"></a>+ (concatenazione) (espressione SSIS)
  Vengono concatenate due espressioni in modo da formare un'unica espressione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
character_expression1 + character_expression2  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *expression1, expression2*  
 Qualsiasi espressione valida con tipo di dati DT_STR, DT_WSTR, DT_TEXT, DT_NTEXT o DT_IMAGE.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_WSTR  
  
## <a name="remarks"></a>Osservazioni  
 Nell'espressione è possibile utilizzare sia il tipo di dati DT_STR che il tipo di dati DT_WSTR.  
  
 La concatenazione dei tipi di dati DT_STR e DT_WSTR restituisce un risultato di tipo DT_WSTR. La lunghezza della stringa risultante è data dalla somma della lunghezza in caratteri delle due stringhe di origine.  
  
 È possibile concatenare solo dati con tipo di dati string DT_STR o DT_WSTR oppure dati con tipo di dati BLOB (Binary Large Object) DT_TEXT, DT_NTEXT o DT_IMAGE. Per concatenare altri tipi di dati è prima necessario convertirli esplicitamente in uno dei tipi di dati indicati in precedenza. Per altre informazioni sui cast supportati tra tipi di dati, vedere [Cast &#40;espressione SSIS&#41;](cast-ssis-expression.md).  
  
 È necessario che le due espressioni abbiano lo stesso tipo di dati oppure che un'espressione possa essere convertita in modo implicito nel tipo di dati dell'altra. Se ad esempio si concatenano la stringa "Order date is " e la colonna **OrderDate** , i valori in **OrderDate** verranno convertiti in modo implicito in un tipo di dati string. Per concatenare due valori numerici, è necessario eseguire il cast esplicito di entrambi a un tipo di dati string.  
  
 In un'operazione di concatenazione è possibile utilizzare un solo tipo di dati BLOB: DT_TEXT, DT_NTEXT o DT_IMAGE.  
  
 Se uno degli elementi è Null, il risultato sarà Null.  
  
 I valori letterali stringa devono essere racchiusi tra virgolette.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio vengono concatenati i valori delle colonne **FirstName** e **LastName** , separandoli con uno spazio.  
  
```  
FirstName + ' ' + LastName  
```  
  
 In questo esempio vengono concatenate le variabili **ZIPCode** e **ZIPCode+4**, che hanno entrambe un tipo di dati string. Poiché il nome della variabile**ZIPCode+4** include il carattere +, deve essere racchiuso tra parentesi quadre.  
  
```  
@ZIPCcode + "-" + @[ZipCode+4]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Precedenza e associatività degli operatori](operator-precedence-and-associativity.md)   
 [Operatori &#40;espressione SSIS&#41;](operators-ssis-expression.md)  
  
  
