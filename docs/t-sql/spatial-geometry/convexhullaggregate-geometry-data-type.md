---
title: ConvexHullAggregate (tipo di dati geometry) | Microsoft Docs
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
- ConvexHullAggregate method (geometry)
ms.assetid: ca3d3b55-e02d-4599-8817-a54f5e047db8
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 5ea01bd48dea04e5ae5d00a480d6ce43662d96d0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85700487"
---
# <a name="convexhullaggregate-geometry-data-type"></a>ConvexHullAggregate (tipo di dati geometry)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

Restituisce una struttura convessa per un set specificato di oggetti **geometry**.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ConvexHullAggregate ( geometry_operand )  
```  
  
## <a name="arguments"></a>Argomenti  
 *geometry_operand*  
 Colonna della tabella di tipo **geometry** che rappresenta un set di oggetti geometry.  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **geometry**  
  
## <a name="exception"></a>Eccezione  
 Genera un'eccezione `FormatException` in presenza di valori di input non validi. Vedere [STIsValid &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/stisvalid-geometry-data-type.md)  
  
## <a name="remarks"></a>Osservazioni  
 Il metodo restituisce **Null** quando l'input è vuoto o dispone di SRID diversi. Vedere [Identificatori SRID &#40;Spatial Reference Identifier&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)  
  
 Il metodo ignora gli input **Null**.  
  
> [!NOTE]  
>  Il metodo restituisce **Null** se tutti i valori immessi sono **Null**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituita una struttura convessa del set di oggetti di geometria in una colonna delle variabili di tabella.  
  
 ```
 -- Setup table variable for ConvexHullAggregate example  
 DECLARE @Geom TABLE  
 (  
 shape geometry,  
 shapeType nvarchar(50)  
 )  
 INSERT INTO @Geom(shape,shapeType) VALUES('CURVEPOLYGON(CIRCULARSTRING(2 3, 4 1, 6 3, 4 5, 2 3))', 'Circle'),  
 ('POLYGON((1 1, 4 1, 4 5, 1 5, 1 1))', 'Rectangle');  
 -- Perform ConvexHullAggregate on @Geom.shape column  
 SELECT geometry::ConvexHullAggregate(shape).ToString()  
 FROM @Geom;
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di geometria statici estesi](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  

