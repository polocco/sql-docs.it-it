---
title: Gestione connessione della sottoscrizione di Azure | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpsubscrconn.f1
- sql11.dts.designer.afpsubscrconn.f1
ms.assetid: e1225327-c308-4c50-8f44-c411f52ef378
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bff1286525983b32c2191f1f8864a0f2bef0e6b0
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "85434248"
---
# <a name="azure-subscription-connection-manager"></a>Gestione connessione della sottoscrizione di Azure
  Gestione connessione di Azure HDInsight consente di connettere un pacchetto SSIS a una sottoscrizione di Azure usando i valori specificati per le proprietà: ID sottoscrizione Azure e Certificato di gestione.

1.  Nella finestra di dialogo **Aggiungi gestione connessione SSIS** mostrata sopra selezionare **Sottoscrizione di Azure**, quindi fare clic su **Aggiungi**.  Viene visualizzata la finestra di dialogo **Editor gestione connessione di Sottoscrizione di Azure** .

     ![SSIS-AzureSubscriptionManager](../media/ssis-azuresubscriptionmanager.png "SSIS-AzureSubscriptionManager")

2.  Immettere l'ID sottoscrizione di Azure, che identifica in modo univoco una sottoscrizione di Azure, per **ID sottoscrizione di Azure**.  Il valore si trova nel [portale di gestione di Azure](https://manage.windowsazure.com) nella pagina **Impostazioni** :

     ![SSIS-AzureSettings-SubscriptionID](../media/ssis-azuresettings-subscriptionid.png "SSIS-AzureSettings-SubscriptionID")

3.  Scegliere il **percorso dell'archivio** e il **nome dell'archivio** del certificato di gestione dagli elenchi a discesa.

4.  Immettere l'**identificazione personale del certificato di gestione** oppure fare clic su **Sfoglia...** per scegliere un certificato dall'archivio selezionato. Il certificato deve essere caricato come certificato di gestione per la sottoscrizione. A tale scopo, fare clic su **Carica** nella pagina seguente del portale di Azure. Per altre informazioni, vedere questo [post MSDN](https://msdn.microsoft.com/library/azure/gg551722.aspx) .

     ![SSIS-AzureSettings-ManagementCertificate](../media/ssis-azuresettings-managementcertificate.png "SSIS-AzureSettings-ManagementCertificate")

5.  Fare clic su **Test connessione** per testare la connessione.

6.  Fare clic su **OK** per chiudere la finestra di dialogo.


