---
description: SQL dinamica
title: SQL dinamico | Microsoft Docs
ms.custom: ''
ms.date: 06/03/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], dynamic SQL
- SQL statements [ODBC], embedded SQL
- dynamic SQL [ODBC]
- SQL [ODBC], dynamic SQL
- embedded SQL [ODBC]
ms.assetid: 0bfb9ab7-9c15-4433-93bc-bad8b6c9d287
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: de711543748a91015a9aa0d4cb8aadb011744306
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494582"
---
# <a name="dynamic-sql"></a>SQL dinamica
Sebbene SQL statico funzioni correttamente in molte situazioni, esiste una classe di applicazioni in cui non è possibile determinare in anticipo l'accesso ai dati. Si supponga, ad esempio, che un foglio di calcolo consenta a un utente di immettere una query, che il foglio di calcolo invia quindi al sistema DBMS per recuperare i dati. Il contenuto di questa query, ovviamente, non può essere noto al programmatore quando viene scritto il programma di foglio di calcolo.  
  
 Per risolvere questo problema, il foglio di calcolo utilizza un modulo di SQL incorporato denominato SQL dinamico. Diversamente dalle istruzioni SQL statiche, che sono hardcoded nel programma, le istruzioni SQL dinamiche possono essere compilate in fase di esecuzione e inserite in una variabile host stringa. Vengono quindi inviati al sistema DBMS per l'elaborazione. Poiché il sistema DBMS deve generare un piano di accesso in fase di esecuzione per le istruzioni SQL dinamiche, SQL dinamico è in genere più lento rispetto a SQL statico. Quando viene compilato un programma contenente istruzioni SQL dinamiche, le istruzioni SQL dinamiche non vengono rimosse dal programma, come in SQL statico. Vengono invece sostituiti da una chiamata di funzione che passa l'istruzione al sistema DBMS. le istruzioni SQL statiche nello stesso programma vengono gestite normalmente.  
  
 Il modo più semplice per eseguire un'istruzione SQL dinamica è con un'istruzione EXECUTE IMMEDIATE. Questa istruzione passa l'istruzione SQL al sistema DBMS per la compilazione e l'esecuzione.  
  
 Uno svantaggio dell'istruzione EXECUTE IMMEDIATE è che il sistema DBMS deve superare ognuno dei cinque passaggi dell'elaborazione di un'istruzione SQL ogni volta che viene eseguita l'istruzione. Il sovraccarico causato da questo processo può essere significativo se molte istruzioni vengono eseguite in modo dinamico ed è inutile se tali istruzioni sono simili. Per risolvere questo problema, SQL dinamico offre una forma ottimizzata di esecuzione denominata esecuzione preparata, che usa i passaggi seguenti:  
  
1.  Il programma crea un'istruzione SQL in un buffer, così come avviene per l'istruzione EXECUTE IMMEDIATE. Anziché le variabili host, un punto interrogativo (?) può essere sostituito da una costante in un punto qualsiasi del testo dell'istruzione per indicare che un valore per la costante verrà fornito in un secondo momento. Il punto interrogativo viene chiamato indicatore di parametro.  
  
2.  Il programma passa l'istruzione SQL al sistema DBMS con un'istruzione Prep, che richiede che il sistema DBMS analizzi, convalidi e ottimizzi l'istruzione e generi un piano di esecuzione. Il programma usa quindi un'istruzione EXECUTE (non un'istruzione EXECUTE IMMEDIATE) per eseguire l'istruzione prepare in un secondo momento. Passa i valori dei parametri per l'istruzione tramite una struttura di dati speciale denominata area dati SQL o SQLDA.  
  
3.  Il programma può utilizzare ripetutamente l'istruzione EXECUTE, specificando valori di parametro diversi ogni volta che viene eseguita l'istruzione dinamica.  
  
 L'esecuzione preparata non è ancora identica a SQL statico. In SQL statico, i primi quattro passaggi per l'elaborazione di un'istruzione SQL si verificano in fase di compilazione. Nell'esecuzione preparata, questi passaggi vengono eseguiti in fase di esecuzione, ma vengono eseguiti solo una volta. l'esecuzione del piano si verifica solo quando viene chiamato EXECUTE. Questo consente di eliminare alcuni svantaggi delle prestazioni inerenti all'architettura di SQL dinamico.
