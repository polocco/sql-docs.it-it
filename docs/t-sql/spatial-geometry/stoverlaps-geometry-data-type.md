---
description: STOverlaps (tipo di dati geometry)
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
ms.openlocfilehash: d92e984fb803cc8b15c58f4b137df2dd51e83f9b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88454260"
---
# <a name="stoverlaps-geometry-data-type"></a>STOverlaps (tipo di dati geometry)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Restituisce 1 se un'istanza **geometry** si sovrappone a un'altra istanza **geometry**. In caso contrario, restituisce 0.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STOverlaps ( other_geometry )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argomenti
 *other_geometry*  
 Altra istanza **geometry** da confrontare con l'istanza sulla quale viene chiamato `STOverlaps()`.  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **bit**  
  
 Tipo CLR restituito: **SqlBoolean**  
  
## <a name="remarks"></a>Commenti  
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
  
  

