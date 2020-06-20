---
title: Configurare log degli errori di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.configurelogs.configureerrorlogs.f1
ms.assetid: 03f0d463-9b0b-4af9-a853-da936d75e5af
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8acc27150f42049384e2789ef83ae66a737da9bd
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935052"
---
# <a name="configure-sql-server-error-logs"></a>Configura log degli errori di SQL Server
  In questo argomento viene descritto come visualizzare o modificare la modalità di riciclo dei log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="to-open-the-configure-sql-server-error-logs-dialog-box"></a>Per aprire la finestra di dialogo Configura log degli errori di SQL Server  
  
1.  In Esplora oggetti espandere l'istanza di SQL Server, espandere **Gestione**, fare clic con il pulsante destro del mouse su **Log di SQL Server**e quindi scegliere **Configura**.  
  
2.  Nella finestra di dialogo **Configura log degli errori di SQL Server** , scegliere dalle opzioni seguenti.  
  
     **Limita il numero di file di log degli errori creati prima di essere riciclati**  
     Selezionare questa opzione per limitare il numero di log degli errori creati prima di essere riciclati. Ogni volta che viene avviata un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene creato un nuovo log degli errori. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mantiene backup dei sei log precedenti, a meno che non si selezioni questa opzione e non si specifichi un diverso numero massimo di log degli errori tramite l'opzione seguente.  
  
     **Numero massimo di file di log degli errori**  
     Consente di specificare il numero massimo di log degli errori creati prima di essere riciclati. Il valore predefinito è 6 che corrisponde al numero di log di backup precedenti mantenuti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prima che vengano riciclati.  
  
  
