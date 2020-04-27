---
title: Guide di piano | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- TEMPLATE plan guide
- SQL plan guides
- OPTIMIZE FOR query hint
- RECOMPILE query hint
- OBJECT plan guide
- plan guides [SQL Server], about plan guides
- OPTION clause
- plan guides [SQL Server]
- USE PLAN query hint
ms.assetid: bfc97632-c14c-4768-9dc5-a9c512f6b2bd
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ea11c177533a6101bb0654ca0450e85ea855d9a5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "63150824"
---
# <a name="plan-guides"></a>Guide di piano
  Le guide di piano consentono di ottimizzare le prestazioni delle query quando non è possibile o non si desidera modificare direttamente il testo della query corrente in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Le guide di piano influiscono sull'ottimizzazione delle query mediante l'aggiunta di hint per la query o di un piano di query fisso. Le guide di piano risultano utili quando le prestazioni di un piccolo subset di query eseguite su un database di terze parti sono inferiori a quelle previste. In una guida di piano, viene specificata l'istruzione Transact-SQL da ottimizzare e la clausola OPTION che contiene gli hint per la query da utilizzare o un piano di query specifico da utilizzare per ottimizzare la query. Quando viene eseguita la query, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] associa l'istruzione Transact-SQL alla guida di piano e, in fase di esecuzione, associa la clausola OPTION alla query oppure utilizza il piano di query specificato.  
  
 Il numero totale di guide di piano che è possibile creare è limitato solo dalle risorse di sistema disponibili. È comunque consigliabile utilizzare le guide di piano per le sole query critiche di cui si desidera migliorare o stabilizzare le prestazioni. Le guide di piano non vanno utilizzate per modificare la maggior parte del carico di query di un'applicazione distribuita.  
  
> [!NOTE]  
>  Le guide di piano sono supportate solo in alcune edizioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md). Le guide di piano sono visibili in qualsiasi edizione. È inoltre possibile collegare un database che contiene guide di piano a qualsiasi edizione. Quando si ripristina o si collega un database a una versione aggiornata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le guide di piano non vengono modificate.  
  
## <a name="types-of-plan-guides"></a>Tipi di guide di piano  
 È possibile creare i seguenti tipi di guide di piano:  
  
 guida di piano di tipo OBJECT  
 Una guida di piano di tipo OBJECT corrisponde alle query eseguite nel contesto di stored procedure [!INCLUDE[tsql](../../includes/tsql-md.md)] , funzioni scalari definite dall'utente, funzioni con valori di tabella definite dall'utente con istruzioni multiple e trigger DML.  
  
 Si supponga che la seguente stored procedure, che accetta il parametro `@Country`_`region` , si trovi in un'applicazione di database distribuita sul database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] :  
  
```  
CREATE PROCEDURE Sales.GetSalesOrderByCountry (@Country_region nvarchar(60))  
AS  
BEGIN  
    SELECT *  
    FROM Sales.SalesOrderHeader AS h, Sales.Customer AS c,   
        Sales.SalesTerritory AS t  
    WHERE h.CustomerID = c.CustomerID  
        AND c.TerritoryID = t.TerritoryID  
        AND CountryRegionCode = @Country_region  
END;  
```  
  
 Questa stored procedure è stata compilata e ottimizzata per `@Country`_`region = N'AU'` (Australia). Tuttavia, poiché sono presenti relativamente pochi ordini di vendita con origine in Australia, le prestazioni diminuiscono quando viene eseguita la query utilizzando i valori del parametro dei paesi con più ordini di vendita. Poiché il paese da cui proviene la maggior parte degli ordini di vendita sono gli Stati Uniti, un piano di query generato per `@Country`\_`region = N'US'` offrirebbe probabilmente prestazioni migliori per tutti i possibili valori del parametro `@Country`\_`region` .  
  
 Per risolvere il problema è possibile modificare la stored procedure aggiungendo alla query l'hint `OPTIMIZE FOR` . Poiché la stored procedure si trova in un'applicazione distribuita, non è possibile modificare direttamente il codice dell'applicazione. È invece possibile creare la guida di piano seguente nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
