---
title: Editor della risoluzione dei riferimenti alle colonne | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.resolvereferences.mapper.F1
- sql12.dts.designer.resolvereferences.preview.F1
ms.assetid: bb3ee33c-79c4-4c76-a82f-71581b4a60f1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8b56e089feba35c3fe83e0a4e593309f8d1ac782
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "85431378"
---
# <a name="resolve-column-reference-editor"></a>Editor della risoluzione dei riferimenti alle colonne
  Quando un percorso di input viene disconnesso o se contiene colonne senza mapping, viene visualizzata un'icona di errore accanto al percorso di dati corrispondente. Per semplificare la risoluzione degli errori di riferimento alle colonne, il nuovo editor per la risoluzione dei riferimenti consente di collegare le colonne di output senza mapping alle colonne di input senza mapping per tutti i percorsi nell'albero di esecuzione. Nell'editor per la risoluzioni dei riferimenti verranno inoltre evidenziati i percorsi risolti.  
  
> [!NOTE]  
>  È ora possibile modificare un componente quando il relativo percorso di input è disconnesso  
  
 Dopo che sono stati risolti tutti i riferimenti alle colonne, in assenza di altri errori del percorso dati, accanto al percorso dati non verranno più visualizzate altre icone di errore.  
  
## <a name="options"></a>Opzioni  
 Colonne di output senza mapping (Origine):  
 Colonne del percorso a monte di cui non è stato eseguito il mapping  
  
 Colonne con mapping (Origine):  
 Colonne del percorso a monte di cui è stato eseguito il mapping alle colonne del percorso a valle  
  
 Colonne con mapping (Destinazione):  
 Colonne del percorso a monte di cui è stato eseguito il mapping alle colonne del percorso a valle  
  
 Colonne di input senza mapping (Destinazione):  
 Colonne del percorso a valle di cui non è stato eseguito il mapping  
  
 Elimina colonne input senza mapping  
 Selezionare Elimina colonne input senza mapping per ignorare le colonne senza mapping alla destinazione del percorso dati. Il pulsante Anteprima modifiche consente di visualizzare un elenco delle modifiche che si verificheranno alla pressione del pulsante OK.  
  
  
