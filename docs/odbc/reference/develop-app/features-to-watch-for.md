---
title: Funzionalità da controllare | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], writing interoperable applications
ms.assetid: 0fb1693b-11c3-43b1-bb16-c3323b7b2d45
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 10fa5df8a47837e92d4215f558d52711a0df3440
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305682"
---
# <a name="features-to-watch-for"></a>Funzionalità da controllare
Questa sezione descrive una serie di funzionalità che gli sviluppatori di applicazioni spesso accettano per scontate. In realtà, queste funzionalità variano notevolmente in termini di supporto e modalità di supporto tra DBMS. è probabile che non si verifichino errori di codice per questi problemi nelle applicazioni interoperative.  
  
 In questa sezione non sono elencate tutte le funzionalità che gli sviluppatori di applicazioni devono prendere in considerazione. Per informazioni, vedere le descrizioni delle funzioni [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md), [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)e [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) , [Appendice C: grammatica SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)e le sezioni di questo manuale che illustrano ciascuna funzionalità.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Numero di versione](../../../odbc/reference/develop-app/version-number.md)  
  
-   [Istruzioni e connessioni attive multiple](../../../odbc/reference/develop-app/multiple-active-statements-and-connections.md)  
  
-   [Supporto delle transazioni in DBMS](../../../odbc/reference/develop-app/transaction-support-in-dbmss.md)  
  
-   [Commit e comportamento di rollback](../../../odbc/reference/develop-app/commit-and-rollback-behavior.md)  
  
-   [Istruzioni NOT NULL in CREATE TABLE](../../../odbc/reference/develop-app/not-null-in-create-table-statements.md)  
  
-   [Tipi di dati supportati](../../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md)  
  
-   [Grammatica SQL ODBC](../../../odbc/reference/develop-app/odbc-sql-grammar.md)  
  
-   [Elaborazione batch](../../../odbc/reference/develop-app/batch-processing.md)
