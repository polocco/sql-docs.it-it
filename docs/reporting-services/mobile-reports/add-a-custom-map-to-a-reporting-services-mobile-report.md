---
title: Aggiungere una mappa personalizzata a un report di Reporting Services per dispositivi mobili | Microsoft Docs
description: È possibile aggiungere una mappa personalizzata a un report di Reporting Services per dispositivi mobili. Questo articolo descrive come caricare e connettere i dati a una mappa personalizzata.
ms.date: 01/31/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.topic: conceptual
ms.assetid: fd259b95-bb58-4eb1-a436-6aa12fc6f5f2
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a1c15d5b5155d68f94a1672ca55654485c6b1835
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "79448340"
---
# <a name="add-a-custom-map-to-a-reporting-services-mobile-report"></a>Aggiungere una mappa personalizzata a un report di Reporting Services per dispositivi mobili
Le mappe personalizzate richiedono due file:  
* Un file SHP per geometrie di forma  
* Un file DBF per i metadati  
  
Altre informazioni sulle [mappe personalizzate nei report di Reporting Services per dispositivi mobili](../../reporting-services/mobile-reports/custom-maps-in-reporting-services-mobile-reports.md).  
  
Archiviare i due file nella stessa cartella. I nomi dei due file devono corrispondere (ad esempio, canada.shp e canada.dbf). La prima colonna dei metadati (file DBF) viene usata per la corrispondenza con il valore del nome della forma corrispondente (chiave), che verrà usato durante il popolamento dei dati nella mappa.
  
## <a name="load-a-custom-map"></a>Caricare una mappa personalizzata  
  
1. Nella scheda **Layout** selezionare un tipo di mappa tra **Mappa termica con sfumature**, **Mappa termica con interruzioni intervallo** o **Mappa a bolle**, trascinarla nell'area di progettazione e impostare le dimensioni desiderate.  
  
   ![SSMRP_MapsGallery](../../reporting-services/mobile-reports/media/ssmrp-mapsgallery.png)  
  
2. Nella vista **Layout** > riquadro **Proprietà visive** > **Mappa** selezionare **Mappa personalizzata da file**.   
  
   ![SSMRP_SelectCustomMap](../../reporting-services/mobile-reports/media/ssmrp-selectcustommap.png)  
  
3. Nella finestra di dialogo **Apri** selezionare il percorso dei file SHP e DBF e selezionarli entrambi.   
  
   ![SSMRP_SelectDBFandSHP](../../reporting-services/mobile-reports/media/ssmrp-selectdbfandshp.png)  
  
## <a name="connect-data-to-a-custom-map"></a>Connettere i dati a una mappa personalizzata  
Quando si aggiunge la mappa personalizzata al report per la prima volta, [!INCLUDE[SS_MobileReptPub_Short](../../includes/ss-mobilereptpub-short.md)] lo popola con dati geografici simulati.  
  
![SSMRP_MapsData](../../reporting-services/mobile-reports/media/ssmrp-mapsdata.png)  
  
La visualizzazione di dati reali nella mappa personalizzata è uguale alla visualizzazione dei dati nelle mappe predefinite. Per visualizzare i dati, seguire la procedura in [Eseguire il mapping nei report di Reporting Services per dispositivi mobili](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md) .  
  
### <a name="see-also"></a>Vedere anche  
- [Custom maps in Reporting Services mobile reports](../../reporting-services/mobile-reports/custom-maps-in-reporting-services-mobile-reports.md)  
- [Eseguire il mapping nei report di Reporting Services per dispositivi mobili](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)  
- [Creare e pubblicare report per dispositivi mobili con SQL Server Mobile Report Publisher](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)   
  
  
  
  
