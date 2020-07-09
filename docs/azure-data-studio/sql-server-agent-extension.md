---
title: Estensione SQL Server Agent
description: Installare e usare l'estensione SQL Server Agent (anteprima) per Azure Data Studio
ms.custom: seodec18
ms.date: 09/24/2018
ms.reviewer: alayu, maghan, sstein
ms.prod: azure-data-studio
ms.technology: ''
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: 3cdbfc4adc32156f838ee3aeca726c2ebd92bd0c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85758361"
---
# <a name="sql-server-agent-extension-preview"></a>Estensione SQL Server Agent (anteprima)

L'estensione SQL Server Agent (anteprima) è un'estensione per la gestione e la risoluzione di problemi dei processi e della configurazione di SQL Agent. Questa estensione è attualmente disponibile in anteprima.

Le azioni principali comprendono:
- Elencare i processi di SQL Server Agent configurati in SQL Server
- Visualizzare la cronologia dei processi con i risultati della loro esecuzione
- Avviare e arrestare i processi tramite il controllo di base dei processi

## <a name="install-the-sql-server-agent-extension"></a>Installare l'estensione SQL Server Agent

1. Per aprire Gestione estensioni e accedere alle estensioni disponibili, selezionare l'icona delle estensioni oppure l'opzione **Estensioni** dal menu **Visualizza**.
2. Selezionare un'estensione disponibile per visualizzarne i dettagli.

   ![Installare Agent](media/extensions/sql-server-agent-extension/install-sql-agent.png)

1. Selezionare l'estensione desiderata e **installarla**.
2. Selezionare **Ricarica** per abilitare l'estensione (necessario solo la prima volta che si installa un'estensione).
1. Passare al dashboard di gestione facendo clic con il pulsante destro del mouse sul server o sul database in uso e scegliendo quindi **Gestisci**.
2. Le estensioni installate vengono visualizzate come schede nel dashboard di gestione:

   ![Visualizzare Agent](media/extensions/sql-server-agent-extension/view-sql-agent.png)

## <a name="view-jobs"></a>Visualizzare i processi

Quando ci si connette all'estensione SQL Server Agent, il primo elemento visualizzato è un elenco di tutti i processi di Agent.

   ![Visualizzare i processi](media/extensions/sql-server-agent-extension/job-view.png)

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su SQL Server Agent, [consultare la documentazione di riferimento](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent?view=sql-server-2017).


