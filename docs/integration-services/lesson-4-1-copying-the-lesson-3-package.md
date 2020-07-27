---
title: 'Passaggio 1: Copiare il pacchetto della lezione 3 | Microsoft Docs'
ms.custom: ''
ms.date: 01/07/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 0d053786-5203-43f3-a613-27a8dd2bc44a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a5d6eec55e339d8aaf23d04b88d14fc945e8f0c7
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2020
ms.locfileid: "86922148"
---
# <a name="lesson-4-1-copy-the-lesson-3-package"></a>Lezione 4-1: Copiare il pacchetto della lezione 3

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



In questa attività si procederà alla creazione di una copia del pacchetto Lesson 3.dtsx creato nella lezione 3. Se non è stata completata la lezione 3, è possibile aggiungere al progetto il pacchetto completo della lezione 3 incluso nell'esercitazione e quindi effettuarne una copia. Questa nuova copia verrà usata per tutto il seguito della lezione 4.  
  
## <a name="create-the-lesson-4-package"></a>Creare il pacchetto della lezione 4  
  
Attenersi alla procedura seguente se si sta copiando la lezione 3 completata.  Per copiare la lezione 3 di esempio, vedere la sezione successiva.

1.  Se [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools non è già aperto, selezionare **Start** > **Tutti i programmi** > **Microsoft SQL Server 2017** e quindi selezionare **SQL Server Data Tools**.

2.  Nel menu **File** selezionare **Apri** > **Progetto/Soluzione**, selezionare la cartella **Esercitazione SSIS** e quindi **Apri** e fare doppio clic su **SSIS Tutorial.sln**.

3.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Lesson 3.dtsx** e quindi selezionare **Copia**.

4.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Pacchetti SSIS** e quindi selezionare **Incolla**.

    Il nome predefinito del pacchetto copiato è **Lesson 4.dtsx**.

5.  In **Esplora soluzioni** fare doppio clic su **Lesson 4.dtsx** per aprire il pacchetto

6.  Fare clic con il pulsante destro del mouse in un punto qualsiasi dell'area di progettazione **Flusso di controllo** e selezionare **Proprietà**.

7.  Nella finestra **Proprietà** aggiornare la proprietà **Name** impostandola su **Lesson 4**.

8.  Selezionare la casella relativa alla proprietà **ID**, fare clic sulla freccia a discesa e quindi selezionare **\<Generate New ID>** .

## <a name="add-the-completed-lesson-3-package"></a>Aggiungere il pacchetto della lezione 3 completato

1.  Aprire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools e il progetto SSIS Tutorial.

2.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Pacchetti SSIS** e selezionare **Aggiungi pacchetto esistente**.

3.  Nella finestra di dialogo **Aggiungi copia del pacchetto esistente** , in **Posizione pacchetto**, selezionare **File system**.

4.  Selezionare il pulsante sfoglia **(...)** , passare a **Lesson 3.dtsx** nel computer e quindi selezionare **Apri**.

5.  Copiare e incollare il pacchetto della lezione 3, come illustrato nei passaggi 3-8 della sezione precedente.

  
## <a name="go-to-next-task"></a>Esecuzione del passaggio successivo  
[Passaggio 2: Creare un file danneggiato](../integration-services/lesson-4-2-creating-a-corrupted-file.md)  
  
