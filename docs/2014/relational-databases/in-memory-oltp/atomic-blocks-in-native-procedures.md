---
title: Blocchi atomici | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 40e0e749-260c-4cfc-a848-444d30c09d85
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 83ec721d214633df7daf9ace5ae45c3cdb51ca97
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62467281"
---
# <a name="atomic-blocks"></a>Blocchi atomici
  `BEGIN ATOMIC` fa parte dello standard SQL ANSI. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta i blocchi atomici solo al livello superiore delle stored procedure compilate in modo nativo.  
  
-   Ogni stored procedure compilata in modo nativo contiene un blocco di istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] . Si tratta di un blocco ATOMIC.  
  
-   Le stored procedure [!INCLUDE[tsql](../../includes/tsql-md.md)] interpretate e non native e i batch ad hoc non supportano i blocchi atomici.  
  
 I blocchi atomici vengono eseguiti (in modo atomico) nella transazione. Tutte le istruzioni nel blocco devono avere esito positivo, altrimenti verrà eseguito il rollback dell'intero blocco al punto di salvataggio creato all'inizio del blocco. Inoltre, per il blocco atomico tutte le impostazioni di sessione sono fisse. L'esecuzione dello stesso blocco atomico in sessioni con impostazioni diverse genera lo stesso comportamento, indipendentemente dalle impostazioni della sessione corrente.  
  
## <a name="transactions-and-error-handling"></a>Transazioni e gestione degli errori  
 Se in una sessione esiste già una transazione (perché un batch ha eseguito un'istruzione `BEGIN TRANSACTION` e la transazione rimane attiva), l'avvio di un blocco atomico creerà un punto di salvataggio nella transazione. Se il blocco viene chiuso senza un'eccezione, viene eseguito il commit del punto di salvataggio creato per il blocco, ma non verrà eseguito il commit della transazione finché non viene eseguito il commit a livello di sessione. Se il blocco genera un'eccezione, viene eseguito il rollback degli effetti del blocco, ma la transazione procede a livello di sessione, a meno che l'eccezione non la termini. Ad esempio, un conflitto di scrittura comporta la fine della transazione, ma non un errore di cast del tipo.  
  
 Se non è presente alcuna transazione attiva in una sessione, `BEGIN ATOMIC` avvia una nuova transazione. Se non viene generata alcuna eccezione all'esterno dell'ambito del blocco, verrà eseguito il commit della transazione alla fine del blocco. Se il blocco genera un'eccezione (l'eccezione non viene rilevata e gestita nel blocco), verrà eseguito il rollback della transazione. Per le transazioni che interessano un singolo blocco atomico (una singola stored procedure compilata in modo nativo), non è necessario scrivere istruzioni `BEGIN TRANSACTION` e `COMMIT` o `ROLLBACK` esplicite.  
  
 Le stored procedure compilate in modo nativo supportano i costrutti `TRY`, `CATCH` e `THROW` per la gestione degli errori. `RAISERROR` non è supportata.  
  
 Nell'esempio seguente viene illustrato il comportamento della gestione degli errori con blocchi atomici e stored procedure compilate in modo nativo:  
  
