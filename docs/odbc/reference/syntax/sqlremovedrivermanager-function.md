---
title: Funzione SQLRemoveDriverManager | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRemoveDriverManager
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDriverManager
helpviewer_keywords:
- SQLRemoveDriverManager function function [ODBC]
ms.assetid: 3a41511f-6603-4b81-a815-7883874023c4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 27b32c1c4e0f3f4d5359af287ba07d40b033af00
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301812"
---
# <a name="sqlremovedrivermanager-function"></a>Funzione SQLRemoveDriverManager
**Conformità**  
 Versione introdotta: ODBC 3,0: deprecato in Windows XP Service Pack 2, Windows Server 2003 Service Pack 1 e sistemi operativi successivi.  
  
 **Riepilogo**  
 **SQLRemoveDriverManager** modifica o rimuove le informazioni sui componenti di base di ODBC dalla voce Odbcinst. ini nelle informazioni di sistema.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
  
BOOL SQLRemoveDriverManager(  
     LPDWORD     pdwUsageCount);  
```  
  
## <a name="arguments"></a>Argomenti  
 *pdwUsageCount*  
 Output Conteggio di utilizzo di gestione driver dopo la chiamata a questa funzione.  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di esito negativo. Se nelle informazioni di sistema non è presente alcuna voce quando viene chiamata questa funzione, la funzione restituisce FALSE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLRemoveDriverManager** restituisce false, è possibile ottenere un valore * \*pfErrorCode* associato chiamando **SQLInstallerError**. La tabella seguente elenca i * \*valori pfErrorCode* che possono essere restituiti da **SQLInstallerError** e ne illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Descrizione|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore generale del programma di installazione|Si è verificato un errore per il quale non è stato specificato alcun errore di programma di installazione.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Componente non trovato nel registro di sistema|Il programma di installazione non è riuscito a rimuovere le informazioni di gestione driver perché non esisteva nel registro di sistema o non è stato trovato nel registro di sistema.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Non è stato possibile incrementare o decrementare il numero di utilizzi dei componenti|Il programma di installazione non è riuscito a decrementare il conteggio di utilizzo di gestione driver.|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione non è riuscito a eseguire la funzione a causa di memoria insufficiente.|  
  
## <a name="comments"></a>Commenti  
 **SQLRemoveDriverManager** completa la funzione **SQLInstallDriverManager** e aggiorna il conteggio di utilizzo dei componenti nelle informazioni di sistema. Questa funzione deve essere chiamata solo da un'applicazione di installazione.  
  
 **SQLRemoveDriverManager** decrementerà di 1 il numero di utilizzo dei componenti di base. Se il conteggio utilizzo componenti passa a 0, le informazioni sul sistema di immissione verranno rimosse. La voce del componente principale si trova nel percorso seguente nelle informazioni di sistema, sotto il titolo "ODBC core":  
  
 `HKEY_LOCAL_MACHINE`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbcinst.ini`  
  
> [!CAUTION]  
>  Un'applicazione non deve rimuovere fisicamente i file di gestione driver quando il conteggio utilizzo componenti e il conteggio utilizzo file raggiungono lo zero.  
  
 **SQLRemoveDriverManager** non rimuove effettivamente alcun file. Il programma chiamante è responsabile dell'eliminazione dei file e della gestione dei conteggi di utilizzo del file. Tuttavia, i file di gestione driver non devono essere rimossi quando il conteggio di utilizzo del componente e il conteggio di utilizzo file hanno raggiunto zero, perché questi file possono essere utilizzati da altre applicazioni che non hanno incrementato il numero di utilizzo del file.  
  
 **SQLRemoveDriverManager** viene chiamata come parte del processo di disinstallazione. I componenti di base di ODBC (che includono Gestione driver, la libreria di cursori, il programma di installazione, la libreria di lingue, l'amministratore, i file di thunk e così via) vengono completamente disinstallati. I file seguenti non vengono rimossi quando **SQLRemoveDriverManager** viene chiamato come parte del processo di disinstallazione:  
  
|||  
|-|-|  
|ODBC32DLL|Odbccp32. DLL|  
|Odbccr32. DLL|Odbc16gt. DLL|  
|ODBCCU32. DLL|ODBC32GT. DLL|  
|ODBCINT. DLL|DS16GT. DLL|  
|ODBCTRAC. DLL|DS32GT. DLL|  
|MSVCRT40. DLL|Odbcad32. EXE|  
|Odbccp32. CPL||  
  
 **SQLRemoveDriverManager** viene chiamato anche come parte di un processo di aggiornamento. Se un'applicazione rileva che è necessario eseguire un aggiornamento e in precedenza ha installato il driver, il driver deve essere rimosso e quindi reinstallato.  
  
 **SQLRemoveDriverManager** deve essere chiamato prima per decrementare il numero di utilizzo dei componenti. **SQLInstallDriverEx** deve quindi essere chiamato per incrementare il conteggio di utilizzo dei componenti. Il programma di installazione dell'applicazione deve sostituire i vecchi file dei componenti di base con i nuovi file. I conteggi di utilizzo dei file rimarranno invariati e altre applicazioni che utilizzano i file dei componenti di base della versione precedente utilizzeranno ora i file di versione più recenti.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Installazione di una gestione driver|[SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|
