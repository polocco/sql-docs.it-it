---
description: Parse (tipo di dati geometry)
title: Parse (tipo di dati geometry) | Microsoft Docs
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
- Parse (geometry Data Type)
ms.assetid: 6e080919-4b64-46cd-8dd2-254a9c232e53
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 2774f83d167ec61d0e1a2d68b391c2d5d3318535
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88416947"
---
# <a name="parse-geometry-data-type"></a>Parse (tipo di dati geometry)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Restituisce un'istanza **geometry** da una rappresentazione WKT (Well-Known Text) OGC (Open Geospatial Consortium). `Parse()` è equivalente a [STGeomFromText()](../../t-sql/spatial-geometry/parse-geometry-data-type.md), con l'eccezione che presuppone un ID di riferimento spaziale (SRID) di 0 come parametro. All'input possono appartenere valori Z (innalzamento) e M (misura) facoltativi.
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Parse ( 'geometry_tagged_text' )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argomenti
 *geometry_tagged_text*  
 Rappresentazione WKT dell'istanza **geometry** da restituire. *geometry_tagged_text* è un'espressione **nvarchar**.  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
## <a name="remarks"></a>Osservazioni  
 Il tipo OGC dell'istanza **geometry** restituita da `Parse()` è impostato sull'input WKT corrispondente.  
  
 La stringa "Null" verrà interpretata come un'istanza **geometry** Null.  
  
 Questo metodo genererà un'eccezione **FormatException** se l'input non è formattato in modo corretto.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato il metodo `Parse()` per creare un'istanza `geometry`.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::Parse('LINESTRING (100 100, 20 180, 180 180)');  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [STGeomFromText](../../t-sql/spatial-geometry/parse-geometry-data-type.md)   
 [Metodi di geometria statici estesi](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  

