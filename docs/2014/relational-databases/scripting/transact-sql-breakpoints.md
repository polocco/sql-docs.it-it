---
title: Punti di interruzione Transact-SQL
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoints
ms.assetid: c234430f-bd94-4d0d-9e74-2bf11681fa50
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 84ff925f2aa68ee81268eaca2faa3920f3ec407b
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/01/2020
ms.locfileid: "82718534"
---
# <a name="transact-sql-breakpoints"></a>Punti di interruzione Transact-SQL
  I punti di interruzione specificano la sospensione dell'esecuzione del debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] in un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] specifica, per consentire le visualizzazione dello stato degli elementi di codice in tale punto.  
  
## <a name="breakpoints"></a>Punti di interruzione  
 Quando si esegue il debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] , è possibile attivare o attivare un punto di interruzione per istruzioni specifiche. Quando viene raggiunta un'istruzione con un punto di interruzione, il debugger sospende l'esecuzione per consentire la visualizzazione di informazioni di debug, ad esempio i valori presenti in variabili e parametri.  
  
 È possibile gestire i punti di interruzione singolarmente nella finestra dell'editor o collettivamente tramite la finestra **Punti di interruzione** . È possibile modificare i punti di interruzione per specificare elementi quali condizioni specifiche in presenza delle quali l'esecuzione deve essere sospesa oppure le azioni in caso di esecuzione del punto di interruzione.  
  
## <a name="breakpoint-tasks"></a>Attività correlate ai punti di interruzione  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Viene decritto come specificare l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] in corrispondenza della quale il debugger deve sospendere l'esecuzione.|[Attivare/disattivare un punto di interruzione](../spatial/point.md)|  
|Viene descritto come disattivare temporaneamente un punto di interruzione e riattivarlo in un secondo momento. Viene inoltre descritto come eliminare un punto di interruzione.|[Abilitare, disabilitare ed eliminare punti di interruzione](enable-disable-and-delete-breakpoints.md)|  
|Viene descritto come specificare una condizione che definisce se l'interruzione nel punto deve avvenire in base alla valutazione di un'espressione Transact-SQL specificata.|[Impostare una condizione del punto di interruzione](specify-a-breakpoint-condition.md)|  
|Viene descritto come specificare un numero di passaggi che determina l'interruzione solo quando l'istruzione contenente il punto di interruzione è stata eseguita un determinato numero di volte.|[Specificare un numero di passaggi](specify-a-hit-count.md)|  
|Viene descritto come specificare un filtro che determina l'interruzione in corrispondenza del punto impostato solo per processi o thread specificati.|[Specificare un filtro per un punto di interruzione](specify-a-breakpoint-filter.md)|  
|Viene descritto come specificare un'azione **Quando raggiunto** , ovvero un'operazione personalizzata eseguita quando viene eseguita l'istruzione del punto di interruzione. Ne è un esempio la visualizzazione di un messaggio.|[Specificare un'azione del punto di interruzione](specify-a-breakpoint-action.md)|  
|Viene descritto come modificare la posizione di un punto di interruzione.|[Modificare la posizione di un punto di interruzione](edit-a-breakpoint-location.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni del debugger Transact-SQL](transact-sql-debugger-information.md)  
  
  
