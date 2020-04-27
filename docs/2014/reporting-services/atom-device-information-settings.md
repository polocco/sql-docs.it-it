---
title: Impostazioni relative alle informazioni sul dispositivo ATOM | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fe4a56a4-5552-423c-85c1-895e2e212fee
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bdbac1500063accf868d4b538b82ba9f3b5aebb0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66109975"
---
# <a name="atom-device-information-settings"></a>Impostazioni relative alle informazioni sul dispositivo ATOM
  Le impostazioni relative alle informazioni sul dispositivo per l'estensione per il rendering Atom supportano l'invio del nome di un feed Atom e della codifica dei caratteri da utilizzare.  
  
 Nella tabella seguente sono elencate le impostazioni relative alle informazioni sul dispositivo per il rendering in un documento di servizio dati.  
  
|Impostazione|valore|  
|-------------|-----------|  
|`DataFeed`|Se specificato, esegue il rendering del feed Atom che corrisponde al nome del feed fornito in questa impostazione. In caso contrario, esegue il rendering del documento di servizio Atom per il report. Identificatore univoco del feed di dati generato automaticamente. Questo valore viene utilizzato internamente e non deve essere modificato.|  
|**Codifica**|Il nome IANA (Internet Assigned Numbers Authority) di una codifica dei caratteri supportata da .NET Framework. Il valore predefinito è `UTF-8`. Esempi di altri valori includono ASCII, UTF-7 e UTF-16.|  
  
## <a name="see-also"></a>Vedi anche  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Passaggio delle impostazioni delle informazioni sul dispositivo alle estensioni per il rendering](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personalizzare i parametri di estensione per il rendering in RSReportServer. config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Riferimento tecnico &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
