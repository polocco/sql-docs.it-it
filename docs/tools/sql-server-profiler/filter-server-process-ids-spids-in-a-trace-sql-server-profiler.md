---
title: Filtrare gli ID del processo server (SPID) in un file di traccia
titleSuffix: SQL Server Profiler
description: Informazioni su come limitare l'output di traccia in SQL Server Profiler applicando un filtro all'ID del processo server (SPID).
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: f5945c39-be6b-4632-91cb-92066c80e188
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 5e4c3d5b6d69b55a588b9be957d2a3226c6b4719
ms.sourcegitcommit: b8933ce09d0e631d1183a84d2c2ad3dfd0602180
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2020
ms.locfileid: "83152062"
---
# <a name="filter-server-process-ids-spids-in-a-trace-sql-server-profiler"></a>Filtrare gli ID del processo server (SPID) in una traccia (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In questo argomento viene descritta la procedura per il filtraggio degli identificatori del processo server (SPID) in una traccia mediante [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
### <a name="to-filter-system-ids-in-a-trace"></a>Per filtrare gli ID di sistema in una traccia  
  
1.  Scegliere **Nuova traccia** dal menu **File**e quindi connettersi a un'istanza di SQL Server.  
  
     Verrà visualizzata la finestra di dialogo **Proprietà traccia** .  
  
    > [!NOTE]  
    >  Se l'opzione **Avvia traccia non appena viene stabilita una connessione** è selezionata, la finestra di dialogo **Proprietà traccia** non viene visualizzata e viene invece avviata la traccia. Per disattivare questa impostazione, scegliere **Opzioni** dal menu **Strumenti** e deselezionare la casella di controllo **Avvia traccia non appena viene stabilita una connessione**.  
  
2.  Nella casella **Nome traccia** digitare un nome per la traccia.  
  
3.  Nell'elenco di nomi **Modello** selezionare un modello di traccia.  
  
4.  Facoltativamente, è possibile specificare un file o una tabella di destinazione in cui salvare i risultati della traccia.  
  
5.  Nella scheda **Selezione eventi** fare clic sull'intestazione di colonna **SPID** per visualizzare la finestra di dialogo **Modifica filtro**. È anche possibile fare clic con il pulsante destro del mouse sull'intestazione di colonna e scegliere **Modifica filtro colonne**. Se non viene visualizzata la colonna **SPID** , selezionare la casella **Mostra tutte le colonne** .  
  
6.  Nella finestra di dialogo **Modifica filtro** espandere l'operatore di confronto appropriato e immettere uno SPID come valore di confronto.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
