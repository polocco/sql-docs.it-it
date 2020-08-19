---
description: Mapping di SQLGetConnectOption
title: Mapping di SQLGetConnectOption | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLGetConnectOption
- SQLGetConnectOption function [ODBC], mapping
ms.assetid: e3792fe4-a955-473a-a297-c1b2403660c4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fbb8578b881e8eb04ef3b699fa7030e4670fab4d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421475"
---
# <a name="sqlgetconnectoption-mapping"></a>Mapping di SQLGetConnectOption
Quando un'applicazione chiama **SQLGetConnectOption** tramite un driver ODBC *3. x* , la chiamata a  
  
```  
SQLGetConnectOption(hdbc, fOption, pvParam)   
```  
  
 viene mappato come segue:  
  
-   Se *fOption* indica un'opzione di connessione definita da ODBC che restituisce una stringa, gestione driver chiama  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   Se *fOption* indica un'opzione di connessione definita da ODBC che restituisce un valore integer a 32 bit, gestione driver chiama  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   Se *fOption* indica un'opzione di istruzione definita dal driver, gestione driver chiama  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 Nei tre casi precedenti, l'argomento *connectionHandle* è impostato sul valore in *HDBC*, l'argomento *attribute* è impostato sul valore in *fOption*e l'argomento *ValuePtr* è impostato sullo stesso valore di *pvParam*.  
  
 Per le opzioni di connessione stringa definite da ODBC, gestione driver imposta l'argomento *bufferLength* nella chiamata a **SQLGetConnectAttr** sulla lunghezza massima predefinita (SQL_MAX_OPTION_STRING_LENGTH); per un'opzione di connessione non stringa, *bufferLength* è impostato su 0.  
  
 Per un driver ODBC *3. x* , gestione driver non verifica più se l' *opzione* è compresa tra SQL_CONN_OPT_MIN e SQL_CONN_OPT_MAX oppure è maggiore di SQL_CONNECT_OPT_DRVR_START. Il driver deve controllare la validità dei valori delle opzioni.
