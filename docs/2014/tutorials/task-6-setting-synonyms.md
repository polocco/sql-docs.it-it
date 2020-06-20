---
title: 'Attività 6: impostazione di sinonimi | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b7d35ee9-d1c9-41d9-bbc5-0ca7db93e54d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a6f4e870dca91e952fbeea95ef8f1198c64d8d6b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054280"
---
# <a name="task-6-setting-synonyms"></a>Attività 6: Impostazione di sinonimi
  In questa attività vengono impostati due valori di dominio, **Stati Uniti** e **Stati Uniti**, del dominio **Country** come sinonimi con **Stati Uniti** come valore principale. Poiché l'opzione **Usa valori iniziali** è stata selezionata durante la creazione del dominio **Country** , tutti i valori **USA** per il dominio **Country** verranno restituiti come **Stati Uniti** (Stati Uniti è il valore principale). Per altri dettagli, vedere [modificare i valori di dominio](https://msdn.microsoft.com/library/hh510408.aspx) .

1.  Selezionare **Country** nell'elenco dei domini.

2.  Passare alla scheda **valori di dominio** .

3.  Fare clic sul pulsante **Aggiungi nuovo valore di dominio** sulla barra degli strumenti.

4.  Digitare **USA** per il valore e premere **invio**.

5.  Selezionare **Stati Uniti** e **USA** con il tasto CTRL o MAIUSC, fare clic con il pulsante destro del mouse sugli elementi selezionati e quindi scegliere **Imposta come sinonimi**. Tramite DQS questi valori vengono raggruppati e uno di essi viene definito come valore iniziale con cui vengono sostituiti gli altri valori.

     ![Menu Imposta come sinonimi](../../2014/tutorials/media/et-settingsynonyms-01.jpg "Menu Imposta come sinonimi")

6.  Si noti che **Stati Uniti** è impostato come valore principale. Se si vuole che gli Stati Uniti siano i valori iniziali, è possibile fare clic con il pulsante destro del mouse su USA e selezionare **Imposta come opzione leader** . Per questa esercitazione si userà **Stati Uniti** come valore principale.

     ![Stati Uniti e USA come sinonimi](../../2014/tutorials/media/et-settingsynonyms-02.jpg "Stati Uniti e USA come sinonimi")

## <a name="next-step"></a>passaggio successivo
 [Attività 7: Creazione di un dominio composito](../../2014/tutorials/task-7-creating-a-composite-domain.md)


