---
description: Limitazioni dell'istruzione CREATE INDEX
title: Limitazioni dell'istruzione CREATE INDEX | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- CREATE INDEX statement limitations [ODBC]
- ODBC SQL grammar, CREATE INDEX statement limitations
ms.assetid: 832dcda1-e452-48e6-8adb-7fb33c4fb4ff
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: db2b346afa13e7f7f37151d6d4fa8efdca9fa230
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466453"
---
# <a name="create-index-statement-limitations"></a>Limitazioni dell'istruzione CREATE INDEX
L'istruzione CREATE INDEX non è supportata per i driver di Microsoft Excel o di testo.  
  
 È possibile definire un indice per un massimo di 10 colonne. Se in un'istruzione CREATE INDEX sono incluse più di 10 colonne, l'indice non verrà riconosciuto e la tabella verrà considerata come se non fosse stato creato alcun indice.  
  
 Il driver dBASE non è in grado di creare un indice in una colonna logica.  
  
 Quando si usa il driver dBASE, il tempo di risposta per i file di grandi dimensioni può essere migliorato creando un indice MDX (o. NDX) nella colonna (campo) specificata nelle clausole WHERE di un'istruzione SELECT. Gli indici MDX esistenti verranno applicati automaticamente per gli operatori =, >, \<, > =, =< e tra gli operatori in una clausola WHERE e come i predicati, nonché nei predicati di join.  
  
 Quando si usa il driver dBASE, l'indice creato da un'istruzione CREATE UNIQUE INDEX è in realtà non univoco e i valori duplicati possono essere inseriti nella colonna indicizzata. All'indice è possibile aggiungere un solo record di un set con valori di chiave identici.  
  
 Quando si utilizza il driver Paradox, è necessario definire un indice univoco su un subset contiguo delle colonne di una tabella, inclusa la prima colonna. Una tabella non può essere aggiornata dal driver Paradox se nella tabella non è definito un indice univoco o quando il driver Paradox viene utilizzato senza l'implementazione del motore di database Borland.
