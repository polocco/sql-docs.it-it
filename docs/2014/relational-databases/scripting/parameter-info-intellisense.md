---
title: Informazioni parametri (IntelliSense)
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Parameter Info option [IntelliSense]
- stored function parameter completion [Intellisense]
- language references [SQL Server]
- IntelliSense [SQL Server], Parameter Info option
ms.assetid: 56c2aac9-c65c-4679-b62c-d9f689876dde
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b842f35c2852ce6ed607e943199bb322823651b9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "75242012"
---
# <a name="parameter-info-intellisense"></a>Informazioni parametri (IntelliSense)
  L'opzione [!INCLUDE[msCoName](../../includes/msconame-md.md)] Informazione sul parametro **di** IntelliSense consente di aprire un elenco di parametri che include informazioni relative a numero, nomi e tipi dei parametri necessari per una funzione o per una stored procedure. Il parametro in grassetto indica il parametro successivo necessario quando viene digitata una funzione o una stored procedure.  
  
 L'elenco dei parametri è visualizzato anche per le funzioni nidificate. Se si digita una funzione come parametro per un'altra funzione, nell'elenco dei parametri verranno visualizzati i parametri per la funzione interna. Quando l'elenco dei parametri della funzione interna è completo, verranno quindi visualizzati i parametri della funzione esterna.  
  
#### <a name="to-view-parameter-info-for-functions-or-stored-procedures"></a>Per visualizzare le informazioni sul parametro per le funzioni o le stored procedure  
  
1.  Dopo il nome di una funzione, digitare una normale parentesi aperta per aprire l'elenco dei parametri. Dopo avere digitato il nome di una stored procedure, digitare un normale spazio per ottenere informazioni sui parametri della procedura.  
  
     In IntelliSense viene visualizzata la dichiarazione completa per la funzione o per i parametri di una stored procedure in una finestra popup subito al di sotto del punto di inserimento. Il primo parametro dell'elenco viene visualizzato in grassetto.  
  
2.  Durante l'immissione dei parametri, il grassetto cambia per indicare il parametro successivo da immettere.  
  
3.  Premere ESC in qualsiasi momento per chiudere l'elenco oppure continuare a digitare fino a completare la funzione.  
  
     Nel caso di una funzione, se viene digitata la parentesi di chiusura viene chiuso anche l'elenco dei parametri.  
  
#### <a name="to-manually-start-parameter-info"></a>Per avviare manualmente l'opzione Informazioni sul parametro  
  
1.  Scegliere **IntelliSense** dal menu **Modifica** , quindi selezionare **Informazioni parametri**.  
  
2.  Utilizzare i tasti di scelta rapida CTRL+MAIUSC+BARRA SPAZIATRICE.  
  
 Per altre informazioni, vedere [Configurare IntelliSense &#40;SQL Server Management Studio&#41;](configure-intellisense-sql-server-management-studio.md).  
  
> [!NOTE]  
>  L'opzione **Informazioni parametri** è disponibile solo per l'editor di query di [!INCLUDE[ssDE](../../includes/ssde-md.md)] e per l'editor di query XML.  
  
  
