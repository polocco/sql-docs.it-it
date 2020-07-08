---
title: STCurveN (tipo di dati geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STCurveN
- STCurveN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STCurveN method (geography)
ms.assetid: 99ef7100-2c4b-4f07-8d66-b343da94b023
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: eabf47faee7f6dbd0916680b378a653a1ae9c619
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85704378"
---
# <a name="stcurven-geography-data-type"></a>STCurveN (tipo di dati geography)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Restituisce la curva specificata da un'istanza **geography** e corrispondente a **LineString**, **CircularString** o **CompoundCurve**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STCurveN( n )  
```  
  
## <a name="arguments"></a>Argomenti  
 *n*  
 Espressione **int** compresa tra 1 e il numero di curve nell'istanza **geography**.  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="exceptions"></a>Eccezioni  
 Se n < 1 viene generata un'eccezione **ArgumentOutOfRangeException**.  
  
## <a name="remarks"></a>Osservazioni  
 **NULL** viene restituito quando si verificano i criteri seguenti.  
  
-   L'istanza **geography** viene dichiarata, ma non ne viene creata un'istanza  
  
-   L'istanza **geography** è vuota  
  
-   n supera il numero di curve presenti nell'istanza **geography** (vedere [STNumCurves &#40;tipo di dati geography&#41;](../../t-sql/spatial-geography/stnumcurves-geography-data-type.md)  
  
-   La dimensione dell'istanza **geography** non è uguale (vedere [STDimension &#40;tipo di dati geography&#41;](../../t-sql/spatial-geography/stdimension-geography-data-type.md)  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-stcurven-on-a-circularstring"></a>R. Utilizzo di STCurveN() in CircularString  
 Nell'esempio seguente viene restituita la seconda curva in un'istanza **CircularString**:  
  
```
 DECLARE @g geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 Nell'esempio viene restituito.  
  
 `CIRCULARSTRING (-122.348 47.658, -122.358 47.658, -122.358 47.653)`  
  
### <a name="b-using-stcurven-on-a-compoundcurve"></a>B. Utilizzo di STCurveN() in CompoundCurve  
 Nell'esempio seguente viene restituita la seconda curva in un'istanza **CompoundCurve**:  
  
```
 DECLARE @g geography = 'COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 Nell'esempio viene restituito.  
  
 `CIRCULARSTRING (-122.348 47.658, -122.358 47.658, -122.358 47.653)`  
  
### <a name="c-using-stcurven-on-a-compoundcurve-containing-three-circularstrings"></a>C. Utilizzo di STCurveN() in un'istanza CompoundCurve che contiene tre istanze CircularString  
 Nell'esempio seguente viene usata un'istanza **CompoundCurve** che combina tre istanze **CircularString** separate nella stessa sequenza di curve dell'esempio precedente:  
  
```
 DECLARE @g geography = 'COMPOUNDCURVE (CIRCULARSTRING (-122.358 47.653, -122.348 47.649, -122.348 47.658), CIRCULARSTRING(-122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 Nell'esempio viene restituito.  
  
 `CIRCULARSTRING (-122.348 47.658, -122.358 47.658, -122.358 47.653)`  
  
 `STCurveN()` restituisce gli stessi risultati indipendentemente dal formato Well-Known Text (WKT) utilizzato.  
  
### <a name="d-testing-for-validity-before-calling-stcurve"></a>D. Verifica della validità prima della chiamata a STCurve()  
 Nell'esempio seguente viene illustrato come assicurarsi che *n* sia valido prima di chiamare il metodo STCurveN():  
  
```
 DECLARE @g geography;  
 DECLARE @n int;  
 SET @n = 2;  
 SET @g = geography::Parse('LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)');  
 IF @n >= 1 AND @n <= @g.STNumCurves()  
 BEGIN  
 SELECT @g.STCurveN(@n).ToString();  
 END
  ```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze geografiche](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
