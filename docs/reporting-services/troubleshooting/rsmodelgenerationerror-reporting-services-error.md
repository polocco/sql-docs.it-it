---
title: rsModelGenerationError - Errore di Reporting Services | Microsoft Docs
description: "Questa pagina di riferimento degli errori contiene informazioni sull'ID evento \"rsModelGenerationError\": Errore durante la generazione del modello."
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: troubleshooting
ms.topic: conceptual
helpviewer_keywords:
- rsModelGenerationError
ms.assetid: 3a0ad63f-87f9-4ca1-b0c2-c85fa991634a
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: bfeb477ac1830d9604e3d794e96e807548639671
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487230"
---
# <a name="rsmodelgenerationerror---reporting-services-error"></a>rsModelGenerationError - Errore di Reporting Services
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|rsRenderingError|  
|Origine evento|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|Componente|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Testo del messaggio|Errore durante la generazione del modello. (rsModelGenerationError) (ReportingServicesLibrary) %1|  
  
## <a name="explanation"></a>Spiegazione  
 Il modello di report non è stato generato. In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005 SP1 e versioni precedenti questo errore viene visualizzato con maggior probabilità quando l'oggetto System.Data.DataSet non riesce a gestire una tabella o una relazione all'interno dello schema del database, ad esempio quando vengono definite due chiavi esterne nella stessa colonna di una tabella.  
  
## <a name="user-action"></a>Azione dell'utente  
 Per determinare il motivo specifico che ha causato la visualizzazione del messaggio, esaminare i file di log del server di report, nel percorso \Microsoft SQL Server\\<Istanza di SQL Server\>\Reporting Services\LogFiles.  
  
## <a name="internal-only"></a>Solo interno  
  
