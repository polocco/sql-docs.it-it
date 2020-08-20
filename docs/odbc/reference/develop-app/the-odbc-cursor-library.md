---
description: Libreria di cursori ODBC
title: Libreria di cursori ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], about cursor library
- ODBC cursor library [ODBC]
- cursor library [ODBC], about cursor library
- scrollable cursors [ODBC]
- cursors [ODBC], cursor library
- block cursors [ODBC]
ms.assetid: 32fb7df0-953a-4f68-b041-7d2852e45d0f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4e5e3a01633a19c4ae82596ba1e180c64bcce06c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487514"
---
# <a name="the-odbc-cursor-library"></a>Libreria di cursori ODBC
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Microsoft consiglia di utilizzare la funzionalità di cursore del driver.  
  
 I cursori a blocchi e scorrevoli sono aggiunte molto utili a molte applicazioni. Tuttavia, non tutti i driver supportano i cursori Block e scorrevoli. Lo stesso vale per le istruzioni Update e Delete posizionate e **SQLSetPos**, descritte in aggiornamento dei dati. Pertanto, il componente ODBC del Windows SDK, incluso in precedenza nell'SDK di Microsoft Data Access Components (MDAC), include una libreria di cursori. La libreria di cursori implementa il blocco, i cursori statici, le istruzioni Update e Delete posizionate e **SQLSetPos** per qualsiasi driver che soddisfi il livello di conformità dell'interfaccia della riga di comando standard del gruppo aperto. La libreria di cursori può essere ridistribuita con le applicazioni ODBC. Per ulteriori informazioni, vedere il contratto di licenza nell'SDK.  
  
 Per utilizzare la libreria di cursori, un'applicazione imposta l'attributo di connessione SQL_ATTR_ODBC_CURSORS prima della connessione all'origine dati. Per ulteriori informazioni sulla libreria di cursori, vedere [Appendice F: libreria di cursori ODBC](../../../odbc/reference/appendixes/appendix-f-odbc-cursor-library.md).
