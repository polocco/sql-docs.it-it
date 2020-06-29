---
title: Origine di Azure Data Lake Store | Microsoft Docs
ms.custom: ''
ms.date: 06/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSSRC.F1
- SQL11.DTS.DESIGNER.AFPADLSSRC.F1
ms.assetid: 7d9e8457-62aa-4aea-98ee-7d1121dfae4f
author: yualan
ms.author: chugu
ms.openlocfilehash: e5bce25e303b055d734da6a00c73851f4eb0d7ec
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439388"
---
# <a name="azure-data-lake-store-source"></a>Origine di Azure Data Lake Store
  Il componente **Origine di Azure Data Lake Store** consente a un pacchetto SSIS di leggere dati da Azure Data Lake Store. I formati di file supportati sono: testo e AVRO.
  
## <a name="configure-the-azure-data-lake-store-source"></a>Configurare Origine di Azure Data Lake Store 
  
1.  Per visualizzare l'editor per Origine di Azure Data Lake Store, trascinare la selezione **Origine di Azure Data Lake Store** nell'area di progettazione del flusso di dati e fare doppio clic per aprire l'editor.  
  
2.  Nel campo **Gestione connessioni di Azure Data Lake Store** specificare un'istanza esistente di Gestione connessioni di Azure Data Lake Store o creare una nuova istanza che faccia riferimento a un servizio di Azure Data Lake Store.  
  
    1.  Per il campo **Percorso File** , specificare il percorso del file di origine in Azure Data Lake Store.   
  
    2.  Per il campo **Formato file** specificare il formato file che si vuole usare.  
  
        Se il formato del file corrisponde a testo, è necessario impostare il valore **Carattere delimitatore di colonna** . Selezionare anche **Nomi di colonne nella prima riga di dati** se la prima riga nel file contiene i nomi di colonna.  
  
3.  Dopo aver specificato le informazioni di connessione, passare alla pagina **Colonne** per eseguire il mapping delle colonne di origine alle colonne di destinazione per il flusso di dati SSIS.  
