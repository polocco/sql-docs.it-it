---
title: Scrittura di istruzioni Transact-SQL internazionali | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- writing international statements
- Transact-SQL international considerations
- international considerations [SQL Server], Transact-SQL
- Database Engine international considerations [SQL Server], Transact-SQL
- statements [SQL Server], international
- database international considerations [SQL Server], Transact-SQL
- dates [SQL Server], international considerations
ms.assetid: f0b10fee-27f7-45fe-aece-ccc3f63bdcdb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1888d1045e43e0a9839fd76a21c51500af63539a
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84953321"
---
# <a name="write-international-transact-sql-statements"></a>Scrittura di istruzioni Transact-SQL internazionali
  Le linee guida seguenti consentono di aumentare il grado di portabilità tra lingue diverse, nonché il supporto di più lingue, per i database e le applicazioni di database che utilizzano istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
-   Sostituire tutte le occorrenze dei tipi di dati `char`, `varchar` e `text` con `nchar`, `nvarchar` e `nvarchar(max)`. In questo modo non si verificano problemi a livello di conversione della tabella codici. Per altre informazioni, vedere [Collation and Unicode Support](collation-and-unicode-support.md).  
  
-   Quando si eseguono confronti e operazioni con mesi o giorni della settimana, utilizzare le parti numeriche della data anziché le stringhe di nomi. I nomi dei mesi e dei giorni della settimana restituiti variano a seconda dell'impostazione della lingua. Ad esempio, DATENAME (MONTH,GETDATE()) restituisce May quando la lingua è impostata sull'inglese (Stati Uniti) Mai se è impostato il tedesco e mai se è impostato il francese. Specificare pertanto una funzione quale DATEPART che utilizza il numero anziché il nome del mese. Utilizzare i nomi DATEPART quando si compilano i set di risultati da visualizzare all'utente, in quanto le stringhe di nomi sono più significative delle parti numeriche. Non creare tuttavia il codice di logica che dipende dai nomi visualizzati di una lingua specifica.  
  
-   Quando si specificano le date nei confronti o nell'input di istruzioni INSERT e UPDATE, utilizzare costanti che vengono interpretate nello stesso modo indipendentemente dall'impostazione della lingua:  
  
    -   Le applicazioni ADO, OLE DB e ODBC devono utilizzare le clausole di escape seguenti relative a timestamp, data e ora:  
  
         **{ts '** aaaa **-** _mm_ **-** _DDHH_**:**_mm_**:**_ss_[**.** _fff_] **'}** ad esempio: **{ts '** 1998 **-** 09 **-** 24 10 **:** 02 **:** 20 **'}**  
  
         **{ d'** _aaaa_ **-** _mm_ **-** _gg_ **'}** ad esempio: **{ d'** 1998**-** 09**-** 24 **'}**  
  
         **{t'** _HH_ **:** _mm_ **:** _SS_ **'}** ad esempio: **{t'** 10:02:20 **'}**  
  
    -   Nelle applicazioni che utilizzano altre API, oppure script, stored procedure e trigger di [!INCLUDE[tsql](../../includes/tsql-md.md)] , è necessario utilizzare le stringhe numeriche non separate, Ad esempio, *aaaammgg* come 19980924.  
  
    -   Per le applicazioni che utilizzano altre API, o [!INCLUDE[tsql](../../includes/tsql-md.md)] script, stored procedure e trigger, è necessario utilizzare l'istruzione CONVERT con un parametro di stile esplicito per tutte le conversioni tra i tipi di dati `time` , `date` , `smalldate` , `datetime` , **datetime2**e e i tipi di dati `datetimeoffset` stringa di caratteri. L'istruzione seguente viene interpretata nello stesso modo indipendentemente dalle impostazioni di connessione della lingua o del formato della data:  
  
        ```  
        SELECT *  
        FROM AdventureWorks2012.Sales.SalesOrderHeader  
        WHERE OrderDate = CONVERT(DATETIME, '20060719', 101)  
        ```  
  
         Per altre informazioni, vedere [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).  
  
  
