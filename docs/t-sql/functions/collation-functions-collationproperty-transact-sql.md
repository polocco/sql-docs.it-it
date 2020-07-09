---
title: COLLATIONPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- COLLATIONPROPERTY_TSQL
- COLLATIONPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- collations [SQL Server], properties
- COLLATIONPROPERTY function
ms.assetid: f5029e74-a1db-4f69-b0f5-5ee920c3311d
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 70a94b187ef0c60d0246c33dec79771600d8fd28
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86011560"
---
# <a name="collation-functions---collationproperty-transact-sql"></a>Funzioni delle regole di confronto - COLLATIONPROPERTY (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

La funzione restituisce la proprietà richiesta delle regole di confronto specificate.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
COLLATIONPROPERTY( collation_name , property )  
```  
  
## <a name="arguments"></a>Argomenti  
*nome_regole_di_confronto*  
Nome delle regole di confronto. L'argomento *collation_name* ha un tipo di dati **nvarchar (128)** , senza alcun valore predefinito.
  
*property*  
Proprietà delle regole di confronto. L'argomento *property* ha un tipo di dati **varchar(128)** e può avere uno dei valori seguenti:
  
|Nome proprietà|Descrizione|  
|---|---|
|**CodePage**|Tabella codici non Unicode delle regole di confronto. Questo è il set di caratteri utilizzato per i dati **varchar**. Vedere [Appendix G DBCS/Unicode Mapping Tables](https://msdn.microsoft.com/library/cc194886.aspx) (Appendice G - Tabelle di mapping DBCS/Unicode) e [Appendix H Code Pages](https://msdn.microsoft.com/library/cc195051.aspx) (Appendice H - Tabelle codici) per la conversione e la visualizzazione dei mapping dei caratteri di questi valori.<br /><br />Tipo di dati di base: **int**|  
|**LCID**|Identificatore delle impostazioni locali di Windows per le regole di confronto. Si tratta delle impostazioni cultura usate per le regole di ordinamento e confronto. Vedere [LCID Structure](https://msdn.microsoft.com/library/cc233968.aspx) (Struttura LCID) per la conversione di questi valori (sarà necessario convertirli prima in **varbinary**).<br /><br />Tipo di dati di base: **int**|  
|**ComparisonStyle**|Stile di confronto di Windows per le regole di confronto. Restituisce 0 per le regole di confronto binarie, sia (\_BIN) che (\_BIN2), e anche quando tutte le proprietà sono sensibili, (\_CS\_AS\_KS\_WS) e (\_CS\_AS\_KS\_WS\_SC) e (\_CS\_AS\_KS\_WS\_VSS). Valori della maschera di bit:<br /><br /> Ignora maiuscole/minuscole: 1<br /><br /> Ignora accento : 2<br /><br /> Ignora Kana : 65536<br /><br /> Ignora larghezza: 131072<br /><br /> Nota: anche se ha effetto sul comportamento di confronto, l'opzione con distinzione tra selettori di variazione (\_VSS) non è rappresentata in questo valore.<br /><br />Tipo di dati di base: **int**|  
|**Version**|La versione delle regole di confronto. Restituisce un valore compreso tra 0 e 3.<br /><br /> Le regole di confronto con "140" nel nome restituiscono 3.<br /><br /> Le regole di confronto con "100" nel nome restituiscono 2.<br /><br /> Le regole di confronto con "90" nel nome restituiscono 1.<br /><br /> Tutte le altre regole di confronto restituiscono 0.<br /><br />Tipo di dati di base: **tinyint**|  
  
## <a name="return-types"></a>Tipi restituiti
**sql_variant**
  
## <a name="examples"></a>Esempi  
  
```sql
SELECT COLLATIONPROPERTY('Traditional_Spanish_CS_AS_KS_WS', 'CodePage');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1252   
```  
  
[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```sql
SELECT COLLATIONPROPERTY('Traditional_Spanish_CS_AS_KS_WS', 'CodePage')  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1252   
```  
  
## <a name="see-also"></a>Vedere anche
[sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)
  
  

