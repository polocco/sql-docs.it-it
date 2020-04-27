---
title: Opzioni (editor di testo-XML-pagina varie) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 1a9509f0-c663-4b31-b396-7f5dc4371651
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: eb3422b859ce4e58fc05564357876c5fe09fcdff
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66089213"
---
# <a name="options-text-editor---xml---miscellaneous-page"></a>Opzioni (Editor di testo - XML - pagina Varie)

La finestra di dialogo **Opzioni** consente di modificare le impostazioni del completamento automatico e dello schema per l'editor XML. Per visualizzare queste impostazioni, scegliere **Opzioni** dal menu **Strumenti**, espandere la cartella **Editor di testo** , fare clic su **XML** e quindi su **Varie** .  
  
## <a name="auto-insert"></a>Inserimento automatico  
 **Chiudi i tag**  
 Nell'editor di testo i tag di chiusura vengono aggiunti automaticamente durante la creazione di elementi XML. Se viene selezionato il tag di inizio di un elemento, viene inserito automaticamente il tag di chiusura corrispondente, che include un prefisso di spazio dei nomi corrispondente. Questa casella di controllo è selezionata per impostazione predefinita.  
  
 **Virgolette per gli attributi**  
 Durante la creazione di attributi XML, l'editor inserisce i caratteri `="``"` e posiziona l'accento circonflesso (**^)** all'interno delle virgolette. Questa casella di controllo è selezionata per impostazione predefinita.  
  
 **Dichiarazioni degli spazi dei nomi**  
 Vengono inserite automaticamente le dichiarazioni degli spazi dei nomi, se necessarie. Questa casella di controllo è selezionata per impostazione predefinita.  
  
 **Altri markup (commenti, CDATA)**  
 Commenti, CDATA, DOCTYPE, istruzioni di elaborazione e altri markup vengono completati automaticamente. Questa casella di controllo è selezionata per impostazione predefinita.  
  
## <a name="network"></a>Rete  
 **Scarica automaticamente le DTD e gli schemi**  
 Gli schemi e le definizioni DTD (Document Type Definitions) vengono scaricati automaticamente da percorsi HTTP. Questa caratteristica utilizza System.Net con il rilevamento automatico del server proxy. Questa casella di controllo è selezionata per impostazione predefinita.  
  
## <a name="outlining"></a>struttura  
 **Attiva modalità struttura all'apertura dei file**  
 Attiva la modalità struttura quando viene aperto un file. Questa casella di controllo è selezionata per impostazione predefinita.  
  
## <a name="caching"></a>Memorizzazione nella cache  
 **Schemi**  
 Specifica il percorso della cache degli schemi. Se si fa clic sul pulsante Sfoglia viene aperto il percorso della cache degli schemi corrente in una nuova finestra. Il percorso predefinito è * \<Management Studio directory di installazione>* \Xml\Schemas.  
