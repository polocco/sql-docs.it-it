---
description: Posizionamento nei recordset
title: Posizionamento del recordset | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- record positioning [ADO]
- Recordset object [ADO]
- repositioning record [ADO]
- AbsolutePosition property [ADO]
ms.assetid: c8f6fbcb-6675-4133-b37e-430de43949c1
author: rothja
ms.author: jroth
ms.openlocfilehash: 1f97f5b9c9a947362edffaa88f878c96d63b270f
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88979882"
---
# <a name="recordset-positioning"></a>Posizionamento nei recordset
Utilizzare la proprietà **AbsolutePosition** per spostarsi in un record, in base alla relativa posizione ordinale nell'oggetto **Recordset** , oppure per determinare la posizione ordinale del record corrente. Il provider deve supportare la funzionalità appropriata affinché questa proprietà sia disponibile.  
  
 **AbsolutePosition** è in base 1 e è uguale a 1 quando il record corrente è il primo record nel **Recordset**. Come indicato in precedenza, è possibile ottenere il numero totale di record nell'oggetto **Recordset** dalla proprietà **RecordCount** .  
  
 Quando si imposta la proprietà **AbsolutePosition** , anche se si tratta di un record nella cache corrente, ADO ricarica la cache con un nuovo gruppo di record a partire dal record specificato. La proprietà **CacheSize** determina le dimensioni di questo gruppo.  
  
> [!NOTE]
>  Non usare la proprietà **AbsolutePosition** come numero di record surrogato. La posizione di un determinato record viene modificata quando si elimina un record precedente. Non esiste inoltre alcuna garanzia che un determinato record avrà lo stesso **AbsolutePosition** se l'oggetto **Recordset** viene nuovamente sottoposto a query o riaperto. I segnalibri rappresentano il metodo consigliato per mantenere e tornare a una posizione specificata e sono l'unico modo per posizionare tutti i tipi di oggetti **Recordset** .
