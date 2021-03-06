---
description: Funzione SQLForeignKeys
title: Funzione SQLForeignKeys | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLForeignKeys
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLForeignKeys
helpviewer_keywords:
- SQLForeignKeys function [ODBC]
ms.assetid: 07f3f645-f643-4d39-9a10-70a72f24e608
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 802153837d53c6886b44511fbdffe6efa6b83281
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491304"
---
# <a name="sqlforeignkeys-function"></a>Funzione SQLForeignKeys
**Conformità**  
 Versione introdotta: ODBC 1,0 Standard Compliance: ODBC  
  
 **Summary**  
 **SQLForeignKeys** può restituire:  
  
-   Elenco di chiavi esterne nella tabella specificata, ovvero le colonne della tabella specificata che fanno riferimento alle chiavi primarie in altre tabelle.  
  
-   Elenco di chiavi esterne in altre tabelle che fanno riferimento alla chiave primaria nella tabella specificata.  
  
 Il driver restituisce ogni elenco come un set di risultati nell'istruzione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
  
SQLRETURN SQLForeignKeys(  
     SQLHSTMT       StatementHandle,  
     SQLCHAR *      PKCatalogName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      PKSchemaName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      PKTableName,  
     SQLSMALLINT    NameLength3,  
     SQLCHAR *      FKCatalogName,  
     SQLSMALLINT    NameLength4,  
     SQLCHAR *      FKSchemaName,  
     SQLSMALLINT    NameLength5,  
     SQLCHAR *      FKTableName,  
     SQLSMALLINT    NameLength6);  