```  
sp_create_plan_guide   
@name = N'Guide1',  
@stmt = N'SELECT *FROM Sales.SalesOrderHeader AS h,  
        Sales.Customer AS c,  
        Sales.SalesTerritory AS t  
        WHERE h.CustomerID = c.CustomerID   
            AND c.TerritoryID = t.TerritoryID  
            AND CountryRegionCode = @Country_region',  
@type = N'OBJECT',  
@module_or_batch = N'Sales.GetSalesOrderByCountry',  
@params = NULL,  
@hints = N'OPTION (OPTIMIZE FOR (@Country_region = N''US''))';  
```  
  
 Al momento dell'esecuzione della query specificata nell'istruzione `sp_create_plan_guide` , la query viene modificata prima dell'ottimizzazione per includere la clausola `OPTIMIZE FOR (@Country = N''US'')` .  
  
 Guida di piano di tipo SQL  
 Una guida di piano di tipo SQL corrisponde alle query eseguite nel contesto di batch e istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] autonome che non fanno parte di un oggetto di database. Le guide di piano basate su SQL possono inoltre essere utilizzate per query con parametrizzazioni specifiche. Le guide di piano di tipo SQL vengono applicate a istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] autonome e batch. Spesso tali istruzioni vengono inoltrate da un'applicazione mediante la stored procedure di sistema [sp_executesql](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql) . Ad esempio, si consideri il batch autonomo seguente:  
  
```  
SELECT TOP 1 * FROM Sales.SalesOrderHeader ORDER BY OrderDate DESC;  
```  
  
 Per impedire la generazione di un piano di esecuzione parallelo su questa query, creare la seguente guida di piano e impostare l'hint per la query `MAXDOP` su `1` nel parametro `@hints` .  
  
```  
sp_create_plan_guide   
@name = N'Guide2',   
@stmt = N'SELECT TOP 1 * FROM Sales.SalesOrderHeader ORDER BY OrderDate DESC',  
@type = N'SQL',  
@module_or_batch = NULL,   
@params = NULL,   
@hints = N'OPTION (MAXDOP 1)';  
```  
  
> [!IMPORTANT]  
>  I valori specificati per gli argomenti `@module_or_batch` e `@params` dell'istruzione `sp_create_plan guide` devono corrispondere al testo specificato nella query effettiva. Per altre informazioni, vedere [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) e [Usare SQL Server Profiler per creare e testare guide di piano](plan-guides.md).  
  
 È possibile creare guide di piano SQL anche per le query con parametrizzazione forzata quando l'opzione di database PARAMETERIZATION è impostata su FORCED, oppure quando si crea una guida di piano di tipo TEMPLATE per specificare la parametrizzazione di una classe di query.  
  
 TEMPLATE - guida di piano  
 Una guida di piano di tipo TEMPLATE corrisponde alle query autonome con parametrizzazioni specifiche. Tali guide di piano vengono utilizzate per sostituire l'opzione SET di database PARAMETERIZATION di un database per una classe di query.  
  
 È possibile creare una guida di piano di tipo TEMPLATE nelle seguenti situazioni:  
  
-   L'opzione di database PARAMETERIZATION è impostata su FORCED, ma si desidera compilare alcune query in base alle regole della parametrizzazione semplice.  
  
-   L'opzione di database PARAMETERIZATION è impostata su SIMPLE (impostazione predefinita), ma si desidera che una classe di query venga sottoposta a parametrizzazione forzata.  
  
