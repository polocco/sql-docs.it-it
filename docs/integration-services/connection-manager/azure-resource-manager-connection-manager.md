---
title: Gestione connessione Azure Resource Manager | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPARMCM.F1
- SQL14.DTS.DESIGNER.AFPARMCM.F1
ms.assetid: 8ce8024f-153f-4066-b607-0d36fefc79ed
author: Lingxi-Li
ms.author: lingxl
ms.openlocfilehash: 06cf645c41c27ec3a2275e19856c8ba935da73c4
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2020
ms.locfileid: "86913659"
---
# <a name="azure-resource-manager-connection-manager"></a>Gestione connessione Azure Resource Manager

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


La **gestione connessione Azure Resource Manager** consente a un pacchetto SSIS di gestire le risorse di Azure mediante un'[entità servizio](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).

**Gestione connessione di Azure Resource Manager** è un componente del [Feature Pack di SQL Server Integration Services (SSIS) per Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Per creare e configurare una **gestione connessione Azure Resource Manager**, eseguire la procedura seguente:

1. Nella finestra di dialogo **Aggiungi gestione connessione SSIS** selezionare **AzureResourceManager** e fare clic su **Aggiungi**.
2. Nella finestra di dialogo **Editor gestione connessione Azure Resource Manager** compilare i campi **ID applicazione**, **Chiave applicazione** e **ID tenant** per l'entità servizio. Per informazioni dettagliate su queste proprietà, vedere [questo](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal) articolo.
3. Scegliere **OK** per chiudere la finestra di dialogo.
4. È possibile visualizzare le proprietà del componente Gestione connessione create nella finestra **Proprietà** .
