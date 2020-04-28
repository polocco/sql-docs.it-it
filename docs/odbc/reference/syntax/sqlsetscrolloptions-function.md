---
title: Funzione SQLSetScrollOptions | Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetScrollOptions
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLSetScrollOptions
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC]
ms.assetid: 2a825ba7-7942-4c23-bcdb-c80dc12f8c86
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 056fc203581e1d5d8323b09ac62d692093d8c0f5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "81287268"
---
# <a name="sqlsetscrolloptions-function"></a>Funzione SQLSetScrollOptions
**Conformità**  
 Versione introdotta: conformità agli standard ODBC 1,0: deprecato  
  
 **Riepilogo**  
 In ODBC *3. x*, la funzione ODBC 2,0 **SQLSetScrollOptions** è stata sostituita dalle chiamate a **SQLGetInfo** e **SQLSetStmtAttr**.  
  
> [!NOTE]
>  Per ulteriori informazioni su ciò che Gestione driver esegue il mapping di questa funzione a quando un'applicazione ODBC *2. x* utilizza un driver ODBC *3. x* , vedere [mapping di funzioni deprecate](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) in Appendice G: linee guida per la compatibilità con le versioni precedenti.  
> 
> [!NOTE]
>  Quando Gestione driver esegue il mapping di **SQLSetScrollOptions** per un'applicazione che utilizza un driver ODBC *3. x* che non **supporta SQLSetScrollOptions**, gestione driver imposta l'opzione dell'istruzione SQL_ROWSET_SIZE, non l'attributo dell'istruzione SQL_ATTR_ROW_ARRAY_SIZE, sull'argomento *RowsetSize* in **SQLSetScrollOption**. Di conseguenza, **SQLSetScrollOptions** non può essere utilizzato da un'applicazione durante il recupero di più righe mediante una chiamata a **SQLFetch** o **SQLFetchScroll**. Può essere utilizzato solo quando si recuperano più righe tramite una chiamata a **SQLExtendedFetch**.  
  
## <a name="remarks"></a>Osservazioni  
 Se l'applicazione viene eseguita su un sistema operativo a 64 bit, vedere [informazioni su ODBC 64-bit](../../../odbc/reference/odbc-64-bit-information.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento sulle API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
