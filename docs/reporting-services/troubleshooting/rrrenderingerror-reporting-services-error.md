---
title: rrRenderingError - Errore di Reporting Services | Microsoft Docs
description: "Questa pagina di riferimento degli errori contiene informazioni sull'ID evento \"rrRenderingError\": Errore durante il rendering del report."
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: troubleshooting
ms.topic: conceptual
helpviewer_keywords:
- rrRenderingError
ms.assetid: 0751efc3-b81b-44ee-8aac-8560f86ca322
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 67e43301ac1582bd3cfc085a9ad6412724d4ec92
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87395289"
---
# <a name="rrrenderingerror---reporting-services-error"></a>rrRenderingError - Errore di Reporting Services
    
## <a name="details"></a>Dettagli  
  
|Category|Valore|  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|rrRenderingError|  
|Origine evento|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings.resources.Strings|  
|Componente|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Testo del messaggio|Errore durante il rendering del report. (rrRenderingError) %1|  
  
## <a name="explanation"></a>Spiegazione  
 Questo messaggio viene restituito quando [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] non è in grado di eseguire il rendering del report o di esportarlo.  
  
 Un messaggio che indica che le dimensioni non sono supportate viene in genere visualizzato quando le dimensioni della pagina RDL non sono valide. Specificare una dimensione RDL della pagina valida, quindi effettuare un nuovo tentativo.  
  
 Un messaggio che indica che l'unità di misura delle dimensioni RDL non è supportata viene in genere visualizzato quando il tipo di unità di misura specificato non è supportato. Tipi di unità validi sono cm, in, mm, PC e pt. Specificare un tipo di unità valido, quindi effettuare un nuovo tentativo.  
  
 Un messaggio che indica che la dimensione negativa non è supportata viene in genere visualizzato quando viene specificata una dimensione negativa, ad esempio -5, per le dimensioni della pagina. Specificare un numero positivo per la dimensione della pagina, quindi effettuare un nuovo tentativo.  
  
 Un messaggio che indica che le dimensioni RDL specificate non sono comprese nell'intervallo dei valori consentiti viene in genere visualizzato quando la misura relativa alle dimensioni della pagina non rientra nelle dimensioni valide per i margini della pagina. Specificare una misura per le dimensioni della pagina che sia all'interno delle dimensioni di margine di pagina valide.  
  
 Un messaggio che indica che il colore specificato non è supportato viene in genere visualizzato quando un colore specificato in RDL non è valido. Scegliere un colore supportato da RDL, quindi effettuare un nuovo tentativo.  
  
 Un messaggio che indica che l'etichetta dell'azione è facoltativa solo quando si utilizza una sola azione e che l'aggiunta di più azioni richiede un'etichetta per ognuna di esse viene in genere visualizzato quando un'etichetta di un'azione specificata non è valida. Specificare un'etichetta valida per ciascuna azione.  
  
 Un messaggio che indica che l'argomento dello stile deve essere di un tipo specifico viene in genere visualizzato quando viene specificato un valore di stile non corretto per il tipo di dati. La specifica RDL identifica i tipi validi che è possibile usare nei valori dello stile di diversi elementi RDL. Ad esempio, un valore di stile non corretto per il colore di sfondo è "2 pt" e un valore non corretto per l'altezza è "true". Specificare un valore corretto, quindi effettuare un nuovo tentativo.  
  
 Un messaggio che indica che lo stile del bordo non è supportato viene in genere visualizzato quando lo stile del bordo specificato non è valido. Specificare un stile del bordo supportato, quindi effettuare un nuovo tentativo.  
  
 Un messaggio che indica che il tipo MIME per l'immagine non è supportato viene in genere visualizzato quando il tipo MIME specificato per un elemento del report di immagine non è valido. Specificare un tipo MIME supportato per l'elemento del report, quindi riprovare.  
  
 Un messaggio che indica che il numero di righe supera il numero massimo di righe possibili per foglio di lavoro viene in genere visualizzato quando viene superato il numero massimo di righe in un foglio di lavoro di Excel. Un foglio di lavoro di Excel supporta fino a 65.000 righe.  
  
 Un messaggio che indica che il numero di colonne supera il numero massimo di colonne possibili per foglio di lavoro viene in genere visualizzato quando viene superato il numero massimo di colonne in un foglio di lavoro di Excel.  
  
## <a name="user-action"></a>Azione dell'utente  
  
## <a name="internal-only"></a>Solo interno  
  
