---
description: STCurveToLine (tipo di dati geometry)
title: STCurveToLine (tipo di dati geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STCurveToLine method (geometry)
ms.assetid: abc80b32-4152-4e10-b816-798b901e0ac5
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: e4eb3aa1d61d49b70a9526f352807a1569dfb7e8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88488089"
---
# <a name="stcurvetoline-geometry-data-type"></a>STCurveToLine (tipo di dati geometry)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

Restituisce un'approssimazione poligonale di un'istanza **geometry** contenente segmenti di arco circolare.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STCurveToLine ( )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Tipi restituiti
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
## <a name="remarks"></a>Osservazioni  
 Restituisce un'istanza **GeometryCollection** vuota per variabili di istanza **geometry** vuote e restituisce **NULL** per variabili **geometry** non inizializzate.  
  
 L'approssimazione poligonale restituita dal metodo dipende dall'istanza **geometry** usata per chiamare il metodo:  
  
-   Restituisce un'istanza **LineString** per un'istanza **CircularString** o **CompoundCurve**.  
  
-   Restituisce un'istanza **Polygon** per un'istanza **CurvePolygon**.  
  
-   Restituisce una copia dell'istanza **geometry** se l'istanza non è di tipo **CircularString**, **CompoundCurve** o **CurvePolygon**. Ad esempio, il metodo `STCurveToLine` restituisce un'istanza **Point** per un'istanza **geometry** di tipo **Point**.  
  
 A differenza della specifica SQL/MM, il metodo `STCurveToLine` non usa i valori della coordinata z per calcolare l'approssimazione poligonale. Il metodo ignora qualsiasi valore della coordinata z presente nell'istanza **geometry** chiamante.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-an-uninitialized-geometry-variable-and-empty-instance"></a>R. Utilizzo di una variabile di geometria non inizializzata e di un'istanza vuota  
 Nell'esempio seguente, la prima istruzione **SELECT** usa un'istanza **geometry** non inizializzata per chiamare il metodo `STCurveToLine` e la seconda istruzione **SELECT** usa un'istanza **geometry** vuota. Pertanto, il metodo restituisce **NULL** alla prima istruzione e una raccolta **GeometryCollection** alla seconda istruzione.  
  
```
 DECLARE @g geometry; 
 SET @g = @g.STCurveToLine(); 
 SELECT @g.STGeometryType(); 
 SET @g = geometry::Parse('LINESTRING EMPTY'); 
 SELECT @g.STGeometryType();
 ```  
  
### <a name="b-using-a-linestring-instance"></a>B. Utilizzo di un'istanza LineString  
 L'istruzione **SELECT** nell'esempio seguente usa un'istanza **LineString** per chiamare il metodo STCurveToLine. In questo caso, il metodo restituisce un'istanza **LineString**.  
  
```
 DECLARE @g geometry; 
 SET @g = geometry::Parse('LINESTRING(1 3, 5 5, 4 3, 1 3)'); 
 SET @g = @g.STCurveToLine(); 
 SELECT @g.STGeometryType();
 ```  
  
### <a name="c-using-a-circularstring-instance"></a>C. Utilizzo di un'istanza CircularString  
 La prima istruzione **SELECT** nell'esempio seguente usa un'istanza **CircularString** per chiamare il metodo STCurveToLine. In questo caso, il metodo restituisce un'istanza **LineString**. Questa istruzione **SELECT** confronta inoltre le lunghezze delle due istanze, che sono pressoché identiche.  Infine, la seconda istruzione **SELECT** restituisce il numero di punti per ogni istanza.  Restituisce solo 5 punti per l'istanza **CircularString**, ma 65 punti per l'istanza **LineString**.  
  
```
 DECLARE @g1 geometry, @g2 geometry; 
 SET @g1 = geometry::Parse('CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0)'); 
 SET @g2 = @g1.STCurveToLine(); 
 SELECT @g1.STGeometryType() AS [G1 Type], @g2.STGeometryType() AS [G2 Type], @g1.STLength() AS [G1 Perimeter], @g2.STLength() AS [G2 Perimeter], @g2.ToString() AS [G2 Def]; 
 SELECT @g1.STNumPoints(), @g2.STNumPoints();
 ```  
  
### <a name="d-using-a-curvepolygon-instance"></a>D. Utilizzo di un'istanza CurvePolygon  
 L'istruzione **SELECT** nell'esempio seguente usa un'istanza **CurvePolygon** per chiamare il metodo STCurveToLine. In questo caso, il metodo restituisce un'istanza **Polygon**.  
  
```
 DECLARE @g1 geometry, @g2 geometry; 
 SET @g1 = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0))'); 
 SET @g2 = @g1.STCurveToLine(); 
 SELECT @g1.STGeometryType() AS [G1 Type], @g2.STGeometryType() AS [G2 Type];
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica dei tipi di dati spaziali](../../relational-databases/spatial/spatial-data-types-overview.md)   
 [STLength &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/stlength-geometry-data-type.md)   
 [STNumPoints &#40;geometry Data Type&#41; (STNumPoints &#40;tipo di dati geometry&#41;)](../../t-sql/spatial-geometry/stnumpoints-geometry-data-type.md)   
 [STGeometryType &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/stgeometrytype-geometry-data-type.md)  
  
  

