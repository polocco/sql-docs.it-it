---
title: Finestra di dialogo SQL Server Profiler-trova | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.pro.find.f1
helpviewer_keywords:
- Find dialog box
ms.assetid: dfaeec04-93d3-4214-9fc1-38b80179b36b
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 81ed454290a5ca62093fe9bdb619179106ca9985
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66088861"
---
# <a name="sql-server-profiler---find-dialog-box"></a>SQL Server Profiler - Finestra di dialogo Trova
  Usare la finestra di dialogo **Trova** per eseguire la ricerca all'interno di una traccia in base a parole o caratteri specifici. Per annullare la ricerca in corso, premere ESC.  
  
 Per aprire questa finestra di dialogo in [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)], scegliere **Trova** dal menu **Modifica**.  
  
## <a name="options"></a>Opzioni  
 **Trova**  
 Immettere il testo che si desidera cercare. La ricerca individua tutte le stringhe contenenti la stringa specificata. Ad esempio, se si cerca "Completed", viene individuata la stringa "SQL:BatchCompleted." I caratteri jolly (*, ? e così via) non sono supportati.  
  
 **Cerca nella colonna**  
 Fare clic su una colonna di dati per eseguire la ricerca oppure fare clic su ** \<tutte le colonne>** per eseguire la ricerca in tutte le colonne di dati della traccia.  
  
 **Maiuscole/minuscole**  
 Consente di trovare una stringa di testo con le stesse lettere maiuscole e minuscole di quella specificata nella casella **Trova** . Deselezionare questa casella di controllo per trovare stringhe di testo nella traccia che corrispondono al testo specificato indipendentemente dai caratteri maiuscoli o minuscoli.  
  
 **Parola intera**  
 Consente di limitare l'ambito della ricerca alle parole intere. Deselezionare la casella di controllo **Parola intera** per cercare un insieme di caratteri all'interno di una parola.  
  
 **Trova successivo**  
 Consente di trovare l'esempio successivo dei caratteri specificati nella casella **Trova** .  
  
 **Trova precedente**  
 Consente di eseguire una ricerca all'indietro per trovare l'esempio precedente dei caratteri specificati nella casella **Trova** .  
  
## <a name="see-also"></a>Vedi anche  
 [Trovare un valore o una colonna di dati durante la traccia &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md)   
 [Creare una traccia &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)   
 [Aprire una tabella di traccia &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)   
 [Aprire un file di traccia &#40;SQL Server Profiler&#41;](../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)   
 [Modelli e autorizzazioni di SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Profiler](../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
