---
title: DLL di installazione driver | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC], driver setup DLL
- ODBC drivers [ODBC], driver setup DLL
- driver setup DLL [ODBC]
ms.assetid: 49bab021-81fa-402e-b7a4-a5214f1fadc4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a0a2878591c92fe0b2070a295d9dc622c245c17e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306422"
---
# <a name="driver-setup-dll"></a>DLL di installazione driver
> [!NOTE]  
>  A partire da Windows XP e Windows Server 2003, ODBC è incluso nel sistema operativo Windows. È consigliabile installare solo in modo esplicito ODBC nelle versioni precedenti di Windows.  
  
 La DLL di installazione del driver contiene le funzioni **ConfigDriver** e **ConfigDSN** . **ConfigDriver** esegue attività di installazione specifiche del driver, ad esempio l'immissione di informazioni specifiche del driver nel registro di sistema. **ConfigDSN** mantiene le informazioni specifiche del driver sulle origini dati nel registro di sistema. Per una descrizione completa di queste funzioni, vedere informazioni di [riferimento sull'API DLL di installazione](../../../odbc/reference/syntax/setup-dll-api-reference.md).  
  
 **ConfigDSN** chiama le funzioni seguenti nella dll del programma di installazione per mantenere le informazioni sull'origine dati nel registro di sistema:  
  
-   **SQLWriteDSNToIni**. Aggiungere un'origine dati.  
  
-   **SQLRemoveDSNFromIni**. Eliminare un'origine dati.  
  
-   **SQLWritePrivateProfileString**. Scrivere un valore specifico del driver in una sottochiave specifica dell'origine dati.  
  
-   **SQLGetPrivateProfileString**. Leggere un valore specifico del driver da una sottochiave specifica dell'origine dati.  
  
-   **SQLGetTranslator**. Chiedere all'utente di specificare un nome e un'opzione per il traduttore. Questa funzione chiama **ConfigTranslator** nella DLL di installazione del traduttore.  
  
 La DLL di installazione del driver viene scritta dallo sviluppatore del driver. Può far parte della DLL del driver o di una DLL separata.
