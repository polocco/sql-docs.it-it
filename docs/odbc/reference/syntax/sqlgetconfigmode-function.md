---
title: Funzione SQLGetConfigMode | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetConfigMode
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConfigMode
helpviewer_keywords:
- SQLGetConfigMode function [ODBC]
ms.assetid: b96ab3b8-08d5-4fea-9ffe-e03043efbf2d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cc11bec24ede3352dd43f3645fb8c720b77fdabe
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "81285691"
---
# <a name="sqlgetconfigmode-function"></a>Funzione SQLGetConfigMode
**Conformità**  
 Versione introdotta: ODBC 3,0  
  
 **Riepilogo**  
 **SQLGetConfigMode** recupera la modalità di configurazione che indica il punto in cui la voce ODBC. ini che elenca i valori DSN è presente nelle informazioni di sistema.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
  
BOOL SQLGetConfigMode(  
     UWORD *   pwConfigMode);  
```  
  
## <a name="arguments"></a>Argomenti  
 *pwConfigMode*  
 Output Puntatore al buffer che contiene la modalità di configurazione. (Vedere "Commenti"). Il valore in * \*pwConfigMode* può essere:  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di esito negativo.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLGetConfigMode** restituisce false, è possibile ottenere un valore * \*pfErrorCode* associato chiamando **SQLInstallerError**. La tabella seguente elenca i * \*valori pfErrorCode* che possono essere restituiti da **SQLInstallerError** e ne illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Descrizione|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione non è riuscito a eseguire la funzione a causa di memoria insufficiente.|  
  
## <a name="comments"></a>Commenti  
 Questa funzione viene utilizzata per determinare la posizione in cui la voce ODBC. ini che elenca i valori DSN è presente nelle informazioni di sistema. Se * \*pwConfigMode* è ODBC_USER_DSN, il DSN è un DSN utente e la funzione legge dalla voce ODBC. ini nel HKEY_CURRENT_USER. Se è ODBC_SYSTEM_DSN, il DSN è un DSN di sistema e la funzione legge dalla voce ODBC. ini nel HKEY_LOCAL_MACHINE. Se è ODBC_BOTH_DSN, viene eseguito un tentativo HKEY_CURRENT_USER e, in caso di errore, viene usato HKEY_LOCAL_MACHINE.  
  
 Per impostazione predefinita, **SQLGetConfigMode** restituisce ODBC_BOTH_DSN. Quando viene creato un DSN utente o un DSN di sistema tramite una chiamata a **SQLConfigDataSource**, la funzione imposta la modalità di configurazione su ODBC_USER_DSN o ODBC_SYSTEM_DSN per distinguere i DSN utente e di sistema durante la modifica di un DSN. Prima di restituire, **SQLConfigDataSource** Reimposta la modalità di configurazione su ODBC_BOTH_DSN.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Impostazione della modalità di configurazione|[SQLSetConfigMode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|