```  
  
## <a name="arguments"></a>Argomenti  
 *StatementHandle*  
 Input Handle di istruzione.  
  
 *PKCatalogName*  
 Input Nome del catalogo della tabella della chiave primaria. Se un driver supporta i cataloghi per alcune tabelle ma non per altri, ad esempio quando il driver recupera dati da DBMS diversi, una stringa vuota ("") indica le tabelle che non contengono cataloghi. *PKCatalogName* non può contenere un criterio di ricerca di stringhe.  
  
 Se l'attributo SQL_ATTR_METADATA_ID Statement è impostato su SQL_TRUE, *PKCatalogName* viene considerato come un identificatore e il relativo case non è significativo. Se è SQL_FALSE, *PKCatalogName* è un argomento normale; viene trattato letteralmente e il suo caso è significativo. Per ulteriori informazioni, vedere [arguments in Catalog Functions](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 *NameLength1*  
 Input Lunghezza di **PKCatalogName*, in caratteri.  
  
 *PKSchemaName*  
 Input Nome dello schema della tabella della chiave primaria. Se un driver supporta gli schemi per alcune tabelle ma non per altri, ad esempio quando il driver recupera dati da DBMS diversi, una stringa vuota ("") indica le tabelle che non contengono schemi. *PKSchemaName* non può contenere un criterio di ricerca di stringhe.  
  
 Se l'attributo SQL_ATTR_METADATA_ID Statement è impostato su SQL_TRUE, *PKSchemaName* viene considerato come un identificatore e il relativo case non è significativo. Se è SQL_FALSE, *PKSchemaName* è un argomento normale; viene trattato letteralmente e il suo caso è significativo.  
  
 *NameLength2*  
 Input Lunghezza di **PKSchemaName*, in caratteri.  
  
 *PKTableName*  
 Input Nome della tabella della chiave primaria. *PKTableName* non può contenere un criterio di ricerca di stringhe.  
  
 Se l'attributo SQL_ATTR_METADATA_ID Statement è impostato su SQL_TRUE, *PKTableName* viene considerato come un identificatore e il relativo case non è significativo. Se è SQL_FALSE, *PKTableName* è un argomento normale; viene trattato letteralmente e il suo caso è significativo.  
  
 *NameLength3*  
 Input Lunghezza di **PKTableName*, in caratteri.  
  
 *FKCatalogName*  
 Input Nome del catalogo della tabella di chiave esterna. Se un driver supporta i cataloghi per alcune tabelle ma non per altri, ad esempio quando il driver recupera dati da DBMS diversi, una stringa vuota ("") indica le tabelle che non contengono cataloghi. *FKCatalogName* non può contenere un criterio di ricerca di stringhe.  
  
 Se l'attributo SQL_ATTR_METADATA_ID Statement è impostato su SQL_TRUE, *FKCatalogName* viene considerato come un identificatore e il relativo case non è significativo. Se è SQL_FALSE, *FKCatalogName* è un argomento normale; viene trattato letteralmente e il suo caso è significativo.  
  
 *NameLength4*  
 Input Lunghezza di **FKCatalogName*, in caratteri.  
  
 *FKSchemaName*  
 Input Nome dello schema della tabella di chiave esterna. Se un driver supporta gli schemi per alcune tabelle ma non per altri, ad esempio quando il driver recupera dati da DBMS diversi, una stringa vuota ("") indica le tabelle che non contengono schemi. *FKSchemaName* non può contenere un criterio di ricerca di stringhe.  
  
 Se l'attributo SQL_ATTR_METADATA_ID Statement è impostato su SQL_TRUE, *FKSchemaName* viene considerato come un identificatore e il relativo case non è significativo. Se è SQL_FALSE, *FKSchemaName* è un argomento normale; viene trattato letteralmente e il suo caso è significativo.  
  
 *NameLength5*  
 Input Lunghezza di **FKSchemaName*, in caratteri.  
  
 *FKTableName*  
 Input Nome della tabella della chiave esterna. *FKTableName* non può contenere un criterio di ricerca di stringhe.  
  
 Se l'attributo SQL_ATTR_METADATA_ID Statement è impostato su SQL_TRUE, *FKTableName* viene considerato come un identificatore e il relativo case non è significativo. Se è SQL_FALSE, *FKTableName* è un argomento normale; viene trattato letteralmente e il suo caso è significativo.  
  
 *NameLength6*  
 Input Lunghezza di **FKTableName*, in caratteri.  
  
## <a name="returns"></a>Restituisce  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLForeignKeys** restituisce SQL_ERROR o SQL_SUCCESS_WITH_INFO, è possibile ottenere un valore SQLSTATE associato chiamando **SQLGetDiagRec** con *HandleType* di SQL_HANDLE_STMT e un *handle* di *statementHandle*. Nella tabella seguente sono elencati i valori SQLSTATE restituiti in genere da **SQLForeignKeys** e ne viene illustrato ciascuno nel contesto di questa funzione; la notazione "(DM)" precede le descrizioni di SQLSTATE restituite da Gestione driver. Il codice restituito associato a ogni valore SQLSTATE è SQL_ERROR, a meno che non sia specificato diversamente.  
  
|SQLSTATE|Errore|Descrizione|  
|--------------|-----------|-----------------|  
|01000|Avviso generale|Messaggio informativo specifico del driver. (La funzione restituisce SQL_SUCCESS_WITH_INFO.)|  
|08S01|Errore collegamento comunicazione|Il collegamento di comunicazione tra il driver e l'origine dati a cui è stato connesso il driver non è riuscito prima del completamento dell'elaborazione della funzione.|  
|24000|Stato del cursore non valido|Un cursore è stato aperto in *statementHandle*e **SQLFetch** o **SQLFetchScroll** è stato chiamato. Questo errore viene restituito da Gestione driver se **SQLFetch** o **SQLFetchScroll** non ha restituito SQL_NO_DATA e viene restituito dal driver se **SQLFetch** o **SQLFetchScroll** ha restituito SQL_NO_DATA.<br /><br /> Un cursore è stato aperto in *statementHandle*, ma non è stato chiamato **SQLFetch** o **SQLFetchScroll** .|  
|40001|Errore di serializzazione|È stato eseguito il rollback della transazione a causa di un deadlock delle risorse con un'altra transazione.|  
|40003|Completamento istruzione sconosciuto|La connessione associata non è riuscita durante l'esecuzione di questa funzione e non è possibile determinare lo stato della transazione.|  
|HY000|Errore generale:|Si è verificato un errore per il quale non esiste un valore SQLSTATE specifico e per il quale non è stato definito alcun valore SQLSTATE specifico dell'implementazione. Il messaggio di errore restituito da **SQLGetDiagRec** nel buffer * \* MessageText* descrive l'errore e la sua origine.|  
|HY001|Errore di allocazione della memoria|Il driver non è stato in grado di allocare memoria necessaria per supportare l'esecuzione o il completamento della funzione.|  
|HY008|Operation canceled|L'elaborazione asincrona è stata abilitata per *statementHandle*. La funzione è stata chiamata e prima del completamento dell'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato su *statementHandle*e quindi la funzione è stata chiamata nuovamente su *statementHandle*.<br /><br /> La funzione è stata chiamata e prima del completamento dell'esecuzione, **SQLCancel** o **SQLCancelHandle** è stato chiamato su *statementHandle* da un thread diverso in un'applicazione multithread.|  
|HY009|Uso non valido del puntatore null|(DM) gli argomenti *PKTableName* e *FKTableName* sono entrambi puntatori null.<br /><br /> L'attributo SQL_ATTR_METADATA_ID Statement è stato impostato su SQL_TRUE, l'argomento *FKCatalogName* o *PKCatalogName* è un puntatore null e il SQL_CATALOG_NAME *InfoType* restituisce i nomi dei cataloghi supportati.<br /><br /> (DM) l'attributo SQL_ATTR_METADATA_ID Statement è stato impostato su SQL_TRUE e l'argomento *FKSchemaName*, *PKSchemaName*, *FKTableName*o *PKTableName* è un puntatore null.|  
|HY010|Errore sequenza funzione|(DM) è stata chiamata una funzione in esecuzione asincrona per l'handle di connessione associato a *statementHandle*. Questa funzione asincrona era ancora in esecuzione quando è stata chiamata la funzione SQLForeignKeys.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**o **SQLMoreResults** è stato chiamato per *statementHandle* e restituito SQL_PARAM_DATA_AVAILABLE. Questa funzione è stata chiamata prima del recupero dei dati per tutti i parametri trasmessi.<br /><br /> (DM) è stata chiamata una funzione in esecuzione asincrona (non questa) per *statementHandle* ed è stata ancora eseguita quando è stata chiamata la funzione.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**o **SQLSetPos** è stato chiamato per *statementHandle* e restituito SQL_NEED_DATA. Questa funzione è stata chiamata prima dell'invio dei dati per tutti i parametri o le colonne data-at-execution.|  
|HY013|Errore di gestione della memoria|Impossibile elaborare la chiamata di funzione perché non è possibile accedere agli oggetti memoria sottostante, probabilmente a causa di condizioni di memoria insufficiente.|  
|HY090|Lunghezza della stringa o del buffer non valida|(DM) il valore di uno degli argomenti della lunghezza del nome è minore di 0 ma non uguale a SQL_NTS.|  
|||Il valore di uno degli argomenti della lunghezza del nome supera il valore di lunghezza massima per il nome corrispondente. (Vedere "Commenti").|  
|HY117|Connessione sospesa a causa di uno stato di transazione sconosciuto. Sono consentite solo le funzioni di disconnessione e di sola lettura.|(DM) per ulteriori informazioni sullo stato Suspended, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Funzionalità facoltativa non implementata|È stato specificato un nome di catalogo e il driver o l'origine dati non supporta i cataloghi.<br /><br /> È stato specificato un nome di schema e il driver o l'origine dati non supporta gli schemi.|  
|||La combinazione delle impostazioni correnti degli attributi SQL_ATTR_CONCURRENCY e SQL_ATTR_CURSOR_TYPE istruzione non è supportata dal driver o dall'origine dati.<br /><br /> L'attributo SQL_ATTR_USE_BOOKMARKS Statement è stato impostato su SQL_UB_VARIABLE e l'attributo SQL_ATTR_CURSOR_TYPE Statement è stato impostato su un tipo di cursore per il quale il driver non supporta i segnalibri.|  
|HYT00|Timeout|Il periodo di timeout della query è scaduto prima che l'origine dati restituisse il set di risultati. Il periodo di timeout viene impostato tramite **SQLSetStmtAttr**, SQL_ATTR_QUERY_TIMEOUT.|  
|HYT01|Timeout connessione scaduto|Il periodo di timeout della connessione è scaduto prima che l'origine dati abbia risposto alla richiesta. Il periodo di timeout della connessione viene impostato tramite **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Il driver non supporta questa funzione|(DM) il driver associato a *statementHandle* non supporta la funzione.|  
|IM017|Polling disabilitato in modalità di notifica asincrona|Ogni volta che viene utilizzato il modello di notifica, il polling è disabilitato.|  
|IM018|**SQLCompleteAsync** non è stato chiamato per completare l'operazione asincrona precedente su questo handle.|Se la chiamata di funzione precedente nell'handle restituisce SQL_STILL_EXECUTING e se è abilitata la modalità di notifica, è necessario chiamare **SQLCompleteAsync** sull'handle per eseguire la post-elaborazione e completare l'operazione.|  
  
## <a name="comments"></a>Commenti  
 Per informazioni sul modo in cui le informazioni restituite da questa funzione potrebbero essere utilizzate, vedere [utilizzi dei dati del catalogo](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Se \* *PKTableName* contiene un nome di tabella, **SQLForeignKeys** restituisce un set di risultati che contiene la chiave primaria della tabella specificata e tutte le chiavi esterne che vi fanno riferimento. L'elenco delle chiavi esterne in altre tabelle non include chiavi esterne che puntano a vincoli UNIQUE nella tabella specificata.  
  
 Se \* *FKTableName* contiene un nome di tabella, **SQLForeignKeys** restituisce un set di risultati contenente tutte le chiavi esterne della tabella specificata che puntano alle chiavi primarie di altre tabelle e alle chiavi primarie nelle altre tabelle a cui fanno riferimento. L'elenco di chiavi esterne nella tabella specificata non contiene chiavi esterne che fanno riferimento a vincoli UNIQUE in altre tabelle.  
  
 Se \* *PKTableName* e \* *FKTableName* contengono nomi di tabella, **SQLForeignKeys** restituisce le chiavi esterne nella tabella specificata in \* *FKTableName* che fanno riferimento alla chiave primaria della tabella specificata in **PKTableName*. Si tratta di una chiave al massimo.  
  
> [!NOTE]  
>  Per ulteriori informazioni sull'utilizzo generale, sugli argomenti e sui dati restituiti delle funzioni del catalogo ODBC, vedere [funzioni di catalogo](../../../odbc/reference/develop-app/catalog-functions.md).  
  
 **SQLForeignKeys** restituisce i risultati come set di risultati standard. Se vengono richieste le chiavi esterne associate a una chiave primaria, il set di risultati viene ordinato in base FKTABLE_CAT, FKTABLE_SCHEM, FKTABLE_NAME e KEY_SEQ. Se vengono richieste le chiavi primarie associate a una chiave esterna, il set di risultati viene ordinato in base PKTABLE_CAT, PKTABLE_SCHEM, PKTABLE_NAME e KEY_SEQ. Nella tabella seguente sono elencate le colonne del set di risultati.  
  
 Le lunghezze delle colonne VARCHAR non vengono visualizzate nella tabella. le lunghezze effettive dipendono dall'origine dati. Per determinare le lunghezze effettive delle colonne PKTABLE_CAT o FKTABLE_CAT, PKTABLE_SCHEM o FKTABLE_SCHEM, PKTABLE_NAME o FKTABLE_NAME e PKCOLUMN_NAME o FKCOLUMN_NAME, un'applicazione può chiamare **SQLGetInfo** con le opzioni SQL_MAX_CATALOG_NAME_LEN, SQL_MAX_SCHEMA_NAME_LEN, SQL_MAX_TABLE_NAME_LEN e SQL_MAX_COLUMN_NAME_LEN.  
  
 Le colonne seguenti sono state rinominate per ODBC 3 *. x.* Le modifiche al nome di colonna non influiscono sulla compatibilità con le versioni precedenti perché le applicazioni vengono associate per numero di colonna  
  
|ODBC 2,0-colonna|Colonna ODBC 3 *. x*|  
|---------------------|-----------------------|  
|PKTABLE_QUALIFIER|PKTABLE_CAT|  
|PKTABLE_OWNER|PKTABLE_SCHEM|  
|FKTABLE_QUALIFIER|FK_TABLE_CAT|  
|FKTABLE_OWNER|FKTABLE_SCHEM|  
  
 Nella tabella seguente sono elencate le colonne del set di risultati. È possibile definire colonne aggiuntive oltre la colonna 14 (osservazioni) dal driver. Un'applicazione deve ottenere l'accesso alle colonne specifiche del driver eseguendo il conteggio a discesa dalla fine del set di risultati anziché specificare una posizione ordinale esplicita. Per ulteriori informazioni, vedere [dati restituiti da funzioni di catalogo](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md).  
  
|Nome colonna|Numero di colonna|Tipo di dati|Commenti|  
|-----------------|-------------------|---------------|--------------|  
|PKTABLE_CAT (ODBC 1,0)|1|Varchar|Nome del catalogo della tabella della chiave primaria; NULL se non è applicabile all'origine dati. Se un driver supporta i cataloghi per alcune tabelle ma non per altri, ad esempio quando il driver recupera dati da DBMS diversi, restituisce una stringa vuota ("") per le tabelle che non contengono cataloghi.|  
|PKTABLE_SCHEM (ODBC 1,0)|2|Varchar|Nome dello schema della tabella della chiave primaria; NULL se non è applicabile all'origine dati. Se un driver supporta schemi per alcune tabelle ma non per altri, ad esempio quando il driver recupera dati da DBMS diversi, restituisce una stringa vuota ("") per le tabelle che non dispongono di schemi.|  
|PKTABLE_NAME (ODBC 1,0)|3|Varchar NOT NULL|Nome della tabella della chiave primaria.|  
|PKCOLUMN_NAME (ODBC 1,0)|4|Varchar NOT NULL|Nome della colonna chiave primaria. Il driver restituisce una stringa vuota per una colonna che non dispone di un nome.|  
|FKTABLE_CAT (ODBC 1,0)|5|Varchar|Nome del catalogo della tabella di chiave esterna; NULL se non è applicabile all'origine dati. Se un driver supporta i cataloghi per alcune tabelle ma non per altri, ad esempio quando il driver recupera dati da DBMS diversi, restituisce una stringa vuota ("") per le tabelle che non contengono cataloghi.|  
|FKTABLE_SCHEM (ODBC 1,0)|6|Varchar|Nome schema della tabella della chiave esterna; NULL se non è applicabile all'origine dati. Se un driver supporta schemi per alcune tabelle ma non per altri, ad esempio quando il driver recupera dati da DBMS diversi, restituisce una stringa vuota ("") per le tabelle che non dispongono di schemi.|  
|FKTABLE_NAME (ODBC 1,0)|7|Varchar NOT NULL|Nome della tabella della chiave esterna.|  
|FKCOLUMN_NAME (ODBC 1,0)|8|Varchar NOT NULL|Nome della colonna chiave esterna. Il driver restituisce una stringa vuota per una colonna che non dispone di un nome.|  
|KEY_SEQ (ODBC 1,0)|9|Smallint non NULL|Numero di sequenza della colonna nella chiave (a partire da 1).|  
|UPDATE_RULE (ODBC 1,0)|10|Smallint|Azione da applicare alla chiave esterna quando l'operazione SQL è **aggiornata**. Può avere uno dei valori seguenti. La tabella a cui si fa riferimento è la tabella che contiene la chiave primaria; la tabella di riferimento è la tabella che contiene la chiave esterna.<br /><br /> SQL_CASCADE: quando viene aggiornata la chiave primaria della tabella a cui si fa riferimento, viene aggiornata anche la chiave esterna della tabella di riferimento.<br /><br /> SQL_NO_ACTION: se un aggiornamento della chiave primaria della tabella a cui si fa riferimento provocherebbe un "riferimento in sospeso" nella tabella di riferimento, ovvero le righe nella tabella di riferimento non avrebbero alcuna controparte nella tabella a cui si fa riferimento, l'aggiornamento viene rifiutato. Se un aggiornamento della chiave esterna della tabella di riferimento introduce un valore che non esiste come valore della chiave primaria della tabella a cui si fa riferimento, l'aggiornamento viene rifiutato. Questa azione equivale all'azione SQL_RESTRICT in ODBC 2 *. x*.<br /><br /> SQL_SET_NULL: quando una o più righe nella tabella di riferimento vengono aggiornate in modo tale che uno o più componenti della chiave primaria vengano modificati, i componenti della chiave esterna nella tabella di riferimento che corrispondono ai componenti modificati della chiave primaria vengono impostati su NULL in tutte le righe corrispondenti della tabella di riferimento.<br /><br /> SQL_SET_DEFAULT: quando una o più righe della tabella a cui viene fatto riferimento vengono aggiornate in modo tale che uno o più componenti della chiave primaria vengono modificati, i componenti della chiave esterna nella tabella di riferimento che corrispondono ai componenti modificati della chiave primaria vengono impostati sui valori predefiniti applicabili in tutte le righe corrispondenti della tabella di riferimento.<br /><br /> NULL se non è applicabile all'origine dati.|  
|DELETE_RULE (ODBC 1,0)|11|Smallint|Azione da applicare alla chiave esterna quando l'operazione SQL è **Delete**. Può avere uno dei valori seguenti. La tabella a cui si fa riferimento è la tabella che contiene la chiave primaria; la tabella di riferimento è la tabella che contiene la chiave esterna.<br /><br /> SQL_CASCADE: quando viene eliminata una riga nella tabella a cui si fa riferimento, vengono eliminate anche tutte le righe corrispondenti nelle tabelle di riferimento.<br /><br /> SQL_NO_ACTION: se un'eliminazione di una riga nella tabella a cui si fa riferimento provocherebbe un "riferimento in sospeso" nella tabella di riferimento, ovvero le righe nella tabella di riferimento non avrebbero alcuna controparte nella tabella a cui si fa riferimento, l'aggiornamento viene rifiutato. Questa azione equivale all'azione SQL_RESTRICT in ODBC 2 *. x*.<br /><br /> SQL_SET_NULL: quando una o più righe della tabella a cui viene fatto riferimento vengono eliminate, ogni componente della chiave esterna della tabella di riferimento viene impostato su NULL in tutte le righe corrispondenti della tabella di riferimento.<br /><br /> SQL_SET_DEFAULT: quando una o più righe della tabella a cui viene fatto riferimento vengono eliminate, ogni componente della chiave esterna della tabella di riferimento viene impostato sul valore predefinito applicabile in tutte le righe corrispondenti della tabella di riferimento.<br /><br /> NULL se non è applicabile all'origine dati.|  
|FK_NAME (ODBC 2,0)|12|Varchar|Nome della chiave esterna. NULL se non è applicabile all'origine dati.|  
|PK_NAME (ODBC 2,0)|13|Varchar|Nome della chiave primaria. NULL se non è applicabile all'origine dati.|  
|RINVIO (ODBC 3,0)|14|Smallint|SQL_INITIALLY_DEFERRED, SQL_INITIALLY_IMMEDIATE, SQL_NOT_DEFERRABLE.|  
  
## <a name="code-example"></a>Esempio di codice  
 Come illustrato nella tabella seguente, in questo esempio vengono utilizzate tre tabelle, denominate ORDERs, LINES e CUSTOMers.  
  
|ORDERS|LINEE|CLIENTI|  
|------------|-----------|---------------|  
|ORDERID|ORDERID|CUSTID|  
|CUSTID|LINEE|NAME|  
|OPENDATE|PARTID|Indirizzo|  
|Venditore|QUANTITÀ|TELEFONO|  
|STATO|||  
  
 Nella tabella ORDERs, CUSTID identifica il cliente a cui è stata effettuata la vendita. Si tratta di una chiave esterna che fa riferimento a CUSTID nella tabella CUSTOMers.  
  
 Nella tabella LINES, ORDERID identifica l'ordine di vendita a cui è associata l'elemento della riga. Si tratta di una chiave esterna che fa riferimento a ORDERID nella tabella ORDERs.  
  
 Questo esempio chiama **SQLPrimaryKeys** per ottenere la chiave primaria della tabella Orders. Il set di risultati avrà una riga. le colonne significative sono illustrate nella tabella seguente.  
  
|TABLE_NAME|COLUMN_NAME|KEY_SEQ|  
|-----------------|------------------|--------------|  
|ORDERS|ORDERID|1|  
  
 Nell'esempio viene quindi chiamato **SQLForeignKeys** per ottenere le chiavi esterne in altre tabelle che fanno riferimento alla chiave primaria della tabella Orders. Il set di risultati avrà una riga. le colonne significative sono illustrate nella tabella seguente.  
  
|PKTABLE_NAME|PKCOLUMN_NAME|FKTABLE_NAME|FKCOLUMN_NAME|KEY_SEQ|  
|-------------------|--------------------|-------------------|--------------------|--------------|  
|ORDERS|CUSTID|LINEE|CUSTID|1|  
  
 Infine, nell'esempio viene chiamato **SQLForeignKeys** per ottenere le chiavi esterne nella tabella Orders che fanno riferimento alle chiavi primarie di altre tabelle. Il set di risultati avrà una riga. le colonne significative sono illustrate nella tabella seguente.  
  
|PKTABLE_NAME|PKCOLUMN_NAME|FKTABLE_NAME|FKCOLUMN_NAME|KEY_SEQ|  
|-------------------|--------------------|-------------------|--------------------|--------------|  
|CLIENTI|CUSTID|ORDERS|CUSTID|1|  
  
```cpp  
#define TAB_LEN SQL_MAX_TABLE_NAME_LEN + 1  
#define COL_LEN SQL_MAX_COLUMN_NAME_LEN + 1  
  
