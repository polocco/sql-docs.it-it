---
description: Funzione SQLSetConnectOption
title: Funzione SQLSetConnectOption | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetConnectOption
helpviewer_keywords:
- SQLSetConnectOption function [ODBC]
ms.assetid: 8cd2c2a2-25c8-4aff-951c-b593bbfc90ad
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ebe9166ea52971812e8905399da4ea0e6347361a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499533"
---
# <a name="sqlsetconnectoption-function"></a>Funzione SQLSetConnectOption
**Conformità**  
 Versione introdotta: conformità agli standard ODBC 1,0: deprecato  
  
 **Summary**  
 In ODBC 3 *. x*, la funzione ODBC 2,0 **SQLSetConnectOption** è stata sostituita da **SQLSetConnectAttr**. Per altre informazioni, vedere [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
> [!NOTE]
>  Per ulteriori informazioni su ciò che Gestione driver esegue il mapping di questa funzione a quando un'applicazione ODBC 2 *. x* utilizza un driver ODBC 3 *. x* , vedere [mapping di funzioni deprecate](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)".  
  
## <a name="remarks"></a>Osservazioni  
 Vedere [informazioni su ODBC 64 bit](../../../odbc/reference/odbc-64-bit-information.md), se l'applicazione viene eseguita su un sistema operativo a 64 bit.  
  
> [!NOTE]  
>  L'attributo SQL_ASYNC_DBC_FUNCTION_ENABLE introdotto in ODBC 3,8 non è supportato da **SQLSetConnectOption**. Le applicazioni che utilizzano l'operazione asincrona sull'handle di connessione devono utilizzare **SQLSetConnectAttr**.  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento sulle API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [File di intestazione ODBC](../../../odbc/reference/install/odbc-header-files.md)
