---
description: Record di intestazione
title: Record di intestazione | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- header records [ODBC]
- diagnostic records [ODBC]
ms.assetid: d0fff1ed-5616-422a-a394-7ea1d2486f89
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4de764381e54a0b3485130c1a3bdf25b2a9bf9fa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476643"
---
# <a name="header-record"></a>Record di intestazione
I campi del record di intestazione contengono informazioni generali sull'esecuzione di una funzione, tra cui il codice restituito, il conteggio delle righe, il numero di record di stato e il tipo di istruzione eseguita. Il record di intestazione viene sempre creato a meno che la funzione non restituisca SQL_INVALID_HANDLE. Per un elenco completo dei campi nel record di intestazione, vedere la descrizione della funzione [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) .
