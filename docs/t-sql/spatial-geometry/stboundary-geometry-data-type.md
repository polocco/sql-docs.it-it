---
title: STBoundary (tipo di dati geometry) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STBoundary (geometry Data Type)
- STBoundary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STBoundary (geometry Data Type)
ms.assetid: f0551674-e6e8-4926-9038-df03f2c807d7
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 2f99cc9931a136d7b3d3919687e5e5b8ffee269c
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/21/2020
ms.locfileid: "86555999"
---
# <a name="stboundary-geometry-data-type"></a>STBoundary (tipo di dati geometry)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Restituisce il limite di un'istanza **geometry**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STBoundary ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Tipi restituiti
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
## <a name="remarks"></a>Osservazioni  
 `STBoundary()` restituisce un'istanza **GeometryCollection** vuota se gli endpoint per un'istanza **LineString**, **CircularString** o **CompoundCurve** corrispondono.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-stboundary-on-a-linestring-instance-with-different-endpoints"></a>R. Utilizzo di STBoundary() in un'istanza LineString con endpoint diversi  
 Nell'esempio seguente viene creata un'istanza `LineString``geometry`. `STBoundary()` restituisce il limite dell'istanza `LineString`.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 0 2, 2 0)', 0);  
SELECT @g.STBoundary().ToString();  
```  
  
### <a name="b-using-stboundary-on-a-linestring-instance-with-the-same-endpoints"></a>B. Utilizzo di STBoundary() in un'istanza LineString con gli stessi endpoint  
 Nell'esempio seguente viene creata un'istanza `LineString` valida con gli stessi endpoint. Tramite `STBoundary()` viene restituita un'istanza `GeometryCollection` vuota.  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 0 2, -2 2, 0 0)', 0);  
 SELECT @g.STBoundary().ToString();
 ```  
  
### <a name="c-using-stboundary-on-a-curvepolygon-instance"></a>C. Utilizzo di STBoundary() in un'istanza CurvePolygon  
 Nell'esempio seguente viene utilizzato `STBoundary()` in un'istanza `CurvePolygon` vuota. Tramite `STBoundary()` viene restituita un'istanza `CircularString`.  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::STGeomFromText('CURVEPOLYGON(CIRCULARSTRING(0 0, 2 2, 0 2, -2 2, 0 0))', 0);  
 SELECT @g.STBoundary().ToString();
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze di geometria](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
