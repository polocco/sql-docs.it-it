---
description: SET PATH (comando)
title: Comando SET PATH | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET PATH command [ODBC]
ms.assetid: db488d1e-0963-4f45-8c76-a23b9bde9e9d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 36131e53d1a10d8af3e7ca226768a9c08a14ba77
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421835"
---
# <a name="set-path-command"></a>SET PATH (comando)
Specifica un percorso per le ricerche di file. Per informazioni specifiche del driver, vedere la sezione Osservazioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET PATH TO [Path]  
```  
  
## <a name="arguments"></a>Argomenti  
 A [ *percorso*]  
 Specifica le directory in cui si vuole eseguire la ricerca in Visual FoxPro. Usare virgole o punti e virgola per separare le directory.  
  
## <a name="remarks"></a>Osservazioni  
 SET PATH consente di specificare i percorsi di ricerca per altri programmi Visual FoxPro che possono essere chiamati all'interno delle stored procedure. SET PATH non modificherà il percorso dell'origine dati specificata per la connessione.  
  
 Problema impostare percorso su senza *percorso* per ripristinare il percorso della directory o della cartella predefinita.  
  
## <a name="driver-remarks"></a>Osservazioni del driver  
 Se si rilascia il percorso SET in una stored procedure, questo verrà ignorato dalle funzioni e dai comandi seguenti:  
  
-   Le funzioni di catalogo come [SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md) e [SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md) ignoreranno il nuovo percorso e continueranno a fare riferimento al percorso specificato dall'origine dati in [SQLPrepare](../../odbc/microsoft/sqlprepare-visual-foxpro-odbc-driver.md) o [SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md).  
  
-   I comandi come SELECT, INSERT, UPDATE, DELETE e CREATE TABLE ignoreranno il nuovo percorso e continueranno a fare riferimento al percorso specificato dall'origine dati in **SQLPrepare** o **SQLExecDirect**.  
  
 Se si esegue SET PATH in una stored procedure e non si imposta successivamente il percorso sullo stato originale, altre connessioni al database utilizzeranno il nuovo percorso, perché SET PATH non è limitato alle sessioni di dati.  
  
 Se si desidera creare, selezionare o aggiornare le tabelle in una directory diversa da quella specificata dall'origine dati, specificare il percorso completo del file con il comando.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestra di dialogo di installazione di Visual FoxPro ODBC](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)   
 [SQLColumns (driver ODBC Visual FoxPro)](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md)   
 [SQLDriverConnect (driver ODBC Visual FoxPro)](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)   
 [SQLTables (driver ODBC Visual FoxPro)](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)
