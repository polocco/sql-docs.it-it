---
title: Finestra di dialogo Proprietà origine dati, credenziali | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.datasourceproperties.credentials.f1
- "10100"
ms.assetid: 14c3eeb6-d37b-4fda-967b-43afcdb48119
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ed5b58aa9a4fe81a55e602fb61f673bf10059ee7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66109447"
---
# <a name="data-source-properties-dialog-box-credentials"></a>Finestra di dialogo Proprietà origine dati, Credenziali
  Selezionare **Credenziali** nella finestra di dialogo **Proprietà origine dati** per visualizzare e modificare le credenziali per la connessione a un'origine dati nel report. Le credenziali specificate vengono utilizzate per accedere all'origine dati e per memorizzare una copia dei dati nella cache per l'anteprima dei report. Per altre informazioni sulla modalità di memorizzazione nella cache dei dati di anteprima, vedere [Anteprima dei report](reports/previewing-reports.md). Per altre informazioni sulle credenziali, vedere [Specificare le credenziali e le informazioni sulla connessione per le origini dati del report](report-data/specify-credential-and-connection-information-for-report-data-sources.md).  
  
## <a name="options"></a>Opzioni  
 **Usa autenticazione di Windows (sicurezza integrata)**  
 Selezionare questa opzione per utilizzare l'autenticazione di Windows.  
  
 **Usa il nome utente e la password seguenti**  
 Selezionare questa opzione per specificare nome utente e password specifici. Per origini dei dati condivise: quando si pubblica il progetto del server di report sul server di destinazione, il nome utente e la password vengono salvati come credenziali archiviate per il database. Se si desidera utilizzare il nome utente e la password come credenziali di Windows, è possibile modificare le proprietà dell'origine dei dati condivisa pubblicata sul server di destinazione. Per altre informazioni, vedere [Creare, eliminare o modificare un'origine dei dati condivisa &#40;Gestione report&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md).  
  
 **Nome utente**  
 Consente di digitare un nome utente da utilizzare per l'accesso all'origine dei dati.  
  
 **Password**  
 Consente di digitare una password da utilizzare per l'accesso all'origine dei dati.  
  
 **Richiedi credenziali**  
 Selezionare questa opzione per richiedere le credenziali durante l'esecuzione del report.  
  
 **Immettere una stringa di richiesta**  
 Digitare una frase con cui chiedere all'utente di specificare le credenziali di accesso per l'origine dati.  
  
 **Nessuna credenziale**  
 Selezionare questa opzione se non si desidera che vengano specificate credenziali per l'origine dati. Questa opzione funziona solamente se l'origine dati non accetta le credenziali o se il passaggio di queste ultime avviene in altro modo.  
  
## <a name="see-also"></a>Vedi anche  
 [Finestra di dialogo Proprietà origine dati, generale](../../2014/reporting-services/data-source-properties-dialog-box-general.md)   
 [Specificare le credenziali e le informazioni sulla connessione per le origini dati del report](report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Connessioni dati, origini dati e stringhe di connessione in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
