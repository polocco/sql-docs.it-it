---
title: Origine file HDFS | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.designer.hdfsfilesrc.f1
ms.assetid: f8cda200-c389-4a2e-8ee9-5d59b326aac1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3be6be9e43d6e9e643ea76c4d4a08cd5b370b343
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2020
ms.locfileid: "86920273"
---
# <a name="hdfs-file-source"></a>Origine file HDFS

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Il componente Origine file HDFS consente a un pacchetto SSIS di leggere dati da un file HDFS. I formati di file supportati sono Testo e AVRO. Le origini ORC non sono supportate.  
  
 Per configurare Origine file HDFS, trascinare e rilasciare Origine file HDFS nella finestra di progettazione del flusso di dati e fare doppio clic sul componente per aprire l'editor.  
  
 ![Editor origine file HDFS](../../integration-services/data-flow/media/hdfs-file-source.png "Editor origine file HDFS")  
  
## <a name="options"></a>Opzioni  
 Configurare le opzioni seguenti nella scheda **Generale** della finestra di dialogo **Editor origine file HDFS** .  
  
|Campo|Descrizione|  
|-----------|-----------------|  
|**Connessione Hadoop**|Specificare un'istanza esistente di Gestione connessione Hadoop o crearne una nuova. Questa istanza di Gestione connessione indica dove sono ospitati i file HDFS.|  
|**Percorso file**|Specificare il nome del file HDFS.|  
|**Formato file**|Specificare il formato del file HDFS. Le opzioni disponibili sono Testo e Avro. Le origini ORC non sono supportate.|  
|**Carattere delimitatore di colonna**|Se si seleziona il formato testo, specificare il carattere delimitatore di colonna.|  
|**Nomi di colonna nella prima riga di dati**|Se si seleziona il formato testo, indicare se la prima riga del file contiene i nomi delle colonne.|  
  
 Dopo aver configurato queste opzioni, selezionare la scheda **Colonne** per eseguire il mapping delle colonne di origine alle colonne di destinazione del flusso di dati.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione connessione Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)   
 [Destinazione file HDFS](../../integration-services/data-flow/hdfs-file-destination.md)  
  
  
