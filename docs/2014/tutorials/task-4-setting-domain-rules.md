---
title: 'Attività 4: impostazione delle regole di dominio | Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3a7162ba-cf2f-481f-830d-bb6a02823827
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0104fe6b64ff2ecc1a37bb1da9691e34d7913f21
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85061085"
---
# <a name="task-4-setting-domain-rules"></a>Attività 4: Impostazione delle regole di dominio
  In questa attività viene creata una regola per il dominio di **posta elettronica di contatto** per verificare se l'indirizzo di posta elettronica termina con ** \@ Adventure-Works.com**. Per ulteriori informazioni sulla pagina, vedere l'argomento [creazione di una regola di dominio](https://msdn.microsoft.com/library/hh510397.aspx) .  
  
1.  Fare clic su **Contact email** nell' **elenco di domini**.  
  
2.  Passare alla scheda **regole di dominio** nel riquadro destro.  
  
     ![Pulsante della barra degli strumenti Aggiungi nuova regola di dominio](../../2014/tutorials/media/et-settingdomainrules-01.jpg "Pulsante della barra degli strumenti Aggiungi nuova regola di dominio")  
  
3.  Nel riquadro destro fare clic sul pulsante **Aggiungi una nuova regola di dominio** sulla barra degli strumenti (vedere l'immagine) per aggiungere una regola.  
  
4.  Digitare **email Validation** per il **nome della regola** e premere **invio**. Per impostazione predefinita, la casella di controllo **attiva** deve essere selezionata. Questo controllo consente di disattivare temporaneamente una regola.  
  
5.  Nel riquadro **Compila una regola** fare clic sulla **freccia in giù**e selezionare il **valore termina con**.  
  
6.  Digitare ** \@ Adventure-Works.com** nella casella di testo e premere **Tab**. È possibile aggiungere altre condizioni facendo clic sul pulsante **Aggiungi una nuova condizione al pulsante della** barra degli strumenti della clausola selezionata nel riquadro **Compila una regola** .  
  
     ![Regola di convalida posta elettronica](../../2014/tutorials/media/et-settingdomainrules-02.jpg "Regola di convalida posta elettronica")  
  
7.  Fare clic sul pulsante **Esegui la regola del dominio selezionato sui dati di test** sulla barra degli strumenti nel riquadro destro per testare la regola rispetto ai dati di esempio.  
  
     ![Pulsante della barra degli strumenti sull'esecuzione della regola di dominio nel test dei dati](../../2014/tutorials/media/et-settingdomainrules-03.jpg "Pulsante della barra degli strumenti sull'esecuzione della regola di dominio nel test dei dati")  
  
8.  Nella finestra di dialogo **testa regola di dominio** fare clic sul pulsante **Aggiungi un nuovo termine di test per la regola di dominio** sulla barra degli strumenti.  
  
     ![Finestra di dialogo Esegui la regola di dominio](../../2014/tutorials/media/et-settingdomainrules-04.jpg "Finestra di dialogo Esegui la regola di dominio")  
  
9. Digitare **frank7 \@ Adventure-Works.com** (un valore valido) nella colonna **Contact email** .  
  
10. Ripetere i due passaggi precedenti per aggiungere **joe2 \@ Adventure-Work.com** (un valore non valido senza ' s').  
  
11. Fare clic sull'ultimo pulsante (**testa la regola di dominio su tutti i termini**) sulla barra degli strumenti per testare i dati di input rispetto alla regola.  
  
     ![Pulsante della barra degli strumenti Testa la regola di dominio su tutti i termini](../../2014/tutorials/media/et-settingdomainrules-05.jpg "Pulsante della barra degli strumenti Testa la regola di dominio su tutti i termini")  
  
12. Si noti che la prima voce viene visualizzata come un elemento valido e la seconda come un elemento non valido.  
  
     ![Risultati di Testa regole di dominio](../../2014/tutorials/media/et-settingdomainrules-06.jpg "Risultati di Testa regole di dominio")  
  
13. Fare clic su **Chiudi** per chiudere la finestra di dialogo **testa regola di dominio** .  
  
## <a name="next-step"></a>passaggio successivo  
 [Attività 5: Impostazione delle relazioni basate su termini](../../2014/tutorials/task-5-setting-term-based-relationships.md)  
  
  
