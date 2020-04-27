---
title: Finestra di dialogo Definizioni di query diverse (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69639
- vdtsql.chm:69640
- vdt.dlgbox.querydefinitionsdiffer
ms.assetid: 90383473-2922-40e5-9682-3850849aa856
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 781963ddd2011c9e16cf67fdcd878039527546cd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "63294456"
---
# <a name="query-definitions-differ-dialog-box-visual-database-tools"></a>Finestra di dialogo Definizioni di query diverse (Visual Database Tools)
  Tramite questa finestra l'utente viene avvisato dell'impossibilità di rappresentare graficamente la query nei riquadri Diagramma e Criteri e della possibilità di modificare la query soltanto nel riquadro SQL.  
  
 La finestra di dialogo viene visualizzata quando si immette o si modifica un'istruzione SQL nel riquadro SQL, quindi si passa a un altro riquadro, si verifica la query o si esegue la query e viene applicata una delle seguenti condizioni:  
  
-   L'istruzione SQL è incompleta o contiene uno o più errori di sintassi.  
  
-   L'istruzione SQL è valida ma non è supportata nei riquadri grafici (ad esempio una query di unione).  
  
-   L'istruzione SQL è valida ma contiene una sintassi specifica per la connessione ai dati che si sta utilizzando.  
  
> [!TIP]  
>  È possibile verificare la validità di un'istruzione usando il pulsante **Verifica istruzione SQL** della barra degli strumenti **Query** .  
  
 Nella finestra di dialogo viene visualizzato un messaggio che indica il motivo per cui l'istruzione SQL non può essere rappresentata e quindi chiede come si desidera procedere.  
  
> [!NOTE]  
>  La finestra di dialogo **Definizioni di query diverse** non viene visualizzata se i riquadri Diagramma e Criteri sono stati nascosti.  
  
## <a name="options"></a>Opzioni  
 **Pulsante Ignora**  
 Scegliere questo pulsante per specificare che si desidera accettare l'istruzione SQL, per modificarla ulteriormente o per eseguirla. Se si accetta l'istruzione, i riquadri Diagramma e Criteri saranno visualizzati in grigio, in modo da indicare che non rappresentano l'istruzione del riquadro SQL.  
  
 **Pulsante Annulla**  
 Scegliere questo pulsante per annullare le modifiche apportate nel riquadro SQL.  
  
> [!NOTE]  
>  Se l'istruzione è corretta ma non è supportata graficamente da Progettazione query e Progettazione viste, sarà possibile eseguirla anche se non può essere rappresentata nei riquadri Diagramma e Criteri. Se, ad esempio, si immette una query di unione, l'istruzione può essere eseguita ma non rappresentata in altri riquadri.  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti di progettazione di query e viste &#40;Visual Database Tools&#41;](visual-database-tools.md)  
  
  