LPSTR   szTable;              /* Table to display */  
  
UCHAR szPkTable[TAB_LEN];   /* Primary key table name */  
UCHAR szFkTable[TAB_LEN];   /* Foreign key table name */  
UCHAR szPkCol[COL_LEN];     /* Primary key column */  
UCHAR szFkCol[COL_LEN];     /* Foreign key column */  
  
SQLHSTMT      hstmt;  
SQLINTEGER    cbPkTable, cbPkCol, cbFkTable, cbFkCol, cbKeySeq;  
SQLSMALLINT   iKeySeq;  
SQLRETURN     retcode;  
  
// Bind the columns that describe the primary and foreign keys.  
// Ignore the table schema, name, and catalog for this example.  
  
SQLBindCol(hstmt, 3, SQL_C_CHAR, szPkTable, TAB_LEN, &cbPkTable);  
SQLBindCol(hstmt, 4, SQL_C_CHAR, szPkCol, COL_LEN, &cbPkCol);  
SQLBindCol(hstmt, 5, SQL_C_SSHORT, &iKeySeq, TAB_LEN, &cbKeySeq);  
SQLBindCol(hstmt, 7, SQL_C_CHAR, szFkTable, TAB_LEN, &cbFkTable);  
SQLBindCol(hstmt, 8, SQL_C_CHAR, szFkCol, COL_LEN, &cbFkCol);  
  
