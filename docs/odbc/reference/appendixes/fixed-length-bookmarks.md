---
title: Segnalibri a lunghezza fissa | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], bookmarks
- bookmarks [ODBC]
- compatibility [ODBC], bookmarks
- fixed-length bookmarks [ODBC]
ms.assetid: cbd8185e-fb03-408f-b80b-1a2e164534fd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f90c5888a68506c056b2a56fce516080148528e7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306982"
---
# <a name="fixed-length-bookmarks"></a>Segnalibri di lunghezza fissa
Se un driver ODBC *3. x* deve funzionare con un'applicazione ODBC *2. x* che utilizza segnalibri a lunghezza fissa, il driver deve supportare quanto segue:  
  
-   SQL_UB_ON come valore per l'opzione dell'istruzione SQL_USE_BOOKMARKS. (SQL_UB_ON è deprecato in ODBC *3. x*).  
  
-   Opzione dell'istruzione SQL_GET_BOOKMARK.
