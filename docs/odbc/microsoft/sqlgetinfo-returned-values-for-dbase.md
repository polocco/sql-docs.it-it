---
description: Valori restituiti da SQLGetInfo per dBASE
title: Valori restituiti da SQLGetInfo per dBASE | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], DBasedriver
- desktop database drivers [ODBC], DBasedriver
- SQLGetInfo function [ODBC], dBASE Driver
- DBase driver [ODBC], SQLGetInfo
- ODBC desktop database drivers [ODBC], DBasedriver
ms.assetid: af64753c-c758-4b68-954b-2c84e3bbd93f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e19e4f46771166dbb08df4fa210f4cc161413aed
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421725"
---
# <a name="sqlgetinfo-returned-values-for-dbase"></a>Valori restituiti da SQLGetInfo per dBASE
Nella tabella seguente sono elencati i #defines del linguaggio C per l'argomento *fInfoType* e i valori corrispondenti restituiti da **SQLGetInfo**. Queste informazioni possono essere recuperate passando le #defines del linguaggio C elencate a **SQLGetInfo** nell'argomento *fInfoType* . Per ulteriori informazioni sui valori restituiti da **SQLGetInfo**, vedere *ODBC Programmer ' s Reference*.  
  
> [!NOTE]  
>  Dove **SQLGetInfo** restituisce una maschera di bit a 32 bit, una barra verticale (&#124;) rappresenta un OR bit per bit.  
  
|InfoType|Valore restituito|  
|--------------|--------------------|  
|SQL_ACCESSIBLE_PROCEDURES|"N"|  
|SQL_ACCESSIBLE_TABLES|"Y"|  
|SQL_ACTIVE_ENVIRONMENTS|0|  
|SQL_AGGREGATE_FUNCTIONS|Tutti impostati|  
|SQL_ALTER_DOMAIN|0|  
|SQL_ALTER_TABLE|Più valori|  
|SQL_ASYNC_MODE|0|  
|SQL_BATCH_ROW_COUNT|0|  
|SQL_BATCH_SUPPORT|0|  
|SQL_BOOKMARK_PERSISTENCE|Più valori|  
|SQL_CATALOG_LOCATION|SQL_QL_START|  
|SQL_CATALOG_NAME|"Y"|  
|SQL_CATALOG_NAME_SEPARATOR|"\\"|  
|SQL_CATALOG_TERM|Directory|  
|SQL_CATALOG_USAGE|Più valori|  
|SQL_COLLATION_SEQ|""|  
|SQL_COLUMN_ALIAS|"Y"|  
|SQL_CONCAT_NULL_BEHAVIOR|SQL_CB_NON_NULL|  
|SQL_CONVERT_BIGINT|0|  
|SQL_CONVERT_BINARY|Più valori|  
|SQL_CONVERT_BIT|0|  
|SQL_CONVERT_CHAR|Più valori|  
|SQL_CONVERT_DATE|Più valori|  
|SQL_CONVERT_DECIMAL|0|  
|SQL_CONVERT_DOUBLE|Più valori|  
|SQL_CONVERT_FLOAT|Più valori|  
|SQL_CONVERT_FUNCTIONS|SQL_FN_CVT_CONVERT|  
|SQL_CONVERT_INTEGER|Più valori|  
|SQL_CONVERT_LONGVARBINARY|Più valori|  
|SQL_CONVERT_LONGVARCHAR|Più valori|  
|SQL_CONVERT_NUMERIC|Più valori|  
|SQL_CONVERT_REAL|Più valori|  
|SQL_CONVERT_SMALLINT|Più valori|  
|SQL_CONVERT_TIME|Più valori|  
|SQL_CONVERT_TIMESTAMP|Più valori|  
|SQL_CONVERT_TINYINT|Più valori|  
|SQL_CONVERT_VARBINARY|Più valori|  
|SQL_CONVERT_VARCHAR|Più valori|  
|SQL_CORRELATION_NAME|SQL_CN_ANY|  
|SQL_CREATE_ASSERTION|0|  
|SQL_CREATE_CHARACTER_SET|0|  
|SQL_CREATE_COLLATION|0|  
|SQL_CREATE_DOMAIN|0|  
|SQL_CREATE_SCHEMA|0|  
|SQL_CREATE_TABLE|SQL_CT_CREATE_TABLE|  
|SQL_CREATE_TRANSLATION|0|  
|SQL_CREATE_VIEW|0|  
|SQL_CURSOR_COMMIT_BEHAVIOR|SQL_CB_CLOSE|  
|SQL_CURSOR_ROLLBACK_BEHAVIOR|SQL_CB_CLOSE|  
|SQL_CURSOR_SENSITIVITY|SQL_UNSPECIFIED|  
|SQL_DATA_SOURCE_NAME|DSN da Odbc.ini o "" se la parola chiave del DRIVER viene utilizzata in Odbc.ini|  
|SQL_DATA_SOURCE_READ_ONLY|"N" (dipende dall'origine dati.)|  
|SQL_DATABASE_NAME|Directory database corrente|  
|SQL_DATETIME_LITERALS|0|  
|SQL_DBMS_NAME|DBASE|  
|SQL_DBMS_VER|Più valori|  
|SQL_DDL_INDEX|Più valori|  
|SQL_DEFAULT_TXN_ISOLATION|0|  
|SQL_DESCRIBE_PARAMETER|0|  
|SQL_DRIVER_HDBC|Gestito da Gestione driver.|  
|SQL_DRIVER_HENV|Gestito da Gestione driver.|  
|SQL_DRIVER_HLIB|Gestito da Gestione driver.|  
|SQL_DRIVER_HSTMT|Gestito da Gestione driver.|  
|SQL_DRIVER_NAME|"OdbcJt32.dll"|  
|SQL_DRIVER_ODBC_VER|"3.51.0000"|  
|SQL_DRIVER_VER|"4,00.*nnnn*" (*nnnn* specifica la data di compilazione)|  
|SQL_DROP_ASSERTION|0|  
|SQL_DROP_CHARACTER_SET|0|  
|SQL_DROP_COLLATION|0|  
|SQL_DROP_DOMAIN|0|  
|SQL_DROP_SCHEMA|0|  
|SQL_DROP_TABLE|SQL_DT_DROP_TABLE|  
|SQL_DROP_TRANSLATION|0|  
|SQL_DROP_VIEW|SQL_DV_DROP_VIEW|  
|SQL_EXPRESSIONS_IN_ORDERBY|"Y"|  
|SQL_FILE_USAGE|SQL_FILE_TABLE|  
|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1|SQL_CA1_NEXT|  
|SQL_GETDATA_EXTENSIONS|Più valori|  
|SQL_GROUP_BY|SQL_GB_GROUP_BY_CONTAINS_SELECT|  
|SQL_IDENTIFIER_CASE|SQL_IC_UPPER (il qualificatore viene restituito in un caso misto, in modo che Windows NT possa individuare la directory).|  
|SQL_IDENTIFIER_QUOTE_CHAR|" \` " (virgoletta indietro)|  
|SQL_KEYWORDS|Più valori|  
|SQL_LIKE_ESCAPE_CLAUSE|"N"|  
|SQL_MAX_BINARY_LITERAL_LEN|255|  
|SQL_MAX_CATALOG_NAME_LEN|66|  
|SQL_MAX_CHAR_LITERAL_LEN|254|  
|SQL_MAX_COLUMN_NAME_LEN|10|  
|SQL_MAX_COLUMNS_IN_GROUP_BY|10|  
|SQL_MAX_COLUMNS_IN_INDEX|0 (limite sconosciuto o non applicabile)|  
|SQL_MAX_COLUMNS_IN_ORDER_BY|10|  
|SQL_MAX_COLUMNS_IN_SELECT|255|  
|SQL_MAX_COLUMNS_IN_TABLE|255|  
|SQL_MAX_CONCURRENT_ACTIVITIES|0|  
|SQL_MAX_CURSOR_NAME_LEN|64|  
|SQL_MAX_DRIVER_CONNECTIONS|64|  
|SQL_MAX_INDEX_SIZE|220|  
|SQL_MAX_PROCEDURE_NAME_LEN|0|  
|SQL_MAX_ROW_SIZE|4000|  
|SQL_MAX_ROW_SIZE_INCLUDES_LONG|"N"|  
|SQL_MAX_SCHEMA_NAME_LEN|0|  
|SQL_MAX_STATEMENT_LEN|65000|  
|SQL_MAX_TABLE_NAME_LEN|12|  
|SQL_MAX_TABLES_IN_SELECT|16|  
|SQL_MAX_USER_NAME_LEN|0|  
|SQL_MULT_RESULT_SETS|"N"|  
|SQL_MULTIPLE_ACTIVE_TXN|"Y"|  
|SQL_NEED_LONG_DATA_LEN|"N"|  
|SQL_NON_NULLABLE_COLUMNS|SQL_NNC_NON_NULL|  
|SQL_NULL_COLLATION|SQL_NC_LOW|  
|SQL_NUMERIC_FUNCTIONS|Più valori|  
|CONFORMITÀ SQL_ODBC_SAG_CLI_|SQL_OSCC_COMPLIANT|  
|SQL_ODBC_SQL_INTEGRITY|"N"|  
|SQL_ODBC_VER|Da Gestione driver|  
|SQL_OJ_CAPABILITIES|Più valori|  
|SQL_ORDER_BY_COLUMNS_IN_SELECT|"N"|  
|SQL_OUTER_JOINS|"Y"|  
|SQL_PROCEDURE_TERM|""|  
|SQL_PROCEDURES|"N"|  
|SQL_QUOTED_IDENTIFIER_CASE|SQL_IC_MIXED|  
|SQL_ROW_UPDATES|"N"|  
|SQL_SCHEMA_TERM|""|  
|SQL_SCHEMA_USAGE|0|  
|SQL_SCROLL_OPTIONS|Più valori|  
|SQL_SEARCH_PATTERN_ESCAPE|"\\"|  
|SQL_SERVER_NAME|DBASE|  
|SQL_SPECIAL_CHARACTERS|"~ \` \@ #$%^& \* \_ -+= \\ } {"';: \? / \><,.!' \[ ] &#124; "|  
|SQL_STRING_FUNCTIONS|Più valori|  
|SQL_SUBQUERIES|Più valori|  
|SQL_SYSTEM_FUNCTIONS|0|  
|SQL_TABLE_TERM|TABELLA|  
|SQL_TIMEDATE_ADD_INTERVALS|0|  
|SQL_TIMEDATE_DIFF_INTERVALS|0|  
|SQL_TIMEDATE_FUNCTIONS|Più valori|  
|SQL_TXN_CAPABLE|SQL_TC_NONE|  
|SQL_TXN_ISOLATION_OPTION|0|  
|SQL_UNION|Più valori|  
|SQL_USER_NAME|""|
