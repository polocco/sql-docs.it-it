---
title: Eseguire un pacchetto in SQL Server Data Tools | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, running
- SSIS packages, running
- packages [Integration Services], running
- SQL Server Integration Services packages, running
ms.assetid: 318e6beb-5540-4101-82a5-18c9d47f0570
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9fdbc707a26c9cebae33c0dd432572cde3157c2d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66056417"
---
# <a name="run-a-package-in-sql-server-data-tools"></a>Eseguire un pacchetto in SQL Server Data Tools
  I pacchetti vengono eseguiti in genere in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] durante lo sviluppo, il debug e il test di pacchetti. In Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] l'esecuzione dei pacchetti è sempre immediata.  
  
 Durante l'esecuzione di un pacchetto [!INCLUDE[ssIS](../includes/ssis-md.md)] , in progettazione viene visualizzato lo stato di avanzamento dell'esecuzione del pacchetto nella scheda **stato** . È possibile visualizzare l'ora di inizio e di fine del pacchetto e le relative attività e contenitori, oltre a informazioni su eventuali attività o contenitori nel pacchetto non riusciti. Al termine dell'esecuzione del pacchetto, le informazioni di run-time rimangono disponibili nella scheda **Risultati esecuzione** . Per ulteriori informazioni, vedere la sezione relativa alla creazione di report sullo stato di avanzamento nell'argomento [debug del flusso di controllo](control-flow/control-flow.md).  
  
 **Distribuzione in fase di progettazione**. Quando si esegue un pacchetto in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], il pacchetto viene compilato e quindi distribuito in una cartella. Prima di eseguire il pacchetto è possibile specificare la cartella in cui deve essere distribuito. Se non si specifica alcuna cartella, per impostazione predefinita viene usata la cartella **bin** . Questo tipo di distribuzione è detto distribuzione in fase di progettazione.  
  
### <a name="to-run-a-package-in-sql-server-data-tools"></a>Per eseguire un pacchetto in SQL Server Data Tools  
  
1.  In Esplora soluzioni, se la soluzione contiene più progetti, fare clic con il pulsante destro del mouse sul progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenente il pacchetto e quindi scegliere **Imposta come oggetto di avvio** per impostare il progetto di avvio.  
  
2.  In Esplora soluzioni, se il progetto contiene più pacchetti, fare clic con il pulsante destro del mouse su un pacchetto e quindi scegliere **Imposta come oggetto di avvio** per impostare il pacchetto di avvio.  
  
3.  Per eseguire un pacchetto, attenersi a una delle procedure seguenti:  
  
    -   Aprire il pacchetto da eseguire e quindi fare clic sul pulsante **Avvia debug** sulla barra dei menu oppure premere F5. Al termine dell'esecuzione del pacchetto premere MAIUSC+F5 per tornare alla modalità progettazione.  
  
    -   In Esplora soluzioni fare clic con il pulsante destro del mouse sul pacchetto e quindi scegliere **Esegui pacchetto**.  
  
### <a name="to-specify-a-different-folder-for-design-time-deployment"></a>Per specificare una cartella diversa per la distribuzione in fase di progettazione  
  
1.  In Esplora soluzioni fare clic con il pulsante destro del mouse sulla cartella del progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenente il pacchetto da eseguire e quindi scegliere **Proprietà**.  
  
2.  Nella finestra di dialogo ** \<nome progetto> pagine delle proprietà** fare clic su **Compila**.  
  
3.  Aggiornare il valore della proprietà OutputPath per specificare la cartella da usare per la distribuzione in fase di progettazione e quindi fare clic su **OK**.  
  
## <a name="see-also"></a>Vedi anche  
 [Esecuzione di progetti e pacchetti](packages/run-integration-services-ssis-packages.md)   
 [Pacchetti di Integration Services &#40;SSIS&#41;](../../2014/integration-services/integration-services-ssis-packages.md)  
  
  
