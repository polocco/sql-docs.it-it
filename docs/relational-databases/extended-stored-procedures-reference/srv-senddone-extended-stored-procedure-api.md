---
title: srv_senddone (API Stored Procedure estesa) | Microsoft Docs
description: Informazioni su come srv_senddone nell'API stored procedure estesa Invia un messaggio di completamento del risultato al client.
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_senddone
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_senddone
ms.assetid: 1fc4f1d5-56d4-43f6-b5e4-0c0cc295cba3
author: rothja
ms.author: jroth
ms.openlocfilehash: 424ef5a1050def714e7f42483cb2c8d16ecfb99b
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248250"
---
# <a name="srv_senddone-extended-stored-procedure-api"></a>srv_senddone (API delle stored procedure estese)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Invia messaggio di completamento dei risultati al client.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
int srv_senddone (  
SRV_PROC *  
srvproc  
,  
DBUSMALLINT   
status  
,  
DBUSMALLINT  
info  
,  
DBINT  
count   
);  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *srvproc*  
 Puntatore alla struttura SRV_PROC che rappresenta l'handle di una determinata connessione client, in questo caso l'handle che ha ricevuto la richiesta del linguaggio. La struttura contiene informazioni utilizzate dalla libreria dell'API Stored procedure estesa per gestire le comunicazioni e i dati tra l'applicazione e il client.  
  
 *Stato*  
 Campo a 2 byte per vari flag di *status*. È possibile impostare più flag usando gli operatori logici AND e OR con i valori dei flag di *status*. Nella tabella seguente sono elencati i possibili flag di *status*.  
  
|Flag di stato|Descrizione|  
|-----------------|-----------------|  
|SRV_DONE_COUNT|Il parametro *count* contiene un conteggio valido.|  
|SRV_DONE_ERROR|Il comando client corrente ha ricevuto un errore.|  
  
 *informazioni*  
 Campo a 2 byte riservato. Impostare questo valore su 0.  
  
 *count*  
 Campo a 4 byte utilizzato per indicare un conteggio per il set di risultati corrente. Se il flag SRV_DONE_COUNT è impostato nel campo *status*, *count* include un conteggio valido.  
  
## <a name="returns"></a>Restituisce  
 SUCCEED o FAIL  
  
## <a name="remarks"></a>Osservazioni  
 Una richiesta del client può provocare l'esecuzione da parte del server di alcuni comandi e la restituzione di alcuni set di risultati. Per ogni set di risultati, **srv_senddone** deve restituire un messaggio di completamento dei risultati al client.  
  
 Il campo *count* indica il numero di righe interessate da un comando. Se il campo *count* contiene un conteggio, il flag SRV_DONE_COUNT deve essere impostato nel campo *status*. Questa impostazione consente al client di distinguere tra un valore di *count* pari a 0 e un campo *count* inutilizzato.  
  
 Non chiamare **srv_senddone** dal gestore SRV_CONNECT.  
  
> [!IMPORTANT]  
>  È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
