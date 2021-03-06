---
description: Mapping di SQLAllocEnv
title: Mapping di SQLAllocEnv | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocEnv
ms.assetid: 4bb51845-ee91-4b97-9dd4-2fab977f2aec
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5783eaa717b5716dd6021f34b7a904ba3994759d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429513"
---
# <a name="sqlallocenv-mapping"></a>Mapping di SQLAllocEnv
Quando un'applicazione chiama **SQLAllocEnv** tramite un driver ODBC *3. x* , viene eseguito il mapping della chiamata a **SQLAllocEnv**(*phenv*) a **SQLAllocHandle** nel modo seguente:  
  
1.  Gestione driver alloca un handle di ambiente e lo restituisce all'applicazione. Gestione driver chiama **SQLSetEnvAttr** per impostare l'attributo dell'ambiente SQL_ATTR_ODBC_VERSION su SQL_OV_ODBC2.  
  
2.  Quando l'applicazione stabilisce la prima connessione a un driver, gestione driver chiama  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     nel driver con *OutputHandlePtr* impostato su *phenv*.
