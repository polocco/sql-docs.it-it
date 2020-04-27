---
title: Configurare le autorizzazioni del file system per l'accesso al motore di database | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- file system permissions
- service account [SQL Server], file system permissions
- permissions [SQL Server], file system
ms.assetid: 78bba43c-4edb-4216-84ac-d6246ae5546d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b23ed3a3a1f128d24bfec2a0066e63b09753311a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62811325"
---
# <a name="configure-file-system-permissions-for-database-engine-access"></a>Configurare le autorizzazioni del file system per l'accesso al motore di database
  In questo argomento viene illustrato come concedere al [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]l'accesso al file system nel percorso in cui sono archiviati i file di database. Il servizio [!INCLUDE[ssDE](../../includes/ssde-md.md)] deve disporre dell'autorizzazione del file system di Windows per accedere alla cartella file in cui sono archiviati i file di database. L'autorizzazione per il percorso predefinito viene configurata durante l'installazione. Se si posizionano i file di database in un percorso diverso, potrebbe essere necessario seguire questi passaggi per concedere al [!INCLUDE[ssDE](../../includes/ssde-md.md)] l'autorizzazione di controllo completo per il percorso in questione.  
  
 A partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] le autorizzazioni vengono assegnate al SID per servizio per ognuno dei relativi servizi. Tramite questo sistema viene fornito un livello elevato di isolamento e protezione del servizio. Il SID per servizio deriva dal nome del servizio ed è univoco per ogni servizio. L'argomento [Configurare account di servizio e autorizzazioni di Windows](configure-windows-service-accounts-and-permissions.md) descrive il SID per servizio e nella sezione **Privilegi e diritti di Windows**specifica i nomi. Si tratta del SID per servizio a cui deve essere assegnata l'autorizzazione di accesso per il percorso del file.  
  
## <a name="to-grant-file-system-permission-to-the-per-service-sid"></a>Per concedere le autorizzazioni del file system al SID per servizio  
  
1.  Utilizzando Esplora risorse passare al percorso del file system in cui sono archiviati i file di database. Fare clic con il pulsante destro del mouse sulla cartella del file system e quindi scegliere **Proprietà**.  
  
2.  Nella scheda **Sicurezza** fare clic su **Modifica**quindi su **Aggiungi**.  
  
3.  Nella finestra di dialogo per la **selezione di utenti, computer, account del servizio o gruppi** fare clic su **Percorsi**sopra l'elenco di percorsi, selezionare il nome del computer e quindi fare clic su **OK**.  
  
4.  Nella casella **immettere i nomi degli oggetti da selezionare** Digitare il nome del SID per servizio elencato nell'argomento **configurare account di servizio e autorizzazioni di Windows**nella documentazione online. Per il [!INCLUDE[ssDE](../../includes/ssde-md.md)] SID per servizio, utilizzare **NT SERVICE\MSSQLSERVER** per un'istanza predefinita o **NT SERVICE\MSSQL $ InstanceName** per un'istanza denominata.  
  
5.  Fare clic su **Controlla nomi** per convalidare la voce. La convalida spesso non viene completata e potrebbe essere indicato che il nome non è stato trovato. Quando si fa clic su **OK**, viene visualizzata la finestra di dialogo **Trovati più nomi** .  
  
6.  A questo punto, selezionare il SID per servizio, **MSSQLSERVER** o **NT SERVICE\MSSQL $ InstanceName**, quindi fare clic su **OK**.  
  
7.  Fare di nuovo clic su **OK** per tornare alla finestra di dialogo **autorizzazioni** .  
  
8.  Nella casella nome **gruppo o utente** selezionare il SID per servizio e quindi nella casella **autorizzazioni per** \<nome> selezionare la casella di controllo **Consenti** per **controllo completo**.  
  
9. Fare clic su **Applica**quindi due volte su **OK** per uscire.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestire il servizio Motore di database](manage-the-database-engine-services.md)   
 [Spostare i database di sistema](../../relational-databases/databases/system-databases.md)   
 [Spostare database utente](../../relational-databases/databases/move-user-databases.md)  
  
  
