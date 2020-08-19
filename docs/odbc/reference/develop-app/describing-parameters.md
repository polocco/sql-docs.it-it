---
description: Descrizione di parametri
title: Descrizione dei parametri | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBindParameter function [ODBC], describing parameters
ms.assetid: 118d0f47-2afd-4955-bb47-38b1e2c2f38f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a41bee40403cc3562c41ccc13a15c706a0772e27
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476753"
---
# <a name="describing-parameters"></a>Descrizione di parametri
**SQLBindParameter** include argomenti che descrivono il parametro: tipo, precisione e scala SQL. Il driver utilizza queste informazioni, o *metadati,* per convertire il valore del parametro nel tipo necessario per l'origine dati. A prima vista, potrebbe sembrare che il driver si trovi in una posizione migliore per individuare i metadati del parametro rispetto all'applicazione; Dopo tutto, il driver può individuare facilmente i metadati per una colonna del set di risultati. Come si scopre, questo non è il caso. Per prima cosa, la maggior parte delle origini dati non consente al driver di individuare i metadati dei parametri. In secondo luogo, la maggior parte delle applicazioni già conosce i metadati.  
  
 Se un'istruzione SQL è hardcoded nell'applicazione, il writer di applicazioni conosce già il tipo di ogni parametro. Se un'istruzione SQL viene costruita dall'applicazione in fase di esecuzione, l'applicazione può determinare i metadati durante la compilazione dell'istruzione. Ad esempio, quando l'applicazione crea la clausola  
  
```  
WHERE OrderID = ?  
```  
  
 può chiamare **SQLColumns** per la colonna OrderID.  
  
 L'unica situazione in cui l'applicazione non è in grado di determinare facilmente i metadati dei parametri è quando l'utente immette un'istruzione con parametri. In questo caso, l'applicazione chiama **SQLPrepare** per preparare l'istruzione, **SQLNumParams** per determinare il numero di parametri e **SQLDescribeParam** per descrivere ogni parametro. Tuttavia, come indicato in precedenza, la maggior parte delle origini dati non consente al driver di individuare i metadati dei parametri, quindi **SQLDescribeParam** non è ampiamente supportato.