strcpy_s(szTable, sizeof(szTable), "ORDERS");  
  
/* Get the names of the columns in the primary key. */  
  
retcode = SQLPrimaryKeys(hstmt,  
         NULL, 0,             /* Catalog name */  
         NULL, 0,             /* Schema name */  
         szTable, SQL_NTS);   /* Table name */  
  
while ((retcode == SQL_SUCCESS) || (retcode == SQL SUCCESS_WITH_INFO)) {  
  
   /* Fetch and display the result set. This will be a list of the */  
   /* columns in the primary key of the ORDERS table. */  
  
   retcode = SQLFetch(hstmt);  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
      fprintf(out, "Table: %s Column: %s Key Seq: %hd \n", szPkTable, szPkCol,  
      iKeySeq);  
}  
  
/* Close the cursor (the hstmt is still allocated). */  
  
SQLFreeStmt(hstmt, SQL_CLOSE);  
  
/* Get all the foreign keys that refer to ORDERS primary key.*/   
  
retcode = SQLForeignKeys(hstmt,  
         NULL, 0,            /* Primary catalog */  
         NULL, 0,            /* Primary schema */  
         szTable, SQL_NTS,   /* Primary table */  
         NULL, 0,            /* Foreign catalog */  
         NULL, 0,            /* Foreign schema */  
         NULL, 0);           /* Foreign table */  
  
