---
title: Editor attività Trasferisci stored procedure master (pagina generale) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferstoredprocedurestask.general.f1
helpviewer_keywords:
- Transfer Stored Procedures Task Editor
ms.assetid: fa1abd4c-e2be-427f-be53-860e49c97227
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: cab36a851c5ef50f0690e9bc0a1a18676d335e50
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66054922"
---
# <a name="transfer-master-stored-procedures-task-editor-general-page"></a>Editor attività Trasferisci stored procedure master (pagina Generale)
  Usare la pagina **Generale** della finestra di dialogo **Editor attività Trasferisci stored procedure master** per assegnare un nome e una descrizione all'attività Trasferisci stored procedure master. Per altre informazioni su questa attività, vedere [Attività Trasferisci stored procedure master](control-flow/transfer-master-stored-procedures-task.md).  
  
> [!NOTE]  
>  L'attività consente solo il trasferimento di stored procedure appartenenti a **dbo** da un database **master** del server di origine a un database **master** del server di destinazione. Per poter creare stored procedure nel server di destinazione, gli utenti devono disporre dell'autorizzazione CREATE PROCEDURE nel database **master** del server di destinazione o essere membri del ruolo predefinito del server **sysadmin** nel server di destinazione.  
  
## <a name="options"></a>Opzioni  
 **Nome**  
 Consente di digitare un nome univoco per l'attività Trasferisci stored procedure master. Tale nome viene utilizzato come etichetta nell'icona dell'attività.  
  
> [!NOTE]  
>  I nomi delle attività devono essere univoci all'interno di un pacchetto.  
  
 **Descrizione**  
 Consente di digitare una descrizione dell'attività Trasferisci stored procedure master.  
  
## <a name="see-also"></a>Vedi anche  
 [Integration Services riferimento a errori e messaggi](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Attività Integration Services](control-flow/integration-services-tasks.md)   
 [Editor attività Trasferisci stored procedure master &#40;pagina stored procedure&#41;](../../2014/integration-services/transfer-master-stored-procedures-task-editor-stored-procedures-page.md)   
 [Pagina Espressioni](expressions/expressions-page.md)  
  
  
