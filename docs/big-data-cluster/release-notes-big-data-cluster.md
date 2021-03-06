---
title: Note sulla versione dei cluster Big Data di SQL Server
titleSuffix: SQL Server big data clusters
description: Questo articolo descrive gli aggiornamenti più recenti e i problemi noti per i cluster Big Data di SQL Server.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 10/01/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 28cfd7e9a78646527bb8c0508535a1475159e35c
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91891081"
---
# <a name="sql-server-2019-big-data-clusters-release-notes"></a>Note sulla versione dei cluster Big Data di SQL Server 2019

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

Le note sulla versione seguenti si applicano a [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]. Questo articolo è suddiviso in sezioni corrispondenti a ogni versione. Ogni versione ha un collegamento a un articolo del supporto che descrive le modifiche CU, oltre ai collegamenti ai download dei pacchetti Linux. L'articolo elenca anche i [problemi noti](#known-issues) per le versioni più recenti dei [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)].

## <a name="supported-platforms"></a>Piattaforme supportate

Questa sezione illustra le piattaforme supportate con i BDC.

### <a name="kubernetes-platforms"></a>Piattaforme Kubernetes

|Piattaforma|Versioni supportate|
|---------|---------|
|Vanilla (upstream) Kubernetes|Distribuire BDC in locale usando la versione minima 1.13 del cluster Kubernetes. Vedere [Kubernetes version and version skew support policy](https://kubernetes.io/docs/setup/release/version-skew-policy/).|
|Red Hat OpenShift|Distribuire BDC in locale usando la versione minima 4.3 del cluster OpenShift. Vedere [Red Hat OpenShift Container Platform Life Cycle Policy](https://access.redhat.com/support/policy/updates/openshift).<br><br> Introduzione del supporto in SQL Server 2019 CU5.|
|Servizio Azure Kubernetes|Distribuire BDC nella versione minima 1.13 del cluster del servizio Azure Kubernetes.<br/>Per i criteri di supporto delle versioni, vedere [Versioni di Kubernetes supportate nel servizio Azure Kubernetes](/azure/aks/supported-kubernetes-versions).|
|Azure Red Hat OpenShift (ARO)|Distribuire BDC nella versione minima 4.3 di ARO. Vedere [Azure Red Hat OpenShift](/azure/openshift/). <br><br> Introduzione del supporto in SQL Server 2019 CU5.|

### <a name="host-os-for-kubernetes"></a>Sistema operativo host per Kubernetes

|Piattaforma|Sistema operativo host|Versioni supportate|
|---------|---------|
|Kubernetes|Ubuntu|16.04|
|Kubernetes|Red Hat Enterprise Linux|7.3, 7.4, 7.5, 7.6|
|OpenShift|Red Hat Enterprise Linux/CoreOS |Vedere le [note sulla versione di OpenShift](https://docs.openshift.com/container-platform/4.3/release_notes/ocp-4-3-release-notes.html#ocp-4-3-about-this-release)|

### <a name="sql-server-editions"></a>Edizioni di SQL Server

|Edizione|Note|
|---------|---------|
|Enterprise<br/>Standard<br/>Developer| L'edizione del cluster Big Data è determinata dall'edizione dell'istanza master di SQL Server. In fase di distribuzione, per impostazione predefinita viene distribuita l'edizione Developer. È possibile modificare l'edizione dopo la distribuzione. Vedere [Configurare l'istanza master di SQL Server](./configure-sql-server-master-instance.md). |

## <a name="tools"></a>Strumenti

|Piattaforma|Versioni supportate|
|---------|---------|
|`azdata`|Come procedura consigliata, usare la versione più recente disponibile. A partire da SQL Server versione 2019 CU5, `azdata` include una versione semantica indipendente dal server. <br/><br/>Eseguire `azdata –-version` per convalidare la versione.<br/><br/>Vedere [Cronologia delle versioni](#release-history) per la versione più recente.|
|Azure Data Studio|Ottenere la build più recente di [Azure Data Studio](../azure-data-studio/download-azure-data-studio.md).|

Per un elenco completo, vedere [Strumenti necessari](deploy-big-data-tools.md#which-tools-are-required).

## <a name="release-history"></a>Cronologia delle versioni

Nella tabella seguente viene elencata la cronologia delle versioni per [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)].

| Versione<sup>1</sup> | Versione di BDC  | `azdata` Versione <sup>2</sup> | Data di rilascio |
|----------------------|--------------|-------------------------------|--------------|
| [CU6](#cu6)          | 15.0.4053.23 | 20.0.1                        | 2020-08-04   |
| [CU5](#cu5)          | 15.0.4043.16 | 20.0.0                        | 2020-06-22   |
| [CU4](#cu4)          | 15.0.4033.1  | 15.0.4033                     | 2020-03-31   |
| [CU3](#cu3)          | 15.0.4023.6  | 15.0.4023                     | 2020-03-12   |
| [CU2](#cu2)          | 15.0.4013.40 | 15.0.4013                     | 2020-02-13   |
| [CU1](#cu1)          | 15.0.4003.23 | 15.0.4003                     | 07 gennaio 2020   |
| [GDR1](#rtm)         | 15.0.2070.34 | 15.0.2070                     | 4 novembre 2019   |

<sup>1</sup>Le versioni seguenti non sono disponibili per BDC:
- CU7
- CU8

<sup>2</sup>La versione `azdata` riflette la versione dello strumento al momento del rilascio dell'aggiornamento cumulativo (CU). `azdata` può anche essere rilasciato indipendentemente dal rilascio del server, pertanto è possibile che si ottengano versioni più recenti quando si installano i pacchetti più recenti. Le versioni più recenti sono compatibili con gli aggiornamenti cumulativi (CU) rilasciati in precedenza.

## <a name="how-to-install-updates"></a>Come installare gli aggiornamenti

Per installare gli aggiornamenti, vedere [Come aggiornare [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](deployment-upgrade.md).

## <a name="cu6-july-2020"></a><a id="cu6"></a> CU6 (luglio 2020)

Aggiornamento cumulativo 6 (CU6) per SQL Server 2019.

|Versione pacchetto | Tag dell'immagine |
|-----|-----|
|15.0.4053.23 |[2019-CU6-ubuntu-16.04]

Questa versione include correzioni e miglioramenti secondari. Gli articoli seguenti includono informazioni correlate a questi aggiornamenti:

- [Gestire l'accesso al cluster Big Data in modalità Active Directory](manage-user-access.md)
- [Distribuire [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] in modalità Active Directory](active-directory-deploy.md)
- [Distribuire un cluster Big Data di SQL Server con disponibilità elevata](deployment-high-availability.md)
- [Configurare un cluster Big Data di SQL Server](configure-cluster.md)
- [Configurare Apache Spark e Apache Hadoop nei cluster Big Data](configure-spark-hdfs.md)
- [Proprietà di configurazione dell'istanza master di SQL Server](reference-config-master-instance.md)
- [Proprietà di configurazione di Apache Spark e Apache Hadoop (HDFS)](reference-config-spark-hadoop.md)
- [Modello di controllo degli accessi in base al ruolo di Kubernetes e impatto sugli utenti e sugli account del servizio che gestiscono i cluster Big Data](kubernetes-rbac.md)

## <a name="cu5-june-2020"></a><a id="cu5"></a> CU5 (giugno 2020)

Aggiornamento cumulativo 5 (CU5) per SQL Server 2019.

|Versione pacchetto | Tag dell'immagine |
|-----|-----|
|15.0.4043.16 |[2019-CU5-ubuntu-16.04]

### <a name="added-capabilities"></a>Funzionalità aggiuntive

- Supporto per la distribuzione di cluster Big Data in Red Hat OpenShift. Il supporto include OpenShift Container Platform distribuito in locale, versione 4.3 e successive, e Azure Red Hat OpenShift. Vedere [Distribuire cluster Big Data di SQL Server in OpenShift](deploy-openshift.md)
- Aggiornamento del modello di sicurezza della distribuzione di BDC in modo che i contenitori con privilegi distribuiti nell'ambito di BDC non siano più *necessari*. Oltre che senza privilegi, per impostazione predefinita i contenitori vengono eseguiti come utente non ROOT per tutte le nuove distribuzioni con SQL Server 2019 CU5. 
- Aggiunta del supporto per la distribuzione di più cluster Big Data in un dominio di Active Directory.
- L'interfaccia della riga di comando `azdata` ha la propria versione semantica, indipendente dal server. Qualsiasi dipendenza tra le versioni client e server di azdata è stata rimossa. È consigliabile usare la versione più recente sia per il client sia per il server per assicurarsi di ottenere gli ultimi miglioramenti e correzioni.
- Introduzione di due nuove stored procedure,  sp_data_source_objects e sp_data_source_table_columns, per supportare l'introspezione di determinate origini esterne. Queste possono essere usate dagli utenti direttamente tramite T-SQL per l'individuazione dello schema e per determinare le tabelle disponibili per la virtualizzazione. Queste modifiche vengono sfruttate nella procedura guidata Tabella esterna dell'[estensione di virtualizzazione dei dati](../azure-data-studio/extensions/data-virtualization-extension.md) per Azure Data Studio, che consente di creare tabelle esterne da SQL Server, Oracle, MongoDB e Teradata.
- Aggiunta del supporto per rendere persistenti le personalizzazioni eseguite in Grafana. Prima della versione CU5, i clienti possono aver notato che qualsiasi modifica nelle configurazioni di Grafana viene perduta al riavvio del pod `metricsui` (che ospita il dashboard di Grafana). Questo problema è stato corretto e tutte le configurazioni vengono ora rese persistenti. 
- Correzione di un problema di sicurezza relativo all'API usata per raccogliere metriche di pod e nodi tramite Telegraf (ospitato nei pod `metricsdc`). Come risultato di questa modifica, Telegraf richiede ora un account di servizio, un ruolo del cluster e associazioni del cluster per ottenere le autorizzazioni necessarie per la raccolta delle metriche di pod e nodi. Per altre informazioni, vedere [Ruolo del cluster necessario per la raccolta di metriche di pod e nodi](kubernetes-rbac.md#cluster-role-required-for-pods-and-nodes-metrics-collection).
- Aggiunta di due opzioni di funzionalità per controllare la raccolta di metriche di pod e nodi. Se si usano soluzioni diverse per il monitoraggio dell'infrastruttura Kubernetes, è possibile disattivare la raccolta predefinita di metriche per pod e nodi host impostando *allowNodeMetricsCollection* e *allowPodMetricsCollection* su false nel file di configurazione della distribuzione control.json. Per gli ambienti OpenShift, queste opzioni sono impostate su false per impostazione predefinita nei profili di distribuzione predefiniti, perché la raccolta di metriche di pod e nodi richiede capacità con privilegi.

## <a name="cu4-april-2020"></a><a id="cu4"></a> CU4 (aprile 2020)

Aggiornamento cumulativo 4 (CU4) per SQL Server 2019. La versione del motore di database di SQL Server per questa versione è 15.0.4033.1.

|Versione pacchetto | Tag dell'immagine |
|-----|-----|
|15.0.4033.1 |[2019-CU4-ubuntu-16.04]

## <a name="cu3-march-2020"></a><a id="cu3"></a> CU3 (marzo 2020)

Aggiornamento cumulativo 3 (CU3) per SQL Server 2019. La versione del motore di database di SQL Server per questa versione è 15.0.4023.6.

|Versione pacchetto | Tag dell'immagine |
|-----|-----|
|15.0.4023.6 |[2019-CU3-ubuntu-16.04]

### <a name="resolved-issues"></a>Problemi risolti

SQL Server 2019 CU3 risolve i problemi seguenti dalle versioni precedenti.

- [Distribuzione con repository privato](#deployment-with-private-repository)
- [Possibile esito negativo dell'aggiornamento a causa di un timeout](#upgrade-may-fail-due-to-timeout)

## <a name="cu2-february-2020"></a><a id="cu2"></a> CU2 (febbraio 2020)

Aggiornamento cumulativo 2 (CU2) per SQL Server 2019. La versione del motore di database di SQL Server per questa versione è 15.0.4013.40.

|Versione pacchetto | Tag dell'immagine |
|-----|-----|
|15.0.4013.40 |[2019-CU2-ubuntu-16.04]

## <a name="cu1-january-2020"></a><a id="cu1"></a> CU1 (gennaio 2020)

Versione Cumulative Update 1 (CU1) per SQL Server 2019. La versione del motore di database di SQL Server per questa versione è 15.0.4003.23.

|Versione pacchetto | Tag dell'immagine |
|-----|-----|
|15.0.4003.23|[2019-CU1-ubuntu-16.04]

## <a name="gdr1-november-2019"></a><a id="rtm"></a> GDR1 (novembre 2019)

SQL Server 2019 General Distribution Release 1 (GDR1): introduce la disponibilità generale per [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-nover.md)]. La versione del motore di database di SQL Server per questa versione è 15.0.2070.34.

|Versione pacchetto | Tag dell'immagine |
|-----|-----|
|15.0.2070.34|[2019-GDR1-ubuntu-16.04]

[!INCLUDE [sql-server-servicing-updates-version-15](../includes/sql-server-servicing-updates-version-15.md)]

## <a name="known-issues"></a>Problemi noti

### <a name="empty-livy-jobs-before-you-apply-cumulative-updates"></a>Svuotare i processi Livy prima di applicare gli aggiornamenti cumulativi

- **Versioni interessate**: Con l'aggiornamento cumulativo corrente

- **Problema e impatto per i clienti**: Durante un upgrade, `sparkhead` restituisce l'errore 404.

- **Soluzione alternativa**: Prima di aggiornare i cluster Big Data, verificare che non siano presenti sessioni Livy o processi batch attivi. Per evitare questo problema, seguire le istruzioni riportate in [Aggiornamento dalla versione supportata](deployment-upgrade.md#upgrade-from-supported-release). 

   Se Livy restituisce un errore 404 durante il processo di aggiornamento, riavviare il server Livy in entrambi i nodi `sparkhead`. Ad esempio:

   ```console
   kubectl -n <clustername> exec -it sparkhead-0/sparkhead-1 -c hadoop-livy-sparkhistory -- exec supervisorctl restart livy
   ```

### <a name="big-data-cluster-generated-service-accounts-passwords-expiration"></a>Scadenza password account del servizio generate dal cluster Big Data

- **Versioni interessate**: Tutte le distribuzioni di cluster Big Data con integrazione di Active Directory, indipendentemente dalla versione

- **Problema e impatto per i clienti**: Durante la distribuzione di cluster Big Data, il flusso di lavoro genera un set di [account del servizio](active-directory-objects.md). A seconda dei criteri di scadenza delle password impostati nel controller di dominio, le password per questi account possono scadere (il valore predefinito è 42 giorni). Attualmente non è disponibile alcun meccanismo di rotazione delle credenziali per tutti gli account dei cluster Big Data, quindi il cluster diventa inutilizzabile quando viene raggiunta la scadenza.

- **Soluzione alternativa**: Aggiornare i criteri di scadenza per gli account del servizio del cluster Big Data impostandoli su "La password non scade mai" nel controller di dominio. Per un elenco completo di questi account, vedere [Oggetti di Active Directory generati automaticamente](active-directory-objects.md). Questa azione può essere eseguita prima o dopo la scadenza. Nel secondo caso, Active Directory attiverà nuovamente le password scadute.

### <a name="credentials-for-accessing-services-through-gateway-endpoint"></a>Credenziali per l'accesso ai servizi tramite l'endpoint gateway

- **Versioni interessate**: nuovi cluster distribuiti a partire dalla versione CU5.

- **Problema e impatto per i clienti**: per i nuovi cluster Big Data distribuiti con SQL Server 2019 CU5, il nome utente del gateway non è **root**. Se l'applicazione usata per la connessione all'endpoint gateway usa le credenziali errate, verrà visualizzato un errore di autenticazione. Questa modifica è il risultato dell'esecuzione di applicazioni all'interno del cluster Big Data come utente non ROOT. Come nuovo comportamento predefinito a partire da SQL Server 2019 CU5, quando si distribuisce un nuovo cluster Big Data tramite la versione CU5, il nome utente per l'endpoint gateway è basato sul valore passato tramite la variabile di ambiente **AZDATA_USERNAME**. Si tratta dello stesso nome utente usato per il controller e gli endpoint SQL Server. Questa modifica ha impatto solo sulle nuove distribuzioni, mentre i cluster Big Data esistenti distribuiti con qualunque versione precedente continuano a usare **root**. Non vi è alcun impatto per le credenziali quando il cluster viene distribuito in modo da usare l'autenticazione di Active Directory. 

- **Soluzione alternativa**: Azure Data Studio gestirà la modifica delle credenziali in modo trasparente per la connessione effettuata al gateway, in modo da consentire l'esperienza di esplorazione di Hadoop Distributed File System in ObjectExplorer. È necessario installare la [versione più recente di Azure Data Studio](../azure-data-studio/download-azure-data-studio.md), che include le modifiche necessarie per la risoluzione di questo caso d'uso.
Per altri scenari in cui è necessario fornire credenziali per l'accesso al servizio tramite il gateway, ad esempio l'accesso con `azdata` o l'accesso a dashboard Web per Spark, è necessario assicurarsi che vengano usate le credenziali corrette. Se la destinazione è un cluster esistente distribuito prima della versione CU5, si continuerà a usare il nome utente **root** per la connessione al gateway, anche dopo l'aggiornamento del cluster a CU5. Se si distribuisce un nuovo cluster tramite la build CU5, accedere specificando il nome utente corrispondente alla variabile di ambiente **AZDATA_USERNAME**.

### <a name="pods-and-nodes-metrics-not-being-collected"></a>Mancata raccolta di metriche di pod e nodi

- **Versioni interessate**: cluster nuovi ed esistenti che usano immagini CU5

- **Problema e impatto per i clienti**: come risultato di una correzione per la sicurezza relativa all'API usata da `telegraf` per raccogliere metriche di pod e nodi host, gli utenti possono aver notato che le metriche non vengono raccolte. Questo problema può avvenire in distribuzioni nuove ed esistenti di BDC (dopo l'aggiornamento alla versione CU5). Come risultato della correzione, Telegraf richiede ora un account di servizio con autorizzazioni del ruolo a livello di cluster. La distribuzione tenta di creare l'account di servizio e il ruolo del cluster necessari, ma se l'utente che distribuisce il cluster o esegue l'aggiornamento non ha autorizzazioni sufficienti, la distribuzione o l'aggiornamento continuerà con un avviso e riuscirà, ma le metriche di pod e nodi non verranno raccolte.

- **Soluzione alternativa**: è possibile chiedere a un amministratore di creare il ruolo e l'account di servizio, prima o dopo la distribuzione o l'aggiornamento, perché vengano usati da BDC. [Questo articolo](kubernetes-rbac.md#cluster-role-required-for-pods-and-nodes-metrics-collection) descrive come creare gli artefatti necessari.

### <a name="azdata-bdc-copy-logs-command-failure"></a>Comando `azdata bdc copy-logs` non riuscito

- **Versioni interessate**: `azdata` versione *20.0.0*

- **Problema e impatto per i clienti**: l'implementazione del comando *copy-logs* presuppone che lo strumento client `kubectl` sia installato nel computer client da cui viene eseguito il comando. Se si esegue il comando su un cluster BDC installato su OpenShift da un client in cui è installato solo lo strumento `oc`, si riceve un errore: *Si è verificato un errore durante la raccolta dei log: [WinError 2] Impossibile trovare il file specificato*.

- **Soluzione alternativa**: installare lo strumento `kubectl` nello stesso computer client e ripetere il comando `azdata bdc copy-logs`. Vedere [qui](deploy-big-data-tools.md) le istruzioni su come installare `kubectl`.

### <a name="deployment-with-private-repository"></a>Distribuzione con repository privato

- **Versioni interessate**: GDR1, CU1, CU2. Risolto per CU3.

- **Problema e impatto per i clienti**: L'aggiornamento da un repository privato presenta requisiti specifici

- **Soluzione alternativa**: Se si usa un repository privato per eseguire preventivamente il pull delle immagini per la distribuzione o l'aggiornamento dei cluster Big Data, verificare che le immagini di compilazione correnti e le immagini di compilazione di destinazione si trovino nel repository privato. Questo consente di ripristinare correttamente lo stato precedente, se necessario. Se le credenziali del repository privato sono state modificate dopo la distribuzione originale, poi, aggiornare il segreto corrispondente in Kubernetes prima di eseguire l'aggiornamento. `azdata` non supporta l'aggiornamento delle credenziali tramite `AZDATA_PASSWORD` e le variabili di ambiente `AZDATA_USERNAME`. Aggiornare il segreto tramite [`kubectl edit secrets`](https://kubernetes.io/docs/concepts/configuration/secret/#editing-a-secret). 

L'aggiornamento tramite repository diversi per le compilazioni correnti e di destinazione non è supportato.

### <a name="upgrade-may-fail-due-to-timeout"></a>Possibile esito negativo dell'aggiornamento a causa di un timeout

- **Versioni interessate**: GDR1, CU1, CU2. Risolto per CU3.

- **Problema e impatto per i clienti**: l'aggiornamento può avere esito negativo a causa di un timeout.

   Il codice seguente illustra il possibile aspetto dell'errore:

   ```
   >azdata.EXE bdc upgrade --name <mssql-cluster>
   Upgrading cluster to version 15.0.4003

   NOTE: Cluster upgrade can take a significant amount of time depending on
   configuration, network speed, and the number of nodes in the cluster.

   Upgrading Control Plane.
   Control plane upgrade failed. Failed to upgrade controller.
   ```

   Questo errore si verifica con maggiore probabilità quando si aggiorna un cluster Big Data nel servizio Azure Kubernetes.

- **Soluzione alternativa**: aumentare il timeout per l'aggiornamento. 

   Per aumentare i timeout per un aggiornamento, modificare la mappa di configurazione dell'aggiornamento stesso. Per modificare la mappa di configurazione dell'aggiornamento:

   1. Eseguire il comando seguente:

      ```bash
      kubectl edit configmap controller-upgrade-configmap
      ```

   2. Modificare i campi seguenti:

       **`controllerUpgradeTimeoutInMinutes`** Indica il numero di minuti di attesa del completamento dell'aggiornamento del controller o del database del controller. Il valore predefinito è 5. Per l'aggiornamento impostare almeno il valore 20.

       **`totalUpgradeTimeoutInMinutes`** : designa la quantità di tempo combinata per il completamento dell'aggiornamento (aggiornamento `controller` + `controllerdb`) da parte del controller e del database del controller. Il valore predefinito è 10. Per l'aggiornamento impostare almeno il valore 40.

       **`componentUpgradeTimeoutInMinutes`** : Definisce la quantità di tempo disponibile per il completamento di ogni fase successiva dell'aggiornamento. L'impostazione predefinita è 30. Per l'aggiornamento impostare su 45.

   3. Salvare e uscire.

   Lo script Python seguente rappresenta un altro metodo per l'impostazione del timeout:

   ```python
   from kubernetes import client, config
   import json

   def set_upgrade_timeouts(namespace, controller_timeout=20, controller_total_timeout=40, component_timeout=45):
       """ Set the timeouts for upgrades

       The timeout settings are as follows

       controllerUpgradeTimeoutInMinutes: sets the max amount of time for the controller
           or controllerdb to finish upgrading

       totalUpgradeTimeoutInMinutes: sets the max amount of time to wait for both the
           controller and controllerdb to complete their upgrade

       componentUpgradeTimeoutInMinutes: sets the max amount of time allowed for
           subsequent phases of the upgrade to complete
       """
       config.load_kube_config()

       upgrade_config_map = client.CoreV1Api().read_namespaced_config_map("controller-upgrade-configmap", namespace)

       upgrade_config = json.loads(upgrade_config_map.data["controller-upgrade"])

       upgrade_config["controllerUpgradeTimeoutInMinutes"] = controller_timeout

       upgrade_config["totalUpgradeTimeoutInMinutes"] = controller_total_timeout

       upgrade_config["componentUpgradeTimeoutInMinutes"] = component_timeout

       upgrade_config_map.data["controller-upgrade"] = json.dumps(upgrade_config)

       client.CoreV1Api().patch_namespaced_config_map("controller-upgrade-configmap", namespace, upgrade_config_map)
   ```

### <a name="livy-job-submission-from-azure-data-studio-ads-or-curl-fail-with-500-error"></a>L'invio di un processo Livy da Azure Data Studio (ADS) o curl ha esito negativo con l'errore 500

- **Problema e impatto per i clienti**: in una configurazione a disponibilità elevata, le risorse condivise Spark `sparkhead` sono configurate con più repliche. In questo caso, è possibile che si verifichino errori durante l'invio di un processo Livy da Azure Data Studio (ADS) o `curl`. A scopo di verifica, se si usa il comando `curl` per qualsiasi pod `sparkhead`, la connessione viene rifiutata. Ad esempio, `curl https://sparkhead-0:8998/` o `curl https://sparkhead-1:8998` restituisce l'errore 500.

   Ciò accade negli scenari seguenti:

   - I pod ZooKeeper o i processi per ogni istanza di ZooKeeper vengono riavviati alcune volte.
   - La connettività di rete tra il pod `sparkhead` e i pod ZooKeeper non è affidabile.

- **Soluzione alternativa**: riavviare entrambi i server Livy.

   ```bash
   kubectl -n <clustername> exec sparkhead-0 -c hadoop-livy-sparkhistory supervisorctl restart livy
   ```

   ```bash
   kubectl -n <clustername> exec sparkhead-1 -c hadoop-livy-sparkhistory supervisorctl restart livy
   ```

### <a name="create-memory-optimized-table-when-master-instance-in-an-availability-group"></a>Creare una tabella ottimizzata per la memoria quando l'istanza master si trova in un gruppo di disponibilità

- **Problema e impatto per i clienti**: non è possibile usare l'endpoint primario esposto per la connessione ai database del gruppo di disponibilità (listener) per creare tabelle ottimizzate per la memoria.

- **Soluzione alternativa**: per creare tabelle ottimizzate per la memoria quando l'istanza master di SQL Server è in una configurazione di un gruppo di disponibilità, [connettersi all'istanza di SQL Server](deployment-high-availability.md#instance-connect), esporre un endpoint, connettersi al database di SQL Server e creare le tabelle ottimizzate per la memoria nella sessione creata con la nuova connessione.

### <a name="insert-to-external-tables-active-directory-authentication-mode"></a>Eseguire l'inserimento in tabelle esterne in modalità di autenticazione di Active Directory

- **Problema e impatto per i clienti**: quando l'istanza master di SQL Server è in modalità di autenticazione di Active Directory, una query che seleziona solo da tabelle esterne, dove almeno una delle tabelle esterne si trova in un pool di archiviazione, ed esegue l'inserimento in un'altra tabella esterna, restituisce:

   ```
   Msg 7320, Level 16, State 102, Line 1
   Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "SQLNCLI11". Only domain logins can be used to query Kerberized storage pool.
   ```

- **Soluzione alternativa**: modificare la query in uno dei modi seguenti. Unire la tabella del pool di archiviazione a una tabella locale oppure eseguire prima l'inserimento nella tabella locale, quindi leggere dalla tabella locale per eseguire l'inserimento nel pool di dati.

### <a name="transparent-data-encryption-capabilities-can-not-be-used-with-databases-that-are-part-of-the-availability-group-in-the-sql-server-master-instance"></a>Non è possibile usare le funzionalità Transparent Data Encryption con i database che fanno parte del gruppo di disponibilità nell'istanza master di SQL Server

- **Problema e impatto per i clienti**: in una configurazione a disponibilità elevata, non è possibile usare database con crittografia abilitata dopo un failover, perché la chiave master usata per la crittografia è diversa per ogni replica. 

- **Soluzione alternativa**: non è disponibile alcuna soluzione alternativa per questo problema. È consigliabile evitare di abilitare la crittografia in questa configurazione fino a quando non verrà resa disponibile una correzione.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sui [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)], vedere [Che cosa sono i [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)