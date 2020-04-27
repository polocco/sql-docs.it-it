---
title: Riconciliare le modifiche apportate da più utenti (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- table modifications [SQL Server], multiple users
- reconciling changes made by multiple users
- modifications made by multiple users
ms.assetid: fc7ed4f2-ad3d-47fc-a3ef-51e5bb069ef0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f13b7f6a2e34d7819b930d919e9fd773e2c993d7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "63010658"
---
# <a name="reconcile-changes-made-by-multiple-users-visual-database-tools"></a>Riconciliare le modifiche apportate da più utenti (Visual Database Tools)
  In un ambiente multiutente può accadere che uno stesso oggetto venga modificato contemporaneamente da più utenti. Questo problema può accadere quando si lavora alla struttura dell'oggetto in Progettazione tabelle o in Progettazione diagrammi di database oppure con i valori dei risultati restituiti nel riquadro Risultati di Progettazione query e Progettazione viste. In questo caso possono verificarsi conflitti che è possibile risolvere.  
  
## <a name="conflicts-in-the-table-or-database-diagram-designers"></a>Conflitti in Progettazione tabelle o Progettazione diagrammi di database  
 È possibile ad esempio che un altro utente elimini o rinomini una tabella mentre si sta utilizzando la stessa tabella o una tabella correlata in Progettazione tabelle. Quando si prova a salvare la tabella, si viene avvisati dalla [Finestra di dialogo Rilevate modifiche al database &#40;Visual Database Tools&#41;](visual-database-tools.md) che il database è stato aggiornato dopo l'apertura della tabella.  
  
 In questa finestra di dialogo viene inoltre visualizzato un elenco degli oggetti di database che verranno influenzati dal salvataggio della tabella. A questo punto, è possibile:  
  
-   Scegliere **Sì** per salvare la tabella e aggiornare il database con tutte le modifiche presenti nell'elenco.  
  
     Questa operazione potrebbe influire anche su altre tabelle che condividono gli stessi oggetti di database. Si supponga ad esempio di modificare la colonna `au`_`id` nella tabella `titleauthors` e che un altro utente stia usando la tabella `authors` che è correlata alla tabella `titleauthors` dalla colonna `au`\_`id` . Il salvataggio della propria tabella influirà sulla tabella dell'altro utente. In modo analogo, si supponga che un altro utente abbia definito un vincolo CHECK per la colonna `qty` nella tabella `sales` . Se si elimina la colonna `qty` e si salva la tabella `sales` , il vincolo CHECK dell'altro utente verrà influenzato.  
  
-   Scegliere **No** per annullare il salvataggio.  
  
     La tabella potrà così essere chiusa senza salvarla. Quando verrà riaperta, la tabella rifletterà i dati contenuti nel database.  
  
-   Scegliere **Salva file di testo** per salvare un elenco delle modifiche.  
  
     È possibile salvare l'elenco delle modifiche del database indicate nella finestra di dialogo **Rilevate modifiche al database** in un file di testo, in modo da poter individuare la causa delle modifiche apportate dagli altri utenti. Se, ad esempio, un altro utente ha modificato una tabella che si era scelto di contrassegnare per l'eliminazione, potrà essere necessario verificare se la tabella dovrà essere eliminata prima di aggiornare il database.  
  
## <a name="conflicts-in-the-query-and-view-designer"></a>Conflitti in Progettazione query e Progettazione viste  
 Quando si esegue una query o si ottengono i risultati di una vista, i dati vengono visualizzati nel riquadro [Risultati](results-pane-visual-database-tools.md). Può accadere che più utenti lavorino contemporaneamente allo stesso set di dati, con il rischio che si generino conflitti.  
  
 Si supponga ad esempio di eseguire contemporaneamente a un proprio collega una query per visualizzare tutti i dati della tabella `titleauthors` . Nel primo record restituito il collega cambia il nome da Barb a Barbara. A questo punto, nel database il campo conterrà Barbara, mentre nel proprio set di risultati sarà ancora visualizzato il nome Barb. Se ora si digita Barbara e si fa clic all'esterno della riga, un messaggio chiederà come si desidera risolvere il conflitto.  
  
-   Scegliere **Sì** per aggiornare il database con le modifiche apportate.  
  
     In questo modo verrà eseguito l'override delle modifiche apportate dal collega.  
  
-   Fare clic su **No** per lasciare che il set di risultati venga aggiornato in base al contenuto corrente del database.  
  
     In questo modo le proprie modifiche verranno sostituite da quelle apportate dal collega.  
  
-   Scegliere **Annulla** per continuare ad apportare modifiche senza risolvere il conflitto.  
  
     In questo caso non sarà possibile eseguire il commit delle modifiche nel database.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestra di dialogo Rilevate modifiche al database &#40;Visual Database Tools&#41;](visual-database-tools.md)  
  
  
