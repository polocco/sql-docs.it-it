---
title: Membri dimensione derivati (Configurazione guidata dimensioni a modifica lenta) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.inferrdim.f1
ms.assetid: 809e395f-2e10-48ff-8860-56403f130628
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 35df99f7870130fb32d1cd7bf63b2bbc775b9381
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84939462"
---
# <a name="inferred-dimension-members-slowly-changing-dimension-wizard"></a>Membri dimensione derivati (Configurazione guidata dimensioni a modifica lenta)
  Utilizzare la finestra di dialogo **Membri dimensione derivati** per specificare le opzioni per l'utilizzo di membri derivati. I membri derivati esistono quando una tabella dei fatti fa riferimento a membri della dimensione non ancora caricati. Dopo il caricamento dei dati relativi al membro derivato, sarà possibile aggiornare il record esistente anziché crearne uno nuovo.  
  
 Per ulteriori informazioni su questa procedura guidata, vedere [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Abilita supporto per membri derivati**  
 Se si sceglie di abilitare i membri derivati, è necessario selezionare una delle due opzioni seguenti.  
  
 **Tutte le colonne con un tipo di modifica sono Null**  
 Consente di specificare se immettere valori Null in tutte le colonne con un tipo di modifica nel nuovo record del membro derivato.  
  
 **Usa una colonna booleana per indicare se il record corrente è un membro derivato**  
 Consente di specificare se utilizzare una colonna booleana esistente per indicare se il record corrente è un membro derivato.  
  
 **Indicatore membro derivato**  
 Se si è scelto di utilizzare una colonna booleana per indicare membri derivati, come descritto in precedenza, selezionare la colonna nell'elenco.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare gli output tramite Configurazione guidata dimensioni a modifica lenta](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
