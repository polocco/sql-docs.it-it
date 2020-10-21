---
description: identificatori SRID (Spatial Reference Identifier)
title: Identificatori SRID (Spatial Reference Identifier) | Microsoft Docs
ms.date: 03/29/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Spatial Reference Identifiers (SRIDs)
- geodetic spatial data [SQL Server], identifiers
- SRID
ms.assetid: 0612658a-7d1b-4178-bdc2-42b914ea31a7
author: MladjoA
ms.author: mlandzic
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 40c2a26425815d75ab000000e2639320769b01b9
ms.sourcegitcommit: a5398f107599102af7c8cda815d8e5e9a367ce7e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/13/2020
ms.locfileid: "92006233"
---
# <a name="spatial-reference-identifiers-srids"></a>identificatori SRID (Spatial Reference Identifier)
[!INCLUDE [SQL Server Azure SQL Database Azure SQL Managed Instance](../../includes/applies-to-version/sql-asdb-asdbmi.md)]
  Ogni istanza spaziale ha un identificatore SRID. L'identificatore SRID corrisponde a un sistema di riferimento spaziale basato sullo specifico ellissoide utilizzato per il mapping terra piatta o terra rotonda.  
  
 Una colonna spaziale può contenere oggetti con identificatori SRID. Tuttavia, solo le istanze spaziali con lo stesso identificatore SRID possono essere utilizzate se si eseguono operazioni con i metodi dei dati spaziali [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sui dati. Il risultato di qualsiasi metodo spaziale derivato da due istanze dei dati spaziali è valido solo se quelle istanze hanno lo stesso identificatore SRID, basato sulla stessa unità di misura, data e proiezione utilizzata per determinare le coordinate delle istanze. Le unità di misura più comuni di un identificatore SRID sono metri o metri quadrati.  
  
 Se due istanze spaziali non hanno lo stesso SRID, i risultati di un metodo tipo dati **geometry** o **geography** usati nelle istanze restituiranno NULL. Ad esempio, affinché il seguente termine di predicato restituisca un risultato non NULL, le due istanze **geometry** , `geometry1` e `geometry2`, devono avere lo stesso identificatore SRID:  
  
 `geometry1.STIntersects(geometry2) = 1`  
  
> [!NOTE]  
>  Il sistema SRID è definito dallo standard [European Petroleum Survey Group (EPSG)](https://go.microsoft.com/fwlink/?LinkId=99349) , un set di standard sviluppato per cartografia, rilevamenti e archiviazione dei dati geodetici. Questo standard è di proprietà di Oil and Gas Producers (OGP) Surveying and Positioning Committee.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica dei tipi di dati spaziali](../../relational-databases/spatial/spatial-data-types-overview.md)  
  
  
