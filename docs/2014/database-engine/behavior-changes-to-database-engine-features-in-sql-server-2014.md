---
title: Modifiche del comportamento delle funzionalità di motore di database in SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- behavior changes [SQL Server]
- Database Engine [SQL Server], what's new
- Transact-SQL behavior changes
ms.assetid: 65eaafa1-9e06-4264-b547-cbee8013c995
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 9072b851f3512113b23dedc91f8c9b7151136a57
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936177"
---
# <a name="behavior-changes-to-database-engine-features-in-sql-server-2014"></a>Differenze di funzionamento delle funzionalità del Motore di database in SQL Server 2014
  In questo argomento vengono descritte le modifiche di comportamento introdotte nel [!INCLUDE[ssDE](../includes/ssde-md.md)]. Queste modifiche influiscono sulle modalità di utilizzo o di interazione delle funzionalità in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] rispetto alle versioni precedenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
## <a name="behavior-changes-in-sssql14"></a><a name="SQL14"></a>Modifiche del comportamento in[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Nelle versioni precedenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], tramite query su un documento XML contenente stringhe in una determinata lunghezza (più di 4020 caratteri) possono essere restituiti risultati non corretti. In [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], tramite query di questo tipo vengono restituiti i risultati corretti.  
  
## <a name="behavior-changes-in-sssql11"></a><a name="Denali"></a>Modifiche del comportamento in[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="metadata-discovery"></a>Individuazione dei metadati  
 I miglioramenti apportati a [!INCLUDE[ssDE](../includes/ssde-md.md)] iniziano con [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Consenti a SQLDescribeCol di ottenere descrizioni più accurate dei risultati previsti rispetto a quelli restituiti da SQLDescribeCol nelle versioni precedenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Per altre informazioni, vedere [Metadata Discovery](../relational-databases/native-client/features/metadata-discovery.md).  
  
 L' [opzione SET FMTONLY](/sql/t-sql/statements/set-fmtonly-transact-sql) per determinare il formato di una risposta senza eseguire effettivamente la query viene sostituita con [sp_describe_first_result_set &#40;&#41;transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql) [sp_describe_undeclared_parameters &#40;Transact-sql ](/sql/relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql)&#41;, [sys. dm_exec_describe_first_result_set &#40;transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql)e [sys. dm_exec_describe_first_result_set_for_object &#40;Transact- ](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql)SQL&#41;.  
  
### <a name="changes-to-behavior-in-scripting-a-sql-server-agent-task"></a>Modifiche al comportamento di script di un'attività di SQL Server Agent  
A partire da [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] , se si crea un nuovo processo copiando lo script da un processo esistente, il nuovo processo potrebbe inavvertitamente influire sul processo esistente. Per creare un nuovo processo utilizzando lo script di un processo esistente, eliminare manualmente il parametro * \@ schedule_uid* che in genere è l'ultimo parametro della sezione che crea la pianificazione del processo nel processo esistente. Verrà creata una nuova pianificazione indipendente per il nuovo processo senza influire sui processi esistenti.  
  
### <a name="constant-folding-for-clr-user-defined-functions-and-methods"></a>Elaborazione delle costanti in fase di compilazione per funzioni e metodi CLR definiti dall'utente  
A partire da [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] , i seguenti oggetti CLR definiti dall'utente sono ora ripieghevoli:  

-   Funzioni CLR definite dall'utente con valori scalari deterministici.  
-   Metodi deterministici di tipi CLR definiti dall'utente.  
  
 Con questo miglioramento si cerca di ottimizzare le prestazioni quando questi metodi o funzioni vengono chiamati più di una volta con gli stessi argomenti. Tuttavia, questa modifica potrebbe provocare risultati imprevisti quando funzioni o metodi non deterministici sono stati contrassegnati erroneamente come deterministici. Il determinismo di una funzione o di un metodo CLR viene indicato dal valore della proprietà `IsDeterministic` di `SqlFunctionAttribute` o `SqlMethodAttribute`.  
  
### <a name="behavior-of-stenvelope-method-has-changed-with-empty-spatial-types"></a>Modifica del comportamento del metodo STEnvelope() con i tipi spaziali vuoti  
 Il comportamento del metodo `STEnvelope` con gli oggetti vuoti è ora coerente con il comportamento degli altri metodi spaziali di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 In [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], in caso di chiamata del metodo `STEnvelope` con oggetti vuoti, venivano restituiti i risultati seguenti:  
  
```sql  
SELECT geometry::Parse('POINT EMPTY').STEnvelope().ToString()  
-- returns POINT EMPTY  
SELECT geometry::Parse('LINESTRING EMPTY').STEnvelope().ToString()  
-- returns LINESTRING EMPTY  
SELECT geometry::Parse('POLYGON EMPTY').STEnvelope().ToString()  
-- returns POLYGON EMPTY  
```  
  
 In [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], in caso di chiamata del metodo `STEnvelope` con oggetti vuoti, vengono ora restituiti i risultati seguenti:  
  
```sql  
SELECT geometry::Parse('POINT EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
SELECT geometry::Parse('LINESTRING EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
SELECT geometry::Parse('POLYGON EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
```  
  
 Per determinare se un oggetto spaziale è vuoto, chiamare il [tipo di dati STIsEmpty &#40;geometry&#41;](/sql/t-sql/spatial-geometry/stisempty-geometry-data-type) metodo.  
  
### <a name="log-function-has-new-optional-parameter"></a>Nuovo parametro facoltativo della funzione LOG  
 La `LOG` funzione dispone ora di un parametro di *base* facoltativo. Per ulteriori informazioni, vedere [LOG &#40;&#41;Transact-SQL ](/sql/t-sql/functions/log-transact-sql).  
  
### <a name="statistics-computation-during-partitioned-index-operations-has-changed"></a>Modifica del calcolo delle statistiche durante operazioni su indici partizionati  
In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]le statistiche non vengono create analizzando tutte le righe nella tabella se viene creato o ricompilato un indice partizionato. Query Optimizer utilizza invece l'algoritmo di campionamento predefinito per generare statistiche. Dopo avere aggiornato un database con gli indici partizionati, è possibile notare una differenza nei dati dell'istogramma relativamente a tali indici. Tale cambiamento potrebbe non influire sulle prestazioni di query. Per ottenere statistiche sugli indici partizionati analizzando tutte le righe nella tabella, usare `CREATE STATISTICS` o `UPDATE STATISTICS` con la clausola `FULLSCAN`.  
  
### <a name="data-type-conversion-by-the-xml-value-method-has-changed"></a>Modifica della conversione del tipo di dati mediante il metodo relativo al valore XML  
Il comportamento interno del metodo `value` del tipo di dati `xml` è cambiato. Con questo metodo è possibile eseguire un'espressione XQuery sul codice XML ottenendo un valore scalare del tipo di dati specificato di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Il tipo xs deve essere convertito nel tipo di dati di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . In precedenza, con il metodo `value` era possibile convertire internamente il valore di origine in xs:string e, successivamente, convertire xs:string nel tipo di dati di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]la conversione a xs:string viene ignorata nei casi seguenti:  
  
|Tipo di dati XS di origine|Tipo di dati di SQL Server di destinazione|  
|-------------------------|--------------------------------------|  
|byte<br /><br /> short<br /><br /> INT<br /><br /> integer<br /><br /> long<br /><br /> unsignedByte<br /><br /> unsignedShort<br /><br /> unsignedInt<br /><br /> unsignedLong<br /><br /> positiveInteger<br /><br /> nonPositiveInteger<br /><br /> negativeInteger<br /><br /> nonNegativeInteger|TINYINT<br /><br /> SMALLINT<br /><br /> INT<br /><br /> bigint<br /><br /> decimal<br /><br /> NUMERIC|  
|decimal|decimal<br /><br /> NUMERIC|  
|float|real|  
|double|float|  
  
 Con il nuovo comportamento è possibile migliorare le prestazioni quando la conversione intermedia può essere ignorata. Tuttavia, quando le conversioni del tipo di dati non vengono completate correttamente, vengono visualizzati messaggi di errore diversi rispetto a quelli generati in caso di conversione dal valore xs:string intermedio. Ad esempio, se tramite il metodo value non era stato possibile convertire il valore `int` 100000 in `smallint`, il messaggio di errore precedente era:  
  
 `The conversion of the nvarchar value '100000' overflowed an INT2 column. Use a larger integer column.`  
  
 In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], senza la conversione intermedia a xs:string, il messaggio di errore è:  
  
 `Arithmetic overflow error converting expression to data type smallint.`  
  
### <a name="sqlcmdexe-behavior-change-in-xml-mode"></a>Modifica del comportamento del file sqlcmd.exe in modalità XML  
 Se si usa sqlcmd.exe con la modalità XML (comando: XML ON) quando si esegue SELECT * from T FOR XML, sono presenti modifiche del comportamento....  
  
### <a name="dbcc-checkident-revised-message"></a>Revisione del messaggio restituito da DBCC CHECKIDENT  
 In [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]il messaggio restituito dal comando DBCC CHECKIDENT è cambiato solo se utilizzato con RESEED *new_reseed_value*  per modificare il valore Identity corrente. Il nuovo messaggio è *"verifica delle informazioni sull'identità: valore Identity corrente ' \<current identity value> '"*. Esecuzione DBCC completata. Se sono stati visualizzati messaggi di errore DBCC, rivolgersi all'amministratore di sistema".  
  
 Nelle versioni precedenti il messaggio è *"verifica delle informazioni di identità: valore Identity corrente ' \<current identity value> ', valore di colonna corrente ' \<current column value> '. Esecuzione DBCC completata. Se sono stati visualizzati messaggi di errore DBCC, contattare l'amministratore di sistema. "* Il messaggio è invariato quando `DBCC CHECKIDENT` viene specificato con `NORESEED` , senza un secondo parametro o senza un valore di RESEED. Per altre informazioni, vedere [DBCC CHECKIDENT &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkident-transact-sql).  
  
### <a name="behavior-of-exist-function-on-xml-datatype-has-changed"></a>Modifica del comportamento della funzione exist() nel tipo di dati di XML  
 Il comportamento della `exist()` funzione è stato modificato quando si confronta un tipo di dati XML con un valore null a 0 (zero). Prendere in considerazione gli esempi seguenti:  
  
```sql  
DECLARE @test XML;  
SET @test = null;  
SELECT COUNT(1) WHERE @test.exist('/dogs') = 0;  
```  
  
 Nelle versioni precedenti tramite questo confronto veniva restituito 1 (true), mentre ora viene restituito 0 (zero, false).  
  
 I confronti riportati di seguito non sono cambiati:  
  
```sql  
DECLARE @test XML;  
SET @test = null;  
SELECT COUNT(1) WHERE @test.exist('/dogs') = 1; -- 0 expected, 0 returned  
SELECT COUNT(1) WHERE @test.exist('/dogs') IS NULL; -- 1 expected, 1 returned  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Modifiche di rilievo apportate alle funzionalità di motore di database in SQL Server 2014](breaking-changes-to-database-engine-features-in-sql-server-2016.md)   
 [Funzionalità di motore di database deprecate SQL Server 2014](deprecated-database-engine-features-in-sql-server-2016.md)   
 [Funzionalità di motore di database sospese in SQL Server 2014](discontinued-database-engine-functionality-in-sql-server-2016.md)   
 [Livello di compatibilità ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
  
  
