---
title: Tipi di dati in Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 910be4f4-3010-41cd-9fdc-f0a79a0ce823
author: minewiskan
ms.author: owend
ms.openlocfilehash: 06b93090918a0fffc9c98e1560b338177eff3d84
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545929"
---
# <a name="data-types-in-analysis-services"></a>Tipi di dati in Analysis Services
  Per tutti <xref:Microsoft.AnalysisServices.DataItem> gli oggetti, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supporta il seguente subset di `System.Data.OleDb.OleDbType` . Per impostare o leggere il tipo di dati, utilizzare il [tipo di dati DataItem &#40;&#41;ASSL ](https://docs.microsoft.com/bi-reference/assl/data-type/dataitem-data-type-assl).  
  
## <a name="supported-data-types"></a>Tipi di dati supportati  
  
|||  
|-|-|  
|BigInt|Intero con segno a 64 bit. Il tipo di valore *bigint* rappresenta numeri interi con valori compresi tra 9.223.372.036.854.775.808 negativi e 9.223.372.036.854.775.807 positivo.|  
|Binario|Flusso di dati binari di tipo **byte** . **Byte** è un tipo valore che rappresenta interi senza segno con valori compresi tra 0 e 255.|  
|Boolean|Istanze di questo tipo dispongono di valori `true` o `false`.|  
|Valuta|Valore di *valuta* compreso tra-922.337.203.685.477,5808 e + 922.337.203.685.477,5807 con precisione pari a dieci millesimi di unità di valuta (quattro posizioni decimali).|  
|Data|Dati relativi alla data e all'ora, archiviati come valore Double. La parte intera indica il numero di giorni a partire dal 30 dicembre 1899 mentre la parte frazionaria rappresenta una frazione del giorno o dell'ora del giorno.|  
|Double|Numero a virgola mobile compreso tra -1,79769313486232E +308 e 1,79769313486232E +308. Un valore Double consente di archiviare informazioni sui numeri fino a 15 cifre decimali di precisione.|  
|Integer|Intero con segno a 32 bit che rappresenta interi con segno con valori compresi tra 2.147.483.648 (negativo) e 2.147.483.647 (positivo).|  
|Single|Numero a virgola mobile compreso tra - 3,4028235E +38 e 3,4028235E +38. Un valore Single consente di archiviare informazioni sui numeri fino a 7 cifre decimali di precisione.|  
|Smallint|Intero con segno a 16 bit. Il tipo di valore *smallint* rappresenta interi con segno con valori compresi tra 32768 negativo e 32767 positivo.|  
|Tinyint|Numero intero con segno a 8 bit. Il tipo di valore Tinyint rappresenta interi con valori compresi tra 128 (negativo) e 127 (positivo).|  
|UnsignedBigInt|Intero senza segno a 64 bit. Il tipo di valore *UnsignedBigInt* rappresenta interi senza segno con valori compresi tra 0 e 18.446.744.073.709.551.615.|  
|UnsignedInt|Intero senza segno a 32 bit. Il tipo di valore *unsignedInt* rappresenta interi senza segno con valori compresi tra 0 e 4.294.967.295.|  
|UnsignedSmallInt|Numero intero non firmato a 16 bit. Il tipo di valore *UnsignedSmallInt* rappresenta interi senza segno con valori compresi tra 0 e 65535.|  
|UnsignedTinyInt|Intero senza segno a 8 bit. Il tipo di valore *e UnsignedTinyInt* rappresenta interi senza segno con valori compresi tra 0 e 255|  
|WChar|Flusso con terminazione Null di caratteri Unicode. *WCHAR* è una raccolta sequenziale di caratteri Unicode utilizzata per rappresentare il testo.|  
  
## <a name="amo-validations-on-data-types"></a>Convalide AMO nei tipi di dati  
 Nella tabella seguente vengono elencate le convalide aggiuntive eseguite nella libreria AMO (Analysis Management Objects) per determinate associazioni.  
  
|Oggetto|Binding|Tipi di dati consentiti|  
|------------|-------------|------------------------|  
|DimensionAttribute|KeyColumns|Tutti tranne i dati binari|  
||NameColumn|Solo WChar|  
||SkippedLevelsColumns|Solo tipi integer: BigInt, Integer, SmallInt, TinyInt, UnsignedBigInt, UnsignedInt, UnsignedSmallInt e UnsignedTinyInt|  
||CustomRollupColumn|Solo WChar|  
||CustomRollupPropertiesColumn|Solo WChar|  
||UnaryOperatorColumn|Solo WChar|  
||ValueColumn|Tutti|  
|AttributeTranslation|CaptionColumn|Solo WChar|  
|ScalarMiningStructureColumn|KeyColumns|Tutti tranne i dati binari|  
||NameColumn|Solo WChar|  
|TableMiningStructureColumn|ForeignKeyColumns|Tutti tranne i dati binari|  
|MeasureGroupAttribute|KeyColumns|Tutti tranne i dati binari|  
|Misura totale valori distinti|Source (Sorgente)|BigInt, Currency, Double, Integer, Single, SmallInt, TinyInt, UnsignedBigInt, UnsignedInt, UnsignedSmallInt e UnsignedTinyInt|  
  
  
