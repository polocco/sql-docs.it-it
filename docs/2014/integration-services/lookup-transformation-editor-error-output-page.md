---
title: Editor trasformazione Ricerca (pagina output degli errori) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.erroroutput.f1
ms.assetid: 15d53bb0-8be1-46fb-b459-04a397e75fac
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d83ceee2756e217271663a768bcb6be70983dc0
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "85440238"
---
# <a name="lookup-transformation-editor-error-output-page"></a>Editor trasformazione Ricerca (pagina Output degli errori)
  Usare la pagina **Output degli errori** della finestra di dialogo **Editor trasformazione Ricerca** per specificare le opzioni di gestione degli errori.  
  
 Per ulteriori informazioni sulla trasformazione Ricerca, vedere [Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Input/Output**  
 Consente di visualizzare il nome dell'input.  
  
 **Colonna**  
 Non usato.  
  
 **Errore**  
 Consente di specificare il tipo di errore che si verifica quando vengono gestite righe prive di voci corrispondenti nel set di dati di riferimento:  
  
-   Ignorare l'errore e inviare le righe a un output.  
  
-   Reindirizzare le righe a un output degli errori.  
  
-   Interrompere il componente.  
  
 Questa opzione non è disponibile quando si seleziona **Reindirizza righe all'output nessuna corrispondenza** nell'elenco **Specificare come gestire le righe senza voci corrispondenti** . Questo elenco si trova nella pagina **Generale** della finestra di dialogo **Editor trasformazione Ricerca** .  
  
 **Argomenti correlati:** [Gestione degli errori nei dati](data-flow/error-handling-in-data.md)  
  
 **Troncamento**  
 Consente di specificare l'azione da eseguire quando si verifica il troncamento:  
  
-   Ignorare l'errore.  
  
-   Reindirizzare la riga.  
  
-   Interrompere il componente.  
  
 **Descrizione**  
 Consente di visualizzare la descrizione dell'operazione.  
  
 **Imposta questo valore nelle celle selezionate**  
 Consente di specificare l'azione da eseguire su tutte le celle selezionate quando si verifica un errore o un troncamento:  
  
-   Ignorare l'errore.  
  
-   Reindirizzare la riga.  
  
-   Interrompere il componente.  
  
 **Applica**  
 Consente di applicare l'opzione di gestione degli errori alle celle selezionate.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
