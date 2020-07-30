---
title: Guida di riferimento per i programmatori delle stored procedure estese | Microsoft Docs
description: Informazioni sul modo in cui le stored procedure estese motore di database forniscono un'API (Application Programming Interface) basata su server per l'espansione delle funzionalità di SQL Server.
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], listed
ms.assetid: 4e9d0374-0927-4f17-bab9-2215b1b8fea8
author: rothja
ms.author: jroth
ms.openlocfilehash: a2830f920078a4e625e9ccf0fc13f376b3fd4107
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/28/2020
ms.locfileid: "87244016"
---
# <a name="database-engine-extended-stored-procedures---reference"></a>Stored procedure estese del motore di database - Informazioni di riferimento
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 L' [!INCLUDE[msCoName](../../includes/msconame-md.md)] API stored procedure estesa, inclusa in precedenza in Open Data Services, fornisce un'Application Programming Interface basata su server (API) per l'estensione della [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] funzionalità. L'API è costituita dalle macro e dalle funzioni C e C++ utilizzate per compilare applicazioni.  
  
 Con la comparsa delle più recenti e avanzate tecnologie, ad esempio l'integrazione con CLR, la necessità di ricorrere alle stored procedure estese è stata ampiamente soppiantata.  
  
> [!IMPORTANT]  
>  È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
:::row:::
    :::column:::
        [Tipi di dati](../../relational-databases/extended-stored-procedures-reference/data-types-extended-stored-procedure-api.md)
    :::column-end:::
    :::column:::
        [srv_pfield](../../relational-databases/extended-stored-procedures-reference/srv-pfield-extended-stored-procedure-api.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [srv_alloc](../../relational-databases/extended-stored-procedures-reference/srv-alloc-extended-stored-procedure-api.md)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [srv_convert](../../relational-databases/extended-stored-procedures-reference/srv-convert-extended-stored-procedure-api.md)
    :::column-end:::
    :::column:::
        [srv_pfieldex](../../relational-databases/extended-stored-procedures-reference/srv-pfieldex-extended-stored-procedure-api.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [srv_describe](../../relational-databases/extended-stored-procedures-reference/srv-describe-extended-stored-procedure-api.md)
    :::column-end:::
    :::column:::
        [srv_rpcdb](../../relational-databases/extended-stored-procedures-reference/srv-rpcdb-extended-stored-procedure-api.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [srv_getbindtoken](../../relational-databases/extended-stored-procedures-reference/srv-getbindtoken-extended-stored-procedure-api.md)
    :::column-end:::
    :::column:::
        [srv_rpcname](../../relational-databases/extended-stored-procedures-reference/srv-rpcname-extended-stored-procedure-api.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [srv_got_attention](../../relational-databases/extended-stored-procedures-reference/srv-got-attention-extended-stored-procedure-api.md)
    :::column-end:::
    :::column:::
        [srv_rpcnumber](../../relational-databases/extended-stored-procedures-reference/srv-rpcnumber-extended-stored-procedure-api.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
    :::column-end:::
    :::column:::
        [srv_rpcoptions](../../relational-databases/extended-stored-procedures-reference/srv-rpcoptions-extended-stored-procedure-api.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [srv_message_handler](../../relational-databases/extended-stored-procedures-reference/srv-message-handler-extended-stored-procedure-api.md)
    :::column-end:::
    :::column:::
        [srv_rpcowner](../../relational-databases/extended-stored-procedures-reference/srv-rpcowner-extended-stored-procedure-api.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [srv_paramdata](../../relational-databases/extended-stored-procedures-reference/srv-paramdata-extended-stored-procedure-api.md)
    :::column-end:::
    :::column:::
        [srv_rpcparams](../../relational-databases/extended-stored-procedures-reference/srv-rpcparams-extended-stored-procedure-api.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [srv_paraminfo](../../relational-databases/extended-stored-procedures-reference/srv-paraminfo-extended-stored-procedure-api.md)
    :::column-end:::
    :::column:::
        [srv_senddone](../../relational-databases/extended-stored-procedures-reference/srv-senddone-extended-stored-procedure-api.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [srv_paramlen](../../relational-databases/extended-stored-procedures-reference/srv-paramlen-extended-stored-procedure-api.md)
    :::column-end:::
    :::column:::
        [srv_sendmsg](../../relational-databases/extended-stored-procedures-reference/srv-sendmsg-extended-stored-procedure-api.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [srv_parammaxlen](../../relational-databases/extended-stored-procedures-reference/srv-parammaxlen-extended-stored-procedure-api.md)
    :::column-end:::
    :::column:::
        [srv_sendrow](../../relational-databases/extended-stored-procedures-reference/srv-sendrow-extended-stored-procedure-api.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [srv_paramname](../../relational-databases/extended-stored-procedures-reference/srv-paramname-extended-stored-procedure-api.md)
    :::column-end:::
    :::column:::
        [srv_setcoldata](../../relational-databases/extended-stored-procedures-reference/srv-setcoldata-extended-stored-procedure-api.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [srv_paramnumber](../../relational-databases/extended-stored-procedures-reference/srv-paramnumber-extended-stored-procedure-api.md)
    :::column-end:::
    :::column:::
        [srv_setcollen](../../relational-databases/extended-stored-procedures-reference/srv-setcollen-extended-stored-procedure-api.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [srv_paramset](../../relational-databases/extended-stored-procedures-reference/srv-paramset-extended-stored-procedure-api.md)
    :::column-end:::
    :::column:::
        [srv_setutype](../../relational-databases/extended-stored-procedures-reference/srv-setutype-extended-stored-procedure-api.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [srv_paramsetoutput](../../relational-databases/extended-stored-procedures-reference/srv-paramsetoutput-extended-stored-procedure-api.md)
    :::column-end:::
    :::column:::
        [srv_willconvert](../../relational-databases/extended-stored-procedures-reference/srv-willconvert-extended-stored-procedure-api.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [srv_paramstatus](../../relational-databases/extended-stored-procedures-reference/srv-paramstatus-extended-stored-procedure-api.md)
    :::column-end:::
    :::column:::
        [srv_wsendmsg](../../relational-databases/extended-stored-procedures-reference/srv-wsendmsg-extended-stored-procedure-api.md)
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        [srv_paramtype](../../relational-databases/extended-stored-procedures-reference/srv-paramtype-extended-stored-procedure-api.md)
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::
  
