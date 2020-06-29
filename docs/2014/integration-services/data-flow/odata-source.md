---
title: Origine OData | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.ODATASOURCE.F1
ms.assetid: cc9003c9-638e-432b-867e-e949d50cec90
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 86f055efd5ef4cbb41d7e600d88b4704bf4e47b1
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "85431888"
---
# <a name="odata-source"></a>Origine OData
  Utilizzare il componente di origine OData in un pacchetto SSIS per utilizzare i dati dai servizi Protocollo OData (Open Data). Il componente supporta i formati dati JSON e ATOM, nonché i protocolli v3 e v2 OData.  
  
> [!NOTE]  
>  L'origine OData può essere utilizzata per eseguire letture da elenchi SharePoint. Per visualizzare tutti gli elenchi nel server SharePoint, usare l'URL seguente: http:// \<server> /_vti_bin/listdata.svc. Per ulteriori informazioni sulle convenzioni per l'URL di SharePoint, vedere la pagina relativa all' [interfaccia REST di SharePoint Foundation](https://msdn.microsoft.com/library/ff521587.aspx).  
  
## <a name="odata-format"></a>Formato OData  
 I risultati restituiti dalla maggior parte dei servizi OData sono in più formati. È possibile specificare il formato del set di risultati utilizzando l'opzione query $format. I formati quali JSON e JSON Light sono più efficienti di ATOM/XML e possono garantire prestazioni migliori quando si trasferiscono grandi quantità di dati. Nella tabella seguente vengono forniti i risultati dei test di esempio. Come si può notare, si verifica un miglioramento delle prestazioni del 30-53% quando si passa dal formato ATOM a JSON e un miglioramento del 67% quando si passa da ATOM al nuovo formato JSON Light, disponibile in WCF Data Services 5.1.  
  
|||||  
|-|-|-|-|  
|Righe|ATOM|JSON|JSON (Light)|  
|10000|113 secondi|74 secondi|68 secondi|  
|1000000|1110 secondi|853 secondi|665 secondi|  
  
> [!NOTE]  
>  Con l'origine SSIS OData viene utilizzato ODataLib 5.5.0 per analizzare i feed OData ed è possibile leggere tutti i formati supportati da questa libreria.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
-   [Installare e disinstallare il componente di origine OData](../install-and-uninstall-odata-source-component.md)  
  
-   [Esercitazione: uso dell'origine OData &#91;SSIS&#93;](tutorial-using-the-odata-source.md)  
  
-   [Modificare la query di origine OData in fase di esecuzione](modify-odata-source-query-at-runtime.md)  
  
-   [Editor origine OData &#40;pagina Connessione &#41;](../odata-source-editor-connection-page.md)  
  
-   [Editor origine OData &#40;pagina Colonne&#41;](../odata-source-editor-columns-page.md)  
  
-   [Editor origine OData &#40;pagina Output degli errori&#41;](../odata-source-editor-error-output-page.md)  
  
-   [Proprietà dell'origine OData](odata-source-properties.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione connessione OData](../connection-manager/odata-connection-manager.md)  
  
  
