---
title: STOverlaps (tipo di dati geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STOverlaps (geometry Data Type)
- STOverlaps_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STOverlaps (geometry Data Type)
ms.assetid: 1813cba1-5780-456a-9489-6b40a79569b3
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 5de112961599421eb7ce2d85d8152f1aa1339e0c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85762250"
---
# <a name="stoverlaps-geometry-data-type"></a>STOverlaps (tipo di dati geometry)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Restituisce 1 se un'istanza **geometry** si sovrappone a un'altra istanza **geometry**. In caso contrario, restituisce 0.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STOverlaps ( other_geometry )  
```  
  
## <a name="arguments"></a>Argomenti  
 *other_geometry*  
 Altra istanza **geometry** da confrontare con l'istanza sulla quale viene chiamato `STOverlaps()`.  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **bit**  
  
 Tipo CLR restituito: **SqlBoolean**  
  
## <a name="remarks"></a>Osservazioni  
 Due istanze **geometry** si sovrappongono se la regione che rappresenta la loro intersezione ha la stessa dimensione delle istanze e se la regione non è uguale alle istanze.  
  
 `STOverlaps()` restituisce sempre 0 se i punti in cui le istanze **geometry** si intersecano non hanno la stessa dimensione.  
  
 Questo metodo restituisce sempre Null se gli identificatori SRID delle istanze **geometry** non corrispondono.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene usato `STOverlaps()` per verificare se due istanze **geometry** si sovrappongono.  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 2 0, 2 2, 0 2, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POLYGON((1 1, 3 1, 3 3, 1 3, 1 1))', 0);  
SELECT @g.STOverlaps(@h);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze di geometria](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

