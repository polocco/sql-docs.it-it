---
title: Uso di CacheSize | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- locks [ADO], CacheSize property
- CacheSize property [ADO]
ms.assetid: ca1c3422-b6a4-4ba6-af55-54f975b698b1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a2e3a67e9ad0f1f26f804ecb38e960041863fad9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "67923570"
---
# <a name="using-cachesize"></a>Uso di CacheSize
Utilizzare la proprietà **CacheSize** per controllare il numero di record da recuperare contemporaneamente nella memoria locale del provider. Se, ad esempio, **CacheSize** è 10, dopo la prima apertura dell'oggetto **Recordset** , il provider recupera i primi 10 record nella memoria locale. Quando si sposta l'oggetto **Recordset** , il provider restituisce i dati dal buffer di memoria locale. Non appena si passa oltre l'ultimo record nella cache, il provider recupera i 10 record successivi dall'origine dati nella cache.  
  
> [!NOTE]
>  **CacheSize** è basato sulla proprietà massima specifica del provider di **righe aperte** (nella raccolta **Properties** dell'oggetto **Recordset** ). Non è possibile impostare **CacheSize** su un valore maggiore del **numero massimo di righe aperte.** Per modificare il numero di righe che possono essere aperte dal provider, impostare il numero **massimo di righe aperte**.  
  
 Il valore di **CacheSize** può essere regolato durante il ciclo di vita dell'oggetto **Recordset** , ma la modifica di questo valore influisca solo sul numero di record nella cache dopo i successivi recuperi dall'origine dati. La modifica del valore della proprietà da solo non comporterà la modifica del contenuto corrente della cache.  
  
 Se il numero di record da recuperare è inferiore a quello specificato da **CacheSize** , il provider restituisce i record rimanenti e non si verifica alcun errore.  
  
 Un'impostazione **CacheSize** pari a zero non è consentita e restituisce un errore.  
  
 I record recuperati dalla cache non riflettono le modifiche simultanee apportate da altri utenti ai dati di origine. Per forzare un aggiornamento di tutti i dati memorizzati nella cache, usare il metodo [Resync](../../../ado/reference/ado-api/resync-method.md) .  
  
 Se **CacheSize** è impostato su un valore maggiore di 1, i metodi di navigazione ([Move](../../../ado/reference/ado-api/move-method-ado.md), [MoveFirst, MoveLast, MoveNext e MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)) possono comportare la navigazione a un record eliminato, se l'eliminazione viene eseguita dopo il recupero dei record. Dopo il recupero iniziale, le eliminazioni successive non verranno riflesse nella cache dei dati fino a quando non si tenta di accedere a un valore di dati da una riga eliminata. Tuttavia, se si imposta **CacheSize** su 1, questo problema viene eliminato perché non è possibile recuperare le righe eliminate.
