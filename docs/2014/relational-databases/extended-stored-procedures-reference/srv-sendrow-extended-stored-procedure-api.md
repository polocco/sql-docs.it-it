---
title: srv_sendrow (API Stored procedure estesa) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_sendrow
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_sendrow
ms.assetid: a08f608a-10e6-4bff-9b48-0d02e8026cdb
author: rothja
ms.author: jroth
ms.openlocfilehash: 35e640b00c0479d7db1d9a151aa6dcdc0eb67cc8
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050525"
---
# <a name="srv_sendrow-extended-stored-procedure-api"></a>srv_convert (API delle stored procedure estese)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Trasmette una riga di dati al client.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
int srv_sendrow ( SRV_PROC *  
srvproc   
);  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *srvproc*  
 Puntatore alla struttura SRV_PROC che rappresenta l'handle di una determinata connessione client, in questo caso l'handle che ha ricevuto la richiesta del linguaggio. La struttura contiene informazioni utilizzate dalla libreria dell'API Stored procedure estesa per gestire le comunicazioni e i dati tra l'applicazione e il client.  
  
## <a name="returns"></a>Restituisce  
 SUCCEED o FAIL.  
  
## <a name="remarks"></a>Osservazioni  
 La funzione **srv_sendrow** viene chiamata una volta per ogni riga inviata al client. Tutte le righe devono essere inviate al client prima che qualsiasi messaggio, valore di stato o stato di completamento venga inviato con **srv_sendmsg**, **srv_status** o **srv_senddone**.  
  
 L'invio di una riga le cui colonne non sono state definite tutte con **srv_describe** fa sì che l'applicazione dell'API Stored procedure estesa generi un messaggio di errore informativo e restituisca FAIL al client. In questo caso, la riga non viene inviata.  
  
> [!NOTE]  
>  L'API delle stored procedure estese non supporta l'invio di righe di calcolo al client. Se, inoltre, una riga che contiene dati `ntext`, `text` o `image` viene inviata al client, il puntatore di testo e il timestamp di testo non vengono inclusi.  
  
> [!IMPORTANT]  
>  È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Vedere anche  
 [srv_describe &#40;API Stored procedure estesa&#41;](srv-describe-extended-stored-procedure-api.md)  
  
  
