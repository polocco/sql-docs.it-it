---
title: MSSQLSERVER_12329 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 12329 (Database Engine error)
ms.assetid: 43f90287-36d5-46c2-ac91-a37202dcf6d3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 83906373b7db0c1ba81ad6779f7657a69fd367cd
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84967981"
---
# <a name="mssqlserver_12329"></a>MSSQLSERVER_12329
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|12329|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|HK_UNSUPPORTED_NON_LATIN_CODEPAGE|  
|Testo del messaggio|Tipi di dati char(n) e varchar(n) che usano regole di confronto con una tabella codici diversa da 1252 non supportati con *construct*.|  
  
## <a name="explanation"></a>Spiegazione  
 Non utilizzare i tipi di dati char(n) e varchar(n) in cui vengono utilizzate le regole di confronto con una tabella codici diversa da 1252.  
  
## <a name="user-action"></a>Azione dell'utente  
 Una situazione imprevista in grado di generare questo errore è:  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = 'us_english')  
```  
  
 Da utilizzare in alternativa:  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
```  
  
  
