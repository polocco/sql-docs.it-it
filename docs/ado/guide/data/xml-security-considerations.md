---
description: Considerazioni sulla sicurezza per XML
title: Considerazioni sulla sicurezza XML | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- XML security in ADO
ms.assetid: fadbd38e-6e7b-4b81-96ea-85169c664374
author: rothja
ms.author: jroth
ms.openlocfilehash: 608ad67d531573d0124ea312252e6d30c289bf15
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2020
ms.locfileid: "88978792"
---
# <a name="xml-security-considerations"></a>Considerazioni sulla sicurezza per XML
I metodi ADO Save e Open sull'oggetto recordset non sono considerati operazioni sicure per l'esecuzione in Internet Explorer. Pertanto, se questi metodi vengono utilizzati in un codice di script in esecuzione in un'applicazione o in un controllo ospitato in un browser, la configurazione di sicurezza del browser avrà effetto sul comportamento.  
  
 Internet Explorer 5 fornisce restrizioni di sicurezza per le operazioni di questo tipo per impostazione predefinita nelle zone Internet. Con tale configurazione, il recordset non può accedere al file system locale sul client o accedere a tutte le origini dati esterne al dominio del server da cui è stata scaricata la pagina. In particolare, quando viene eseguito all'interno dell'host del browser, un recordset può essere salvato di nuovo in un file solo se si trova nello stesso server da cui è stata scaricata la pagina. Analogamente, è possibile aprire un recordset eseguendone il caricamento da un file solo se tale file si trova nello stesso server da cui è stata scaricata la pagina.  
  
## <a name="see-also"></a>Vedere anche  
 [Persistenza di record in formato XML](./persisting-records-in-xml-format.md)