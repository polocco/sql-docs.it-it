---
title: "Passaggio 2: Inizializzare l'applicazione . Documenti Microsoft"
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- initializing applications [ODBC]
- application process [ODBC], initializing applications
ms.assetid: 23a7a230-ae2c-4a5e-9760-d2e17f92c389
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 843155ba6b641ea26717e63af55c8774f963a800
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288267"
---
# <a name="step-2-initialize-the-application"></a>Passaggio 2: Inizializzare l'applicazione
Il secondo passaggio consiste nell'inizializzare l'applicazione, come illustrato nella figura seguente. Esattamente ciò che viene fatto qui varia con l'applicazione.  
  
 ![Inizializzazione di un'applicazione ODBC](../../../odbc/reference/develop-app/media/pr12.gif "pr12 (informazioni in")  
  
 A questo punto, è comune utilizzare **SQLGetInfo** per individuare le funzionalità del driver. Per ulteriori informazioni, vedere [Considerare le funzionalità del database da utilizzare](../../../odbc/reference/develop-app/considering-database-features-to-use.md).  
  
 Tutte le applicazioni devono allocare un handle di istruzione con **SQLAllocHandle**e molte applicazioni impostano attributi di istruzione, ad esempio il tipo di cursore, con **SQLSetStmtAttr**. Per ulteriori informazioni, vedere [Allocazione di un handle](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md) di istruzione e [attributi di istruzione](../../../odbc/reference/develop-app/statement-attributes.md).
