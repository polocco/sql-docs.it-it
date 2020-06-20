---
title: Organizzare le colonne visualizzate in una traccia (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- organizing trace columns displayed [SQL Server]
- arranging trace columns displayed
- traces [SQL Server], data columns
ms.assetid: 6b923f94-0eb1-467e-82f6-ceed43f77017
author: stevestein
ms.author: sstein
ms.openlocfilehash: ed3228806a4fe0d136a1a2d9761dc46ab519677d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054346"
---
# <a name="organize-columns-displayed-in-a-trace-sql-server-profiler"></a>Organizzare le colonne visualizzate in una traccia (SQL Server Profiler)
  È possibile raggruppare le colonne di dati di una traccia selezionando **Organizza colonne** nella tabella di traccia o nella finestra di dialogo **Proprietà file di traccia** oppure durante la definizione della traccia. Il raggruppamento delle colonne di dati semplifica l'analisi dell'output della traccia di [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] . Per altre informazioni, vedere [Visualizzare e analizzare le tracce con SQL Server Profiler](view-and-analyze-traces-with-sql-server-profiler.md).  
  
 L'opzione**Organizza colonne** consente di raggruppare gli eventi di traccia oppure di raggrupparli e aggregarli in base alle colonne di dati selezionate.  
  
-   Per raggruppare unicamente gli eventi di traccia, selezionare più colonne di dati per il raggruppamento. In questo caso, nella finestra della traccia gli eventi saranno raggruppati in base ai valori delle colonne di dati selezionate per il raggruppamento. L'esempio seguente mostra come viene visualizzata la griglia della finestra di traccia se per il raggruppamento vengono selezionate le colonne di dati **Duration** e **StartTime** . I valori della colonna **Duration** vengono visualizzati in ordine crescente, seguiti dai valori della colonna **StartTime** .  
  
|Duration|StartTime|EventClass|ClientProcessID|  
|--------------|---------------|----------------|---------------------|  
||12/12/2006 3:16:43 PM|SQL:StmtStarting|2124|  
|0|12/12/2006 5:39:23 PM|Connessione di controllo|648|  
|1|12/12/2006 5:24:44 PM|SQL:StmtStarting|2124|  
|25|12/12/2006 5:24:44 PM|SQL:StmtCompleted|648|  
  
-   Per raggruppare e aggregare gli eventi di traccia, selezionare una singola colonna per il raggruppamento. In questo caso, nella finestra della traccia gli eventi vengono raggruppati in base ai valori della colonna di dati specificata e tutti gli eventi sottostanti vengono compressi. A sinistra dell'evento nella colonna di dati selezionata per il raggruppamento viene visualizzato un segno più ( **+** ), mentre a destra dell'evento viene visualizzato tra parentesi il numero degli eventi compressi sottostanti. L'esempio seguente mostra come viene visualizzata la griglia della finestra di traccia se per il raggruppamento viene selezionata solo la colonna di dati **EventClass** . Tutti gli eventi vengono organizzati nella colonna di dati **EventClass** . Per visualizzare tutti gli eventi, fare clic sul segno più per espandere e visualizzare tutte le classi di eventi del tipo specificato.  
  
|EventClass|StartTime|Duration|ClientProcessID|  
|----------------|---------------|--------------|---------------------|  
|+ ExistingConnection (6)||||  
|+ SQL:BatchStarting (25)||||  
|+ SQL:StmtCompleted (11)||||  
|+ SQL:SmtStarting (21)||||  
  
### <a name="to-group-data-columns-displayed-in-a-trace"></a>Per raggruppare le colonne di dati visualizzate in una traccia  
  
1.  Aprire un file o una tabella di traccia esistente.  
  
2.  Scegliere **Proprietà** dal menu **File**.  
  
3.  Nella finestra di dialogo **Proprietà file di traccia** o **Proprietà tabella di traccia** fare clic sulla scheda **Selezione eventi** .  
  
4.  Nella scheda **Selezione eventi** fare clic su **Organizza colonne**.  
  
5.  Nella finestra di dialogo **Organizza colonne** selezionare le colonne da visualizzare raggruppate e fare clic su **Su** per spostarle in **Gruppi**. Dopo avere spostato tutte le colonne desiderate in **Gruppi**, è possibile usare i pulsanti **Su** e **Giù** per modificarne l'ordine.  
  
     Lo spostamento dei nomi delle colonne di dati nell'elenco **Gruppi** implica che la traccia visualizzata viene organizzata prima in base ai valori della colonna di dati che appare nella posizione più in alto nell'elenco **Gruppi** , quindi in base alla seconda colonna di dati nell'elenco **Gruppi** e così via.  
  
6.  Fare clic su **OK** nella finestra di dialogo **Organizza colonne** e quindi su **OK** nella finestra di dialogo **Proprietà tabella di traccia** o **Proprietà file di traccia** .  
  
     Dopo avere fatto clic su **OK** nella finestra di dialogo **Proprietà tabella di traccia** o **Proprietà file di traccia** , le colonne di dati verranno riorganizzate nella traccia visualizzata. La colonna di dati spostata nella prima posizione dell'elenco **Gruppi** appare per prima nella visualizzazione della traccia se si legge la griglia da sinistra a destra. Le righe della traccia sono organizzate in ordine crescente in base ai valori contenuti nelle colonne di dati inserite nell'elenco **Gruppi** . Le colonne selezionate per il raggruppamento rimangono fisse, ma è possibile scorrere a destra o a sinistra per visualizzare le altre colonne.  
  
7.  Per separare i dati di traccia visualizzati, scegliere **Visualizzazione a gruppi** dal menu **Visualizza** per annullare la selezione. Per tornare alla visualizzazione a gruppi, scegliere di nuovo **Visualizzazione a gruppi** dal menu **Visualizza** per confermare di nuovo la selezione.  
  
### <a name="to-group-and-aggregate-data-columns-in-a-trace"></a>Per raggruppare e aggregare le colonne di dati di una traccia  
  
1.  Aprire un file o una tabella di traccia esistente.  
  
2.  Scegliere **Proprietà** dal menu **File**.  
  
3.  Nella finestra di dialogo **Proprietà file di traccia** o **Proprietà tabella di traccia** fare clic sulla scheda **Selezione eventi** .  
  
4.  Nella scheda **Selezione eventi** fare clic su **Organizza colonne**.  
  
5.  Nella finestra di dialogo **Organizza colonne** selezionare la colonna in base alla quale raggruppare e aggregare gli eventi di traccia visualizzati. Fare clic su **Su** per spostare il nome della colonna in **Gruppi**. Se necessario, è possibile usare i pulsanti **Su** e **Giù** per modificare la disposizione delle colonne rimanenti in **Colonne** .  
  
6.  Fare clic su **OK** nella finestra di dialogo **Organizza colonne** e quindi su **OK** nella finestra di dialogo **Proprietà tabella di traccia** o **Proprietà file di traccia** .  
  
     Dopo avere fatto clic su **OK** nella finestra di dialogo **Proprietà tabella di traccia** o **Proprietà file di traccia** , le colonne di dati verranno riorganizzate nella traccia visualizzata. Tutti gli altri eventi delle colonne di dati verranno aggregati nella colonna di dati spostata in precedenza nell'elenco **Gruppi** . Fare clic sul segno più ( **+** ) a sinistra dell'evento nella colonna di dati selezionata per l'aggregazione per espanderla e visualizzare tutti gli eventi dello stesso tipo. La colonna selezionata per l'aggregazione rimane fissa, ma è possibile scorrere a destra o a sinistra per visualizzare le altre colonne.  
  
7.  Per tornare a una visualizzazione normale dei dati di traccia, scegliere **Visualizzazione aggregata** dal menu **Visualizza** per annullare la selezione. Per tornare alla visualizzazione aggregata, scegliere di nuovo **Visualizzazione aggregata** dal menu **Visualizza** per confermare di nuovo la selezione. È anche possibile scegliere **Visualizzazione a gruppi** dal menu **Visualizza** per visualizzare gli eventi di traccia raggruppati senza comprimerli.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare una traccia &#40;SQL Server Profiler&#41;](create-a-trace-sql-server-profiler.md)   
 [Aprire una tabella di traccia &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)   
 [Aprire un file di traccia &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md)  
  
  
