---
title: Set di righe DISCOVER_XEVENT_TRACE_DEFINITION | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: e1ce2d2d-f994-4318-801a-ee0385aecd84
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 826389eafb4fdf6a32e8d3b62ebfc1f333b62d4d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/25/2020
ms.locfileid: "62731913"
---
# <a name="discover_xevent_trace_definition-rowset"></a>Set di righe DISCOVER_XEVENT_TRACE_DEFINITION
  Vengono fornite informazioni sulle tracce XEvent attualmente attive nel server.  
  
 **Si applica a:** modelli tabulari, modelli multidimensionali  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il set di righe `DISCOVER_XEVENT_TRACE_DEFINITION` contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Descrizione|  
|-----------------|--------------------|------------|-----------------|  
|`Data`|`DBTYPE_WSTR`||Definizione XML della traccia XEvent.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|valore|  
|--------------|-----------|  
|GUID|a07ccd1c-8148-11d0-87bb-00c04fc33942|  
|string|DISCOVER_XEVENT_TRACE_DEFINITION|  
  
## <a name="see-also"></a>Vedi anche  
 [Set di righe dello schema XML for Analysis](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/xml-for-analysis-schema-rowsets)   
 [Usare SQL Server eventi estesi &#40;&#41; XEvent per monitorare Analysis Services](../instances/monitor-analysis-services-with-sql-server-extended-events.md)   
 [Utilizzare DMV per monitorare Analysis Services](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
