---
title: Archivia file | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VisualStudio.SourceControl.CheckInDialog
helpviewer_keywords:
- checking in files
ms.assetid: 0657a387-8411-4406-bef9-d262a5bfa269
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 052859e4605162daa87789b5c61d2ef9d33d4177
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936042"
---
# <a name="check-in-files"></a>Archiviazione di file
  Per rendere accessibili ad altri utenti i file modificati inclusi nel controllo del codice sorgente, è necessario archiviarli nel controllo del codice sorgente. Quando un file viene archiviato, la versione archiviata viene scritta nel provider del controllo del codice sorgente e diventa la versione più recente del file.  
  
 È possibile usare il comando **Archivia** per archiviare i file. Quando si utilizza questo comando, vengono archiviati anche tutti i file inclusi nella soluzione o nel progetto. L'archiviazione di un singolo file di codice sorgente tuttavia non comporta l'archiviazione anche del progetto o della soluzione ai quali il file appartiene.  
  
### <a name="to-check-in-a-file"></a>Per archiviare un file  
  
1.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul file da archiviare, quindi fare clic su **Archivia**.  
  
2.  Se viene visualizzata la finestra **di dialogo Archivia** , selezionare le opzioni appropriate e quindi fare clic su **OK**.  
  
     **Archivia**  
     Consente di archiviare tutti gli elementi selezionati.  
  
     **Colonne**  
     Consente di specificare le colonne da visualizzare e il relativo ordine.  
  
     **Commenti**  
     Consente di aggiungere un commento da associare all'operazione di archiviazione.  
  
     **Non visualizzare la finestra di dialogo Estrai durante l'archiviazione degli elementi**  
     Consente di evitare la visualizzazione della finestra di dialogo durante le operazioni di archiviazione.  
  
     **Visualizzazione semplice**  
     Consente di visualizzare i file di cui si sta eseguendo l'archiviazione come elenchi semplici sotto la relativa connessione del controllo del codice sorgente.  
  
     **Nome**  
     Consente di visualizzare i nomi degli elementi da archiviare. Accanto agli elementi viene visualizzata la casella di controllo selezionata. Se non si desidera archiviare un determinato elemento, deselezionare la relativa casella di controllo.  
  
     **Opzioni**  
     Consente di visualizzare le opzioni di archiviazione specifiche del plug-in del controllo del codice sorgente quando si fa clic sulla freccia a destra del pulsante.  
  
     **Ordina**  
     Consente di eseguire l'ordinamento delle colonne visualizzate.  
  
     **Visualizzazione albero**  
     Consente di visualizzare la gerarchia di cartelle e di file per gli elementi di cui si sta eseguendo l'archiviazione.  
  
 Se il file archiviato non fa parte di un'estrazione condivisa, nell'ambiente [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ne viene immediatamente eseguita l'archiviazione. In caso contrario, può venire chiesto di unire la versione utilizzata a quelle create da altri utenti.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare un elenco di file modificati](../../2014/database-engine/view-a-list-of-modified-files.md)   
 [Gestione delle archiviazioni](../../2014/database-engine/manage-checkins.md)  
  
  