while ((retcode == SQL_SUCCESS) || (retcode == SQL_SUCCESS_WITH_INFO)) {  
  
/* Fetch and display the result set. This will be all of the */  
/* foreign keys in other tables that refer to the ORDERS */  
/* primary key. */  
  
   retcode = SQLFetch(hstmt);  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
      fprintf(out, "%-s ( %-s ) <-- %-s ( %-s )\n", szPkTable,  
               szPkCol, szFkTable, szFkCol);  
}  
  
/* Close the cursor (the hstmt is still allocated). */  
  
SQLFreeStmt(hstmt, SQL_CLOSE);  
  
/* Get all the foreign keys in the ORDERS table. */  
  
retcode = SQLForeignKeys(hstmt,  
         NULL, 0,             /* Primary catalog */  
         NULL, 0,             /* Primary schema */  
         NULL, 0,             /* Primary table */  
         NULL, 0,             /* Foreign catalog */  
         NULL, 0,             /* Foreign schema */  
         szTable, SQL_NTS);   /* Foreign table */  
  
while ((retcode == SQL_SUCCESS) || (retcode == SQL_SUCCESS_WITH_INFO)) {  
  
/* Fetch and display the result set. This will be all of the */  
/* primary keys in other tables that are referred to by foreign */  
/* keys in the ORDERS table. */  
  
   retcode = SQLFetch(hstmt);  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
      fprintf(out, "%-s ( %-s )--> %-s ( %-s )\n", szFkTable, szFkCol, szPkTable, szPkCol);  
}  
  
/* Free the hstmt. */  
SQLFreeStmt(hstmt, SQL_DROP);  
```  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Associazione di un buffer a una colonna in un set di risultati|[Funzione SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Annullamento dell'elaborazione di istruzioni|[Funzione SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Recupero di una singola riga o di un blocco di dati in una direzione di sola trasmissione|[Funzione SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Recupero di un blocco di dati o scorrimento di un set di risultati|[Funzione SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Restituzione delle colonne di una chiave primaria|[Funzione SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
|Restituzione di statistiche e indici tabella|[Funzione SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento sulle API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
