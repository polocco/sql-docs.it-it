---
title: MSSQLSERVER_7711 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7711 (Database Engine error)
ms.assetid: a5c7cd6e-18d6-47ef-902b-db9dd64bba34
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ef193b4089a1ef92bd28877feb95902eee5bbc42
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551086"
---
# <a name="mssqlserver_7711"></a>MSSQLSERVER_7711
    
## <a name="details"></a>Dettagli  
  
|Attributo|valore|  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|7711|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|PRT_RANGE_OVERLAP|  
|Testo del messaggio|L'opzione DATA_COMPRESSION è stata specificata più di una volta per la tabella o per l'indice o per una delle relative partizioni.|  
  
## <a name="explanation"></a>Spiegazione  
 Si è verificato un errore nell'opzione DATA_COMPRESSION di una delle istruzioni seguenti:  
  
-   CREA TABELLA  
  
-   MODIFICA TABELLA  
  
-   CREATE INDEX  
  
-   ALTER INDEX  
  
 Se la tabella o l'indice indicato è partizionato, l'opzione DATA_COMPRESSION è stata elencata più volte per almeno una delle partizioni. Se la tabella o l'indice non è partizionato, l'opzione DATA_COMPRESSION è stata indicata più volte.  
  
## <a name="user-action"></a>Azione dell'utente  
 Per una tabella o un indice partizionato, verificare che l'opzione DATA_COMPRESSION sia specificata solo una volta per ciascuna partizione. Per una tabella o un indice non partizionato, utilizzare l'opzione DATA_COMPRESSION solo una volta nell'istruzione.  
  
  
