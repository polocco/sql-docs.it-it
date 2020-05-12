---
title: COMPRESS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/11/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: reference
f1_keywords:
- COMPRESS
- COMPRESS_TSQL
helpviewer_keywords:
- COMPRESS function
ms.assetid: c2bfe9b8-57a4-48b4-b028-e1a3ed5ece88
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 006fa6a31fcb5561de19cd48d4127ad506ef100b
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832185"
---
# <a name="compress-transact-sql"></a>COMPRESS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

Questa funzione comprime l'espressione di input usando l'algoritmo GZIP. La funzione restituisce una matrice di byte di tipo **varbinary (max)** .
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
COMPRESS ( expression )  
```  
  
## <a name="arguments"></a>Argomenti  
*expression*  
Una

* **binary(***n***)**
* **char(***n***)**
* **nchar(***n***)**
* **nvarchar(max)**
* **nvarchar(***n***)**
* **varbinary(max)**
* **varbinary(***n***)**
* **ntext**

o

* **varchar(***n***)**

expression. Per altre informazioni, vedere [Espressioni &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).
  
## <a name="return-types"></a>Tipi restituiti
**varbinary (max)** che rappresenta il contenuto compresso dell'input.
  
## <a name="remarks"></a>Osservazioni  
I dati compressi non possono essere indicizzati.
  
La funzione `COMPRESS` comprime i dati di espressione dell'input. Richiamare questa funzione per ogni sezione di dati da comprimere. Vedere [Compressione dei dati](../../relational-databases/data-compression/data-compression.md) per altre informazioni sulla compressione automatica dei dati durante l'archiviazione a livello di riga o pagina.
  
## <a name="examples"></a>Esempi  
  
### <a name="a-compress-data-during-the-table-insert"></a>R. Comprimere i dati durante l'inserimento nella tabella  
L'esempio illustra come comprimere i dati inseriti in una tabella:
  
```sql
INSERT INTO player (name, surname, info )  
VALUES (N'Ovidiu', N'Cracium',   
        COMPRESS(N'{"sport":"Tennis","age": 28,"rank":1,"points":15258, turn":17}'));  
  
INSERT INTO player (name, surname, info )  
VALUES (N'Michael', N'Raheem', compress(@info));  
```  
  
### <a name="b-archive-compressed-version-of-deleted-rows"></a>B. Archiviare la versione compressa di righe eliminate  
Questa istruzione elimina i record obsoleti Player (Giocatore) dalla tabella `player`, dopo di ché, per risparmiare spazio, archivia i record nella tabella `inactivePlayer` usando un formato compresso.
  
```sql
DELETE FROM player  
OUTPUT deleted.id, deleted.name, deleted.surname, deleted.datemodifier, COMPRESS(deleted.info)   
INTO dbo.inactivePlayers
WHERE datemodified < @startOfYear; 
```  
  
## <a name="see-also"></a>Vedere anche
[Funzioni per i valori stringa &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)  
[DECOMPRESS &#40;Transact-SQL&#41;](../../t-sql/functions/decompress-transact-sql.md)
  
  