## <a name="plan-guide-matching-requirements"></a>Requisiti di corrispondenza per la guida di piano  
 Le guide di piano sono definite a livello di ambito del database in cui vengono create. Pertanto, è possibile far corrispondere alla query solo le guide di piano presenti nel database corrente al momento dell'esecuzione della query. Ad esempio, se [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] è il database corrente e viene eseguita la query seguente:  
  
 `SELECT FirstName, LastName FROM Person.Person;`  
  
 È possibile far corrispondere alla query solo le guide di piano nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Se tuttavia il database corrente è [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] e vengono eseguite le istruzioni seguenti:  
  
 `USE DB1;`  
  
 `SELECT FirstName, LastName FROM Person.Person;`  
  
 È possibile far corrispondere alla query solo le guide di piano in `DB1` , poiché la query è in esecuzione nel contesto di `DB1`.  
  
 Per guide di piano basate su SQL o TEMPLATE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esegue la corrispondenza tra i valori per gli argomenti @module_or_batch e @params e una query, confrontando i due valori carattere per carattere. Per questo motivo è necessario immettere il testo esattamente come [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lo riceve nel batch.  
  
 Quando @type =' SQL ' e @module_or_batch è impostato su null, il valore di @module_or_batch viene impostato sul valore di @stmt. Ciò significa che il valore di *statement_text* deve essere specificato nello stesso formato, carattere per carattere, così come viene inviato a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per semplificare questa corrispondenza, non viene eseguita alcuna conversione interna.  
  
 Quando è possibile applicare sia una guida di piano normale (SQL o OBJECT) sia una guida di piano TEMPLATE a un'istruzione, verrà utilizzata solo la guida di piano normale.  
  
> [!NOTE]  
>  Il batch contenente l'istruzione sulla quale si desidera creare una guida di piano non può contenere un'istruzione USE *database* .  
  
## <a name="plan-guide-effect-on-the-plan-cache"></a>Effetto delle guide di piano sulla cache dei piani  
 La creazione di una guida di piano su un modulo rimuove il piano di query per il dato modulo dalla cache dei piani. La creazione di una guida di piano di tipo OBJECT o SQL su un batch rimuove il piano di query per un batch con lo stesso valore hash. La creazione di una guida di piano di tipo TEMPLATE rimuove tutti i batch a istruzione singola dalla cache dei piani all'interno del database.  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Attività|Argomento|  
|----------|-----------|  
|Viene descritto come creare una guida di piano.|[Creare una nuova guida di piano](create-a-new-plan-guide.md)|  
|Viene descritto come creare una guida di piano per le query con parametri.|[Creare una guida di piano per le query con parametri](create-a-plan-guide-for-parameterized-queries.md)|  
|Viene descritto come controllare il comportamento di parametrizzazione delle query utilizzando guide di piano.|[Specificare il comportamento di parametrizzazione delle query tramite guide di piano](specify-query-parameterization-behavior-by-using-plan-guides.md)|  
|Viene descritto come includere un piano di query fisso in una guida di piano.|[Applicare un piano di query fisso a una guida di piano](apply-a-fixed-query-plan-to-a-plan-guide.md)|  
|Viene descritto come specificare hint per la query in una guida di piano.|[Associare gli hint per le query a una guida di piano](attach-query-hints-to-a-plan-guide.md)|  
|Viene descritto come visualizzare le proprietà di una guida di piano.|[Visualizzare le proprietà delle guide di piano](view-plan-guide-properties.md)|  
|Viene descritto come utilizzare SQL Server Profiler per creare e testare guide di piano.|[Usare SQL Server Profiler per creare e testare le guide di piano](plan-guides.md)|  
|Viene descritto come convalidare una guida di piano.|[Convalidare le guide di piano dopo l'aggiornamento](validate-plan-guides-after-upgrade.md)|  
  
## <a name="see-also"></a>Vedi anche  
 [sp_create_plan_guide &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)   
 [sp_control_plan_guide &#40;&#41;Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql)   
 [sys. plan_guides &#40;&#41;Transact-SQL](/sql/relational-databases/system-catalog-views/sys-plan-guides-transact-sql)   
 [sys.fn_validate_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql)  
  
  
