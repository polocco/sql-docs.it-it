---
description: MSSQLSERVER_2519
title: MSSQLSERVER_2519 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2519 (Database Engine error)
ms.assetid: 8dc6ad98-5db8-4c88-8dea-6d455e63b839
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6136c47919f6578c0caaf7a1ac5408763a17bda0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88428773"
---
# <a name="mssqlserver_2519"></a>MSSQLSERVER_2519
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Dettagli  
  
| Attributo | valore |  
| :-------- | :---- |  
|Nome prodotto|SQL Server|  
|ID evento|2519|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC_NO_EXPRESSION_EVALUATOR|  
|Testo del messaggio|Impossibile controllare le colonne calcolate e i tipi definiti dall'utente per l'ID di oggetto ID_O (oggetto "NOME_O") perché non è stato possibile inizializzare l'analizzatore di espressioni interno.|  
  
## <a name="explanation"></a>Spiegazione  
Questo messaggio informativo indica che Query Processor non è riuscito a fornire a DBCC un oggetto interno per consentire la restituzione delle colonne calcolate e dei tipi CLR (Common Language Runtime) definiti dall'utente. Ciò significa che non verrà controllata la correttezza delle colonne calcolate e dei tipi CLR definiti dall'utente o che questi non verranno utilizzati durante il controllo DBCC della consistenza tra indici e tabelle di base.  
  
## <a name="user-action"></a>Azione dell'utente  
nessuno  
  
## <a name="see-also"></a>Vedere anche  
[MSSQLSERVER_2518](~/relational-databases/errors-events/mssqlserver-2518-database-engine-error.md)  
  
