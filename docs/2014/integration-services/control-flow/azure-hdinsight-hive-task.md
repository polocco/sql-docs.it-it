---
title: Attività Hive di Azure HDInsight | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afphivetask.f1
- sql11.dts.designer.afphivetask.f1
ms.assetid: e1896c73-128a-4128-9814-3e01f7dfe19b
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 428677947f864175c97c52ed2687c4ffcf952703
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84919907"
---
# <a name="azure-hdinsight-hive-task"></a>Attività Hive di Azure HDInsight
Usare l' **attività Hive di Azure HDInsight** per eseguire uno script Hive in un cluster di Azure HDInsight.
     
Per aggiungere un' **attività Hive di Azure HDInsight**, trascinare l'attività in Progettazione SSIS e farvi doppio clic oppure clic con il pulsante destro del mouse, quindi scegliere **Modifica** per visualizzare la finestra di dialogo seguente relativa all' **editor dell'attività Hive di Azure HDInsight** .  
  
 L'elenco seguente contiene i campi di questa finestra di dialogo.  
  
1.  Per il campo **HDInsightConnection** selezionare un'istanza di Gestione connessione Azure HDInsight esistente oppure creare una nuova istanza che faccia riferimento al cluster HDInsight di Azure usato per eseguire lo script.
  
2.  Per il campo **AzureStorageConnection** selezionare un'istanza di Gestione connessione Archiviazione di Azure esistente oppure creare una nuova istanza che faccia riferimento all'account di archiviazione di Azure associato al cluster. Questa operazione è necessaria solo se si vuole scaricare l'output dell'esecuzione dello script e i log degli errori.
 
3.  Per il campo **BlobContainer** specificare il nome del contenitore di archiviazione associato al cluster. Questa operazione è necessaria solo se si vuole scaricare l'output dell'esecuzione dello script e i log degli errori.
  
4.  Per il campo **LocalLogFolder** specificare la cartella in cui verranno scaricati l'output dell'esecuzione dello script e i log degli errori. Questa operazione è necessaria solo se si vuole scaricare l'output dell'esecuzione dello script e i log degli errori.   
  
5.  È possibile specificare due modalità di esecuzione dello script Hive:
  
    1.  **Script inline**: specificare il campo **Script** digitando lo script inline da eseguire nella finestra di dialogo **Immetti script**.
  
    2.  **File script**: caricare il file script in Archiviazione BLOB di Azure e specificare il campo **BlobName**. Se il BLOB non è presente nell'account di archiviazione o nel contenitore predefinito associato al cluster HDInsight, è necessario specificare i campi **ExternalStorageAccountName** e **ExternalBlobContainer**. Per un BLOB esterno, assicurarsi che sia configurato come accessibile pubblicamente.  
  
     Se vengono specificati entrambi, verrà usato il file script e lo script inline verrà ignorato.
