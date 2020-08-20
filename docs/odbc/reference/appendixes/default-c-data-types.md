---
description: Tipi di dati C predefiniti
title: Tipi di dati C predefiniti | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], pseudo-type identifiers
- pseudo-type identifiers [ODBC], about pseudo-type identifiers
- pseudo-type identifiers [ODBC]
ms.assetid: 229140ae-af8f-4ec8-9ccf-1e92360e0bac
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7d0ed42971405ca23d5f69f47cbb6ac02e8e5675
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456607"
---
# <a name="default-c-data-types"></a>Tipi di dati C predefiniti
Se un'applicazione specifica SQL_C_DEFAULT in **SQLBindCol**, **SQLGetData**o **SQLBindParameter**, il driver presuppone che il tipo di dati C del buffer di output o di input corrisponda al tipo di dati SQL della colonna o del parametro a cui è associato il buffer.  
  
> [!IMPORTANT]  
>  Le applicazioni interoperative non devono utilizzare SQL_C_DEFAULT. Devono invece specificare sempre il tipo C del buffer utilizzato. Ciò è dovuto al fatto che i driver non possono determinare sempre correttamente il tipo C predefinito, per i motivi seguenti:  
  
-   Se il sistema DBMS promuove un tipo di dati SQL di una colonna o di un parametro, il driver non è in grado di determinare il tipo di dati SQL originale di una colonna o un parametro. Pertanto, non è in grado di determinare il tipo di dati C predefinito corrispondente.  
  
-   Se il driver non è in grado di determinare se una colonna o un parametro specifico è firmato, come spesso accade quando questo viene gestito dal sistema DBMS, il driver non è in grado di determinare se il tipo di dati C predefinito corrispondente deve essere firmato o senza segno.  
  
     Poiché SQL_C_DEFAULT viene fornita solo come praticità di programmazione, l'applicazione non perde alcuna funzionalità quando specifica il tipo di dati C effettivo.  
  
 Una tabella che mostra il tipo di dati C predefinito per ogni tipo di dati SQL è inclusa nella [conversione dei dati da SQL ai tipi di dati c](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md), più avanti in questa appendice.
