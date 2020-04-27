---
title: srv_rpcdb (API Stored procedure estesa) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_rpcdb
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcdb
ms.assetid: d52bfd22-7a7c-4ab0-af65-df96ff359e6f
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7eb462881ab9ae5d6221498a84fc2b79e0524bc9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "63046656"
---
# <a name="srv_rpcdb-extended-stored-procedure-api"></a>srv_rpcdb (API delle stored procedure estese)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Restituisce il componente del nome del database per la stored procedure remota corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DBCHAR * srv_rpcdb (  
SRV_PROC * srvproc,int *len );  
```  
  
## <a name="arguments"></a>Argomenti  
 *srvproc*  
 Puntatore alla struttura SRV_PROC che rappresenta l'handle di una determinata connessione client. La struttura contiene informazioni utilizzate dalla libreria dell'API Stored procedure estesa per gestire le comunicazioni e i dati tra l'applicazione e il client.  
  
 *Len*  
 Puntatore a una variabile `int` che riceve la lunghezza del nome del database. Se *len* è NULL, la lunghezza del nome del database non viene restituita.  
  
## <a name="returns"></a>Valori di codice restituiti  
 Puntatore DBCHAR alla stringa con terminazione Null per la parte del nome del database della stored procedure remota corrente. Se non è presente alcuna stored procedure remota corrente, viene restituito NULL e il parametro *len* viene impostato su -1.  
  
## <a name="remarks"></a>Osservazioni  
 Questa funzione restituisce solo il componente del database del nome dell'oggetto stored procedure remota. Non include gli identificatori facoltativi per il proprietario, il nome della stored procedure remota e il numero della stored procedure remota.  
  
> [!IMPORTANT]  
>  È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
