---
description: SET NULL (comando)
title: Comando SET NULL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set nullSET NULL
ms.assetid: 410c5a6e-e957-4ecc-9e2d-e591cbc0bc4f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5e98037838325a0bfe56b51cdcfec7df8539facd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421845"
---
# <a name="set-null-command"></a>SET NULL (comando)
Determina il modo in cui i valori null sono supportati dai comandi ALTER TABLE-SQL, CREATE TABLE-SQL e INSERT-SQL.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET NULL ON | OFF  
```  
  
## <a name="arguments"></a>Argomenti  
 ON  
 (Impostazione predefinita per il driver; l'impostazione predefinita per Visual FoxPro è OFF). Specifica che tutte le colonne di una tabella creata con ALTER TABLE e CREATE TABLE consentiranno valori null. È possibile eseguire l'override del supporto di valori null per le colonne nella tabella includendo la clausola NOT NULL nelle definizioni delle colonne.  
  
 Specifica inoltre che INSERT-SQL inserisce valori null in tutte le colonne non incluse nella clausola INSERT-SQL VALUE. INSERT-SQL inserisce i valori null solo nelle colonne che consentono valori null.  
  
 OFF  
 Specifica che tutte le colonne di una tabella creata con ALTER TABLE e CREATE TABLE non consentiranno valori null. È possibile designare il supporto di valori null per le colonne in ALTER TABLE e CREATE TABLE includendo la clausola NULL nelle definizioni delle colonne.  
  
 Specifica inoltre che INSERT-SQL inserisce i valori vuoti in tutte le colonne non incluse nella clausola INSERT-SQL VALUE.  
  
## <a name="remarks"></a>Osservazioni  
 SET NULL interessa solo il modo in cui i valori null sono supportati da ALTER TABLE, CREATE TABLE e INSERT-SQL. Gli altri comandi non sono interessati dal SET NULL.  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER TABLE-comando SQL](../../odbc/microsoft/alter-table-sql-command.md)   
 [Comando CREATE TABLE-SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [INSERT (comando SQL)](../../odbc/microsoft/insert-sql-command.md)