```sql  
-- sample table  
CREATE TABLE dbo.t1 (  
  c1 int not null primary key nonclustered  
)  
WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
-- sample proc that inserts 2 rows  
CREATE PROCEDURE dbo.usp_t1 @v1 bigint not null, @v2 bigint not null  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS  
BEGIN ATOMIC  
WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english', DELAYED_DURABILITY = ON)  
  
  INSERT dbo.t1 VALUES (@v1)  
  INSERT dbo.t1 VALUES (@v2)  
  
END  
GO  
  
-- insert two rows  
EXEC dbo.usp_t1 1, 2  
GO  
  
-- verify we have no active transaction  
SELECT @@TRANCOUNT  
GO  
  
-- verify the rows 1 and 2 were committed  
SELECT c1 FROM dbo.t1  
GO  
  
-- execute proc with arithmetic overflow  
EXEC dbo.usp_t1 3, 4444444444444  
GO  
-- expected error message:  
-- Msg 8115, Level 16, State 0, Procedure usp_t1  
-- Arithmetic overflow error converting bigint to data type int.  
  
-- verify we have no active transaction  
SELECT @@TRANCOUNT  
GO  
  
-- verify rows 3 was not committed; usp_t1 has been rolled back  
SELECT c1 FROM dbo.t1  
GO  
  
-- start a new transaction  
BEGIN TRANSACTION  
  -- insert rows 3 and 4  
  EXEC dbo.usp_t1 3, 4  
  
  -- verify there is still an active transaction  
  SELECT @@TRANCOUNT  
  
  -- verify the rows 3 and 4 were inserted  
  SELECT c1 FROM dbo.t1 WITH (SNAPSHOT)   
  ORDER BY c1  
  
  -- catch the arithmetic overflow error  
  BEGIN TRY  
    EXEC dbo.usp_t1 5, 4444444444444  
  END TRY  
  BEGIN CATCH  
    PRINT N'Error occurred: ' + error_message()  
  END CATCH  
  
  -- verify there is still an active transaction  
  SELECT @@TRANCOUNT  
  
  -- verify rows 3 and 4 are still in the table, and row 5 has not been inserted  
  SELECT c1 FROM dbo.t1 WITH (SNAPSHOT)   
  ORDER BY c1  
  
COMMIT  
GO  
  
-- verify we have no active transaction  
SELECT @@TRANCOUNT  
GO  
  
-- verify rows 3 and 4 has been committed  
SELECT c1 FROM dbo.t1  
ORDER BY c1  
GO  
```  
  
 I messaggi di errore seguenti specifici delle tabelle ottimizzate per la memoria comportano la fine della transazione. Se si verificano nell'ambito di un blocco atomico, causano l'interruzione della transazione: 10772, 41301, 41302, 41305, 41325, 41332 e 41333.  
  
## <a name="session-settings"></a>Impostazioni sessione  
 Le impostazioni di sessione nei blocchi atomici sono fisse quando la stored procedure è compilata. Alcune impostazioni possono essere specificate con `BEGIN ATOMIC`, mentre altre sono sempre fisse sullo stesso valore.  
  
 Le opzioni seguenti sono necessarie con `BEGIN ATOMIC`:  
  
|Impostazione necessaria|Descrizione|  
|----------------------|-----------------|  
|`TRANSACTION ISOLATION LEVEL`|I valori supportati sono `SNAPSHOT`, `REPEATABLEREAD` e `SERIALIZABLE`.|  
|`LANGUAGE`|Determina i formati data e ora e i messaggi di sistema. Tutti i linguaggi e gli alias in [sys.syslanguages &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql) sono supportati.|  
  
 Le impostazioni seguenti sono facoltative:  
  
|Impostazione facoltativa|Descrizione|  
|----------------------|-----------------|  
|`DATEFORMAT`|Tutti i formati data di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono supportati. Quando viene specificata, `DATEFORMAT` esegue l'override del formato data predefinito associato a `LANGUAGE`.|  
|`DATEFIRST`|Quando viene specificata, `DATEFIRST` esegue l'override dell'impostazione predefinita associata a `LANGUAGE`.|  
|`DELAYED_DURABILITY`|I valori supportati sono `OFF` e `ON`.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]il commit delle transazioni può essere completamente durevole, il valore predefinito o con durabilità ritardata. Per ulteriori informazioni, vedere [controllo della durabilità delle transazioni](../logs/control-transaction-durability.md).|  
  
 Le opzioni SET seguenti presentano lo stesso valore predefinito di sistema per tutti i blocchi atomici in tutte le stored procedure compilate in modo nativo:  
  
|Opzione SET|Impostazione predefinita di sistema per i blocchi atomici|  
|----------------|--------------------------------------|  
|ANSI_NULLS|ON|  
|ANSI_PADDING|ON|  
|ANSI_WARNING|ON|  
|ARITHABORT|ATTIVA|  
|ARITHIGNORE|OFF|  
|CONCAT_NULL_YIELDS_NULL|ATTIVA|  
|IDENTITY_INSERT|OFF|  
|NOCOUNT|ON|  
|NUMERIC_ROUNDABORT|OFF|  
|QUOTED_IDENTIFIER|ON|  
|ROWCOUNT|0|  
|TEXTSIZE|0|  
|XACT_ABORT|OFF<br /><br /> Le eccezioni non rilevate causano il rollback dei blocchi atomici, ma non l'interruzione della transazione, a meno che l'errore non comporti la fine della transazione.|  
  
## <a name="see-also"></a>Vedi anche  
 [stored procedure compilate in modo nativo](natively-compiled-stored-procedures.md)  
  
  
