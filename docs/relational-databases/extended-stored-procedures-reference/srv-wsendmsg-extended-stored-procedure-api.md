---
title: srv_wsendmsg (API Stored procedure estesa) | Microsoft Docs
description: Informazioni su come srv_wsendmsg nell'API stored procedure estesa può inviare un messaggio Unicode al client.
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_wsendmsg
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_wsendmsg
ms.assetid: f2153076-32c9-4a52-8e1b-fc9618153543
author: rothja
ms.author: jroth
ms.openlocfilehash: 0256a21d4d64df710a4720797297293cbf8a9c0e
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248203"
---
# <a name="srv_wsendmsg-extended-stored-procedure-api"></a>srv_wsendmsg (API Stored procedure estesa)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Invia un messaggio Unicode al client.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
int srv_wsendmsg(SRV_PROC *   
srvproc  
, int   
msgnum  
, int   
severity  
, WCHAR *   
message  
, int   
msglen  
);  
```  
  
## <a name="arguments"></a>Argomenti  
 *srvproc*  
 Puntatore alla struttura SRV_PROC che rappresenta l'handle di una determinata connessione client. La struttura contiene informazioni utilizzate dalla libreria dell'API Stored procedure estesa per gestire le comunicazioni e i dati tra l'applicazione e il client.  
  
 *Msgnum*  
 Numero di messaggio a 4 byte.  
  
 *Gravità*  
 Specifica la gravità dell'errore. Un livello di gravità minore o uguale a 10 è considerato un messaggio informativo; in caso contrario, è un errore.  
  
 *message*  
 Puntatore alla stringa Unicode da inviare al client.  
  
 *msglen*  
 Specifica la lunghezza, espressa in caratteri, di *message*.  
  
## <a name="returns"></a>Restituisce  
 SUCCEED o FAIL.  
  
## <a name="remarks"></a>Commenti  
 Utilizzare questa funzione per inviare messaggi in Unicode. È simile a **srv_sendmsg**, ma il messaggio che invia è una stringa WCHAR anziché una stringa di tipo DBCHAR. Notare che la lunghezza del messaggio viene riportata in caratteri anziché in byte e che *msglen* non sarà mai uguale a SRV_NULLTERM.  
  
 La funzione restituisce FAIL quando:  
  
-   Il valore *msglen* specificato non è incluso nell'intervallo 0-32242.  
  
-   Il valore *msglen* specificato è 0 ma il puntatore del messaggio è NULL.  
  
-   Si verifica un errore durante l'invio del messaggio di errore tramite rete.  
  
> [!IMPORTANT]  
>  È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Vedere anche  
 [srv_sendmsg &#40;API Stored procedure estesa&#41;](../../relational-databases/extended-stored-procedures-reference/srv-sendmsg-extended-stored-procedure-api.md)  
  
  
