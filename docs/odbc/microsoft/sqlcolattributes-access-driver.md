---
description: SQLColAttributes (driver Access)
title: SQLColAttributes (driver Access) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColAttribute function [ODBC], Access Driver
- Access driver [ODBC], SQLColAttributes
ms.assetid: adb6f81d-e8c7-4748-9b1d-f7a053788bbc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d9758bb5c473971d3ed9acea52559da0a4aac67d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412277"
---
# <a name="sqlcolattributes-access-driver"></a>SQLColAttributes (driver Access)
> [!NOTE]  
>  In questo argomento vengono fornite informazioni specifiche del driver di accesso. Per informazioni generali su questa funzione, vedere l'argomento appropriato in informazioni di [riferimento sulle API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Attributo|Commenti|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Per i dati di LONGVARBINARY, SQL_COLUMN_DISPLAY_SIZE è la lunghezza massima della colonna, non la lunghezza massima della colonna per 2.|  
|SQL_OWNER_NAME|In questa colonna viene restituita una stringa vuota ("") perché il nome del proprietario non è supportato.|  
|SQL_QUALIFIER_NAME|Viene restituito il percorso di un file di database.|  
|SQL_COLUMN_SEARCHABLE|Le colonne LONGVARBINARY e LONGVARCHAR sono segnalate come SQL_UNSEARCHABLE.<br /><br /> I tipi di dati binary e character a lunghezza fissa e a lunghezza variabile sono disponibili per la ricerca, anche se LONGVARBINARY e LONGVARCHAR non lo sono.|  
  
> [!NOTE]  
>  Il valore precedente non è un elenco completo degli attributi restituiti da **SQLColAttributes**.
