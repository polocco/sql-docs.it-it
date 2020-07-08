---
title: ShortestLineTo (tipo di dati geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ShortestLineTo_TSQL
- ShortestLineTo
dev_langs:
- TSQL
helpviewer_keywords:
- ShortestLineTo method (geography)
ms.assetid: 9d7c9885-5d1b-49ae-af31-5ef9fb8acaba
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 849fc974147d06e6b31713666498b0df00e7a279
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85705483"
---
# <a name="shortestlineto-geography-data-type"></a>ShortestLineTo (tipo di dati geography)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

  Restituisce un'istanza **LineString** con due punti che rappresentano la distanza più breve tra le due istanze **geography**. La lunghezza dell'istanza **LineString** restituita è la distanza tra le due istanze **geography**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.ShortestLineTo ( geography_other )  
```  
  
## <a name="arguments"></a>Argomenti  
 *geography_other*  
 Specifica la seconda istanza **geography** da cui l'istanza **geography** chiamante tenta di determinare la distanza più breve.  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="remarks"></a>Osservazioni  
 Il metodo restituisce un'istanza **LineString** con endpoint che si trovano sui bordi delle due istanze **geography** non intersecate messe a confronto. La lunghezza dell'istanza **LineString** restituita corrisponde alla distanza minore tra le due istanze **geography**. Viene restituita un'istanza **LineString** vuota quando le due istanze **geography** si intersecano.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-calling-shortestlineto-on-non-intersecting-instances"></a>R. Chiamata di ShortestLineTo() in istanze non intersecate  
 In questo esempio viene individuata la distanza più breve tra un'istanza `CircularString` e un'istanza `LineString` e viene restituita l'istanza `LineString` che collega i due punti:  
  
 ```
 DECLARE @g1 geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 DECLARE @g2 geography = 'LINESTRING(-119.119263 46.183634, -119.273071 47.107523, -120.640869 47.569114, -122.200928 47.454094)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
 ```  
  
### <a name="b-calling-shortestlineto-on-intersecting-instances"></a>B. Chiamata di ShortestLineTo() in istanze intersecate  
 In questo esempio viene restituita un'istanza `LineString` vuota perché l'istanza `LineString` interseca l'istanza `CircularString`:  
  
 ```
 DECLARE @g1 geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 DECLARE @g2 geography = 'LINESTRING(-119.119263 46.183634, -119.273071 47.107523, -120.640869 47.569114, -122.348 47.649, -122.681 47.655)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
``` 
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze geografiche](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
 [ShortestLineTo (tipo di dati geometry)](../../t-sql/spatial-geometry/shortestlineto-geometry-data-type.md)  
  
