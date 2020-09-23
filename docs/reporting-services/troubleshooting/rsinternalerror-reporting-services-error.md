---
title: rsInternalError - Errore di Reporting Services | Microsoft Docs
description: "Questa pagina di riferimento degli errori contiene informazioni sull'ID evento \"rsInternalError\": Errore interno nel server di report. Per altre informazioni, vedere il log degli errori."
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: troubleshooting
ms.topic: conceptual
helpviewer_keywords:
- rsInternalError
ms.assetid: 52613d52-fc78-4870-93f0-7d393ab9c335
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d8df18bf9487d1d8797eff4e60f5ec5eefb87c4f
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2020
ms.locfileid: "87394722"
---
# <a name="rsinternalerror---reporting-services-error"></a>rsInternalError - Errore di Reporting Services
    
## <a name="details"></a>Dettagli  
  
|Category|Valore|  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|rsInternalError|  
|Origine evento|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|Componente|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Testo del messaggio|Errore interno nel server di report. Per altre informazioni, vedere il log degli errori.|  
  
## <a name="explanation"></a>Spiegazione  
 Si tratta di un messaggio di errore generico, spesso seguito da un errore più descrittivo che include ulteriori dettagli.  
  
 Gli errori interni non sono comuni. Se viene visualizzato questo errore, nei log di traccia del server di report sono disponibili ulteriori informazioni. Se inoltre si esegue il servizio come amministratore locale nello stesso computer in cui si è verificato l'errore, è possibile visualizzare lo stack di chiamate per ottenere ulteriori informazioni.  
  
## <a name="user-action"></a>Azione dell'utente  
 Per stabilire la causa specifica di questo messaggio, esaminare i file di log del server di report, disponibili in \Microsoft SQL Server\MSRS12.\<instancename >\Reporting Services\LogFiles. Per altre informazioni, vedere [File di log e origini di Reporting Services](../../reporting-services/report-server/reporting-services-log-files-and-sources.md).  
  
 Per visualizzare lo stack di chiamate, fare clic con il pulsante destro del mouse nella pagina in cui si è verificato l'errore e scegliere **Visualizza origine**. Per visualizzare lo stack di chiamate, è necessario disporre delle autorizzazioni di amministratore nello stesso computer in cui si verifica l'errore.  
  
 Se non sono disponibili informazioni aggiuntive, è possibile riprovare a eseguire la richiesta.  
  
## <a name="internal-only"></a>Solo interno  
  
## <a name="see-also"></a>Vedere anche  
 [Avviare e arrestare il servizio del server di report](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)  
  
  
