---
title: Gestione connessione di Archiviazione di Azure | Microsoft Doc
description: La gestione connessione di Archiviazione di Azure consente a un pacchetto SSIS di connettersi a un account di Archiviazione di Azure.
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpstorageconn.f1
- sql14.dts.designer.afpstorageconn.f1
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 44193053e6a5f09b2864b95ded9c5ac933c4cf95
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726022"
---
# <a name="azure-storage-connection-manager"></a>Gestione connessione di Archiviazione di Azure

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]

La gestione connessione di Archiviazione di Azure consente a un pacchetto SSIS di SQL Server di connettersi a un account di Archiviazione di Azure. La gestione connessione è un componente del [Feature Pack di SQL Server Integration Services (SSIS) per Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md). 
  
Nella finestra di dialogo **Aggiungi gestione connessione SSIS** selezionare **AzureStorage** > **Aggiungi**.  
  
Sono disponibili le proprietà seguenti.

- **Service:** specifica il servizio di archiviazione a cui connettersi.
- **Account name:** specifica il nome dell'account di archiviazione.
- **Authentication:** specifica il metodo di autenticazione da usare. Sono supportate le autenticazioni AccessKey, ServicePrincipal e SharedAccessSignature.
    - **AccessKey:** per questo metodo di autenticazione, specificare la **chiave dell'account**.
    - **ServicePrincipal:** per questo metodo di autenticazione, specificare l'**ID applicazione**, la **chiave applicazione** e l'**ID tenant** per l'entità servizio.
      Per il funzionamento di **Test connessione**, all'entità servizio deve essere assegnato almeno il **Ruolo con autorizzazioni di lettura per i dati dei BLOB di archiviazione** per l'account di archiviazione.
      Per altre informazioni, vedere [Concedere l'accesso ai dati dei BLOB e delle code di Azure con il controllo degli accessi in base al ruolo nel portale di Azure](/azure/storage/common/storage-auth-aad-rbac-portal#assign-rbac-roles-using-the-azure-portal).
    - **SharedAccessSignature:** Per questo metodo di autenticazione, specificare almeno il **token** della firma di accesso condiviso.
      Per testare la connessione, specificare anche l'ambito della risorsa in cui eseguire il test. Potrebbe essere il **servizio**, il **contenitore** o il **BLOB**.
      Per il **contenitore** e il **BLOB**, specificare rispettivamente il nome del contenitore e il percorso del BLOB.
      Per altre informazioni, vedere [Panoramica della firma di accesso condiviso di Archiviazione di Azure](/azure/storage/common/storage-sas-overview).
- **Environment:** specifica l'ambiente cloud che ospita l'account di archiviazione.

## <a name="managed-identities-for-azure-resources-authentication"></a>Identità gestite per l'autenticazione delle risorse di Azure
Quando si eseguono pacchetti SSIS in [Azure-SSIS Integration Runtime in Azure Data Factory](/azure/data-factory/concepts-integration-runtime#azure-ssis-integration-runtime), è possibile usare l'[identità gestita](/azure/data-factory/connector-azure-sql-database#managed-identity) associata alla data factory per l'autenticazione dell'archiviazione di Azure. La factory specificata può accedere e copiare i dati dall'account di archiviazione o nell'account di archiviazione usando questa identità.

Per informazioni generali sull'autenticazione per l'archiviazione di Azure, vedere [Autenticare l'accesso all'archiviazione di Azure tramite Azure Active Directory](/azure/storage/common/storage-auth-aad). Per usare l'autenticazione identità gestita per Archiviazione di Azure:

1. [Trovare l'identità gestita della data factory dal portale di Azure](/azure/data-factory/data-factory-service-identity). Visualizzare le **Proprietà** della data factory. Copiare l'**ID applicazione dell'identità gestita** (non l'**ID oggetto identità gestita**).

1. Concedere all'identità gestita l'autorizzazione appropriata nell'account di archiviazione. Per informazioni dettagliate sui ruoli, vedere [Gestire i diritti di accesso ai dati di Archiviazione di Azure con il controllo degli accessi in base al ruolo](/azure/storage/common/storage-auth-aad-rbac-portal).

    - **Come origine** in Controllo di accesso (IAM) concedere almeno il **Ruolo con autorizzazioni di lettura per i dati dei BLOB di archiviazione**.
    - **Come destinazione** in Controllo di accesso (IAM) concedere almeno il ruolo **Collaboratore ai dati dei BLOB di archiviazione**.

Configurare quindi l'autenticazione identità gestita per la gestione connessione di Archiviazione di Azure. Sono disponibili le opzioni seguenti:

- **Configurare in fase di progettazione.** In Progettazione SSIS fare doppio clic sulla gestione connessione di Archiviazione di Azure per aprire l'**editor gestione connessione di Archiviazione di Azure**. Selezionare **Use managed identity to authenticate on Azure** (Usa identità gestita per l'autenticazione in Azure).
    > [!NOTE]
    >  Attualmente questa opzione non ha effetto, vale a dire l'autenticazione identità gestita non funziona quando il pacchetto SSIS viene eseguito in Progettazione SSIS o in [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server.
    
- **Configurare in fase di esecuzione.** Quando il pacchetto viene eseguito tramite [SQL Server Management Studio (SSMS)](../ssis-quickstart-run-ssms.md) o l'[attività Esegui pacchetto SSIS di Azure Data Factory](/azure/data-factory/how-to-invoke-ssis-package-ssis-activity), individuare la gestione connessione di Archiviazione di Azure. Aggiornarne la proprietà `ConnectUsingManagedIdentity` impostandola su `True`.
    > [!NOTE]
    >  In Azure-SSIS Integration Runtime tutti gli altri metodi di autenticazione, ad esempio chiave di accesso ed entità servizio, preconfigurati nella gestione connessione di Archiviazione di Azure vengono ignorati quando viene usata l'autenticazione identità gestita per le operazioni sull'archiviazione.

> [!NOTE]
>  Per configurare l'autenticazione identità gestita nei pacchetti esistenti, il modo migliore consiste nel ricompilare almeno una volta il progetto SSIS con la [versione più recente di Progettazione SSIS](../../ssdt/download-sql-server-data-tools-ssdt.md). Ridistribuire il progetto SSIS in Azure-SSIS Integration Runtime, in modo che la nuova proprietà di gestione connessione `ConnectUsingManagedIdentity` venga aggiunta automaticamente a tutte le gestioni connessione di Archiviazione di Azure nel progetto SSIS. In alternativa, è possibile usare direttamente un override di proprietà con il percorso della proprietà **\Package.Connections[{nome della gestione connessione}].Properties[ConnectUsingManagedIdentity]** in fase di esecuzione.

## <a name="secure-network-traffic-to-your-storage-account"></a>Proteggere il traffico di rete verso l'account di archiviazione
Azure Data Factory è ora un [servizio Microsoft attendibile](/azure/storage/common/storage-network-security#trusted-microsoft-services) per Archiviazione di Azure. Se si usa l'autenticazione identità gestita, è possibile proteggere l'account di archiviazione [limitando l'accesso alle reti selezionate](/azure/storage/common/storage-network-security#change-the-default-network-access-rule) ma consentendo comunque al data factory di accedere all'account di archiviazione. Per istruzioni, vedere [Gestione delle eccezioni](/azure/storage/common/storage-network-security#managing-exceptions).

## <a name="see-also"></a>Vedere anche  
 [Connessioni in Integration Services &#40;SSIS&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md)