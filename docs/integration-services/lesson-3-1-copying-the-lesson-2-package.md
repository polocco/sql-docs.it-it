---
title: 'Passaggio 1: Copiare il pacchetto della lezione 2 | Microsoft Docs'
ms.custom: ''
ms.date: 01/04/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 4bd91402-4e37-41de-ab78-8ca5a1948a37
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9448dada6a93e4cda928f75e06862ad42ee2eee5
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2020
ms.locfileid: "86922237"
---
# <a name="lesson-3-1-copy-the-lesson-2-package"></a>Lezione 3-1: Copiare il pacchetto della lezione 2

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



In questa attività si procederà alla creazione di una copia del pacchetto Lesson 2.dts creato nella lezione 2. Se non è stata completata la lezione 2, è possibile aggiungere al progetto il pacchetto della lezione 2 completato incluso nell'esercitazione e quindi copiarlo. Questa nuova copia verrà usata per tutto il seguito della lezione 3.

## <a name="create-the-lesson-3-package"></a>Creare il pacchetto della lezione 3

Attenersi alla procedura seguente se si sta copiando la lezione 2 completata.  Per copiare la lezione 2 di esempio, vedere la sezione successiva.

1.  Se [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools non è già aperto, selezionare **Start** > **Tutti i programmi** > **Microsoft SQL Server 2017** e quindi selezionare **SQL Server Data Tools**.

2.  Nel menu **File** selezionare **Apri** > **Progetto/Soluzione**, selezionare la cartella **Esercitazione SSIS** e quindi **Apri** e fare doppio clic su **SSIS Tutorial.sln**.

3.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Lesson 2.dtsx** e quindi selezionare **Copia**.

4.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Pacchetti SSIS** e quindi selezionare **Incolla**.

    Il nome predefinito del pacchetto copiato è Lesson 3.dtsx.

5.  In **Esplora soluzioni** fare doppio clic su **Lesson 3.dtsx** per aprire il pacchetto

6.  Fare clic con il pulsante destro del mouse in un punto qualsiasi dell'area di progettazione **Flusso di controllo** e selezionare **Proprietà**.

7.  Nella finestra **Proprietà** aggiornare la proprietà **Name** impostandola su **Lesson 3**.

8.  Selezionare la casella relativa alla proprietà **ID**, fare clic sulla freccia a discesa e quindi selezionare **\<Generate New ID>** .

## <a name="add-the-completed-lesson-2-package"></a>Aggiungere il pacchetto della lezione 2 completato

1.  Aprire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools e il progetto SSIS Tutorial.

2.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Pacchetti SSIS** e selezionare **Aggiungi pacchetto esistente**.

3.  Nella finestra di dialogo **Aggiungi copia del pacchetto esistente** in **Posizione pacchetto** selezionare **File system**.

4.  Selezionare il pulsante sfoglia **(...)** , passare a **Lesson 2.dtsx** nel computer e quindi selezionare **Apri**.

5.  Copiare e incollare il pacchetto della lezione 3, come illustrato nei passaggi 3-8 della sezione precedente.  
  
## <a name="go-to-next-task"></a>Esecuzione del passaggio successivo
[Passaggio 2: Aggiungere e configurare le funzionalità di registrazione](../integration-services/lesson-3-2-adding-and-configuring-logging.md)  
  
