---
title: Filter (tipo di dati geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Filter
- Filter_TSQL
- Filter (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- Filter method
ms.assetid: 3d629a39-157e-4159-a3ca-a3c2e0ed4160
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: ef84f7d95644c552d90f137e9f6edab980acfba9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85736029"
---
# <a name="filter-geometry-data-type"></a>Filter (tipo di dati geometrico)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Metodo di intersezione basato solo su indici che consente di determinare in modo rapido se un'istanza **geometry** interseca un'altra istanza **geometry**, a condizione che sia disponibile un indice.
  
Restituisce 1 se un'istanza **geometry** interseca potenzialmente un'altra istanza **geometry**. Questo metodo può produrre un risultato falso positivo e il risultato esatto può dipendere dal piano. Restituisce un valore esatto 0 (risultato vero positivo) se non viene rilevata alcuna intersezione tra le istanze **geometry**.
  
Nel caso in cui un indice non sia disponibile o non venga usato, il metodo restituisce gli stessi valori di **STIntersects()** se viene chiamato con gli stessi parametri.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.Filter ( other_geometry )  
```  
  
## <a name="arguments"></a>Argomenti  
 *other_geometry*  
 Altra istanza **geometry** da confrontare con l'istanza sulla quale viene chiamato Filter().  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **bit**  
  
 Tipo CLR restituito: **SqlBoolean**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo non è deterministico e non è preciso.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato `Filter()` per determinare se due istanze `geometry` si intersecano.  
  
```  
CREATE TABLE sample (id int primary key, g geometry);  
GO  
INSERT INTO sample VALUES  
   (0, geometry::Point(0, 0, 0)),  
   (1, geometry::Point(0, 1, 0)),  
   (2, geometry::Point(0, 2, 0)),  
   (3, geometry::Point(0, 3, 0)),  
   (4, geometry::Point(0, 4, 0));  
  
CREATE SPATIAL INDEX sample_idx ON sample(g)  
WITH (bounding_box = (-8000, -8000, 8000, 8000));  
GO  
SELECT id  
FROM sample   
WHERE g.Filter(geometry::Parse('POLYGON((-1 -1, 1 -1, 1 1, -1 1, -1 -1))')) = 1;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze di geometria](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [STIntersects &#40;tipo di dati geometry&#41;](../../t-sql/spatial-geometry/stintersects-geometry-data-type.md)  
  
  

