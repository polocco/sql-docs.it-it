---
title: Distribuire applicazioni con azdata
titleSuffix: SQL Server Big Data Clusters
description: Distribuire uno script Python o R come applicazione in un cluster Big Data di SQL Server 2019.
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.metadata: seo-lt-2019
ms.date: 12/13/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f44b423ae369ee9210710702ca57340a79e62cf3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85728851"
---
# <a name="how-to-deploy-an-app-on-big-data-clusters-2019"></a>Come distribuire un'app in [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

Questo articolo descrive come distribuire e gestire uno script R e Python come applicazione all'interno di un cluster Big Data di SQL Server 2019.

## <a name="whats-new-and-improved"></a>Novità e miglioramenti

- Un'unica utilità della riga di comando per gestire cluster e app.
- Distribuzione semplificata di app con controllo granulare tramite file di specifiche.
- Supporto per l'hosting di tipi di applicazione aggiuntivi: SSIS e MLeap.
- [Estensione di Visual Studio Code](app-deployment-extension.md) per gestire la distribuzione di applicazioni.

Le applicazioni vengono distribuite e gestite tramite l'utilità della riga di comando `azdata`. Questo articolo fornisce alcuni esempi su come distribuire app dalla riga di comando. Per informazioni sull'uso in Visual Studio Code, fare riferimento a [Estensione di Visual Studio Code](app-deployment-extension.md).

Sono supportati i tipi seguenti di app:
- App R e Python (funzioni, modelli e app)
- MLeap Serving
- SQL Server Integration Services (SSIS)

## <a name="prerequisites"></a>Prerequisiti

- [Cluster Big Data di SQL Server 2019](deployment-guidance.md)
- [Utilità della riga di comando azdata](deploy-install-azdata.md)

## <a name="capabilities"></a>Capabilities

In SQL Server 2019 è possibile creare, eliminare, descrivere, inizializzare, elencare, eseguire e aggiornare l'applicazione. La tabella seguente descrive i comandi per la distribuzione di applicazioni che è possibile usare con **azdata**.

|Comando |Descrizione |
|:---|:---|
|`azdata login` | Esegue l'accesso al cluster Big Data di SQL Server |
|`azdata app create` | Crea un'applicazione. |
|`azdata app delete` | Elimina un'applicazione. |
|`azdata app describe` | Descrive un'applicazione. |
|`azdata app init` | Avvia un nuovo scheletro dell'applicazione. |
|`azdata app list` | Elenca le applicazioni. |
|`azdata app run` | Esegue un'applicazione. |
|`azdata app update`| Aggiorna un'applicazione. |

È possibile ottenere informazioni con il parametro `--help`, come nell'esempio seguente:

```bash
azdata app create --help
```

Le sezioni seguenti descrivono più dettagliatamente questi comandi.

## <a name="sign-in"></a>Accesso

Prima di distribuire applicazioni o interagirvi, accedere al cluster Big Data di SQL Server con il comando `azdata login`. Specificare l'indirizzo IP esterno del servizio `controller-svc-external`, ad esempio `https://ip-address:30080`, insieme al nome utente e alla password del cluster.

```bash
azdata login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
```

## <a name="aks"></a>Servizio Azure Kubernetes

Se si usa il servizio Azure Kubernetes, è necessario eseguire il comando seguente per ottenere l'indirizzo IP del servizio `controller-svc-external` eseguendo questo comando in una finestra di Bash o di comando:


```bash
kubectl get svc controller-svc-external -n <name of your big data cluster>
```

## <a name="kubernetes-clusters-created-with-kubeadm"></a>Cluster Kubernetes creati con kubeadm

Eseguire il comando seguente per ottenere l'indirizzo IP per accedere al cluster

```bash
kubectl get node --selector='node-role.kubernetes.io/master'
```

## <a name="create-an-app"></a>Creare un'app

Per creare un'applicazione, usare `azdata` con il comando `app create`. Questi file si trovano in locale nel computer da cui viene creata l'app.

Usare la sintassi seguente per creare una nuova app nel cluster Big Data:

```bash
azdata app create --spec <directory containing spec file>
```

Il comando seguente mostra un esempio del possibile aspetto di questo comando:

```bash
azdata app create --spec ./addpy
```

Si presuppone che l'applicazione sia archiviata nella cartella `addpy`. Questa cartella deve contenere anche un file di specifiche per l'applicazione, denominato `spec.yaml`. Per altre informazioni sul file `spec.yaml`, vedere la [pagina sulla distribuzione di applicazioni](concept-application-deployment.md).

Per distribuire l'app di esempio, creare i file seguenti in una directory denominata `addpy`:

- `add.py`. Copiare il codice Python seguente in questo file:
   ```py
   #add.py
  def add(x, y):
    result = x+y
    return result
  result=add(x,y)
   ```
- `spec.yaml`. Copiare il codice seguente in questo file:
   ```yaml
   #spec.yaml
   name: add-app #name of your python script
   version: v1  #version of the app
   runtime: Python #the language this app uses (R or Python)
   src: ./add.py #full path to the location of the app
   entrypoint: add #the function that will be called upon execution
   replicas: 1  #number of replicas needed
   poolsize: 1  #the pool size that you need your app to scale
   inputs:  #input parameters that the app expects and the type
     x: int
     y: int
   output: #output parameter the app expects and the type
     result: int
   ```

Eseguire quindi il comando seguente:

```bash
azdata app create --spec ./addpy
```

È possibile verificare se l'app viene distribuita usando il comando list:

```bash
azdata app list
```

Se la distribuzione non viene completata, `state` indicherà `WaitingforCreate`, come nell'esempio seguente:

```json
[
  {
    "name": "add-app",
    "state": "WaitingforCreate",
    "version": "v1"
  }
]
```

Al termine della distribuzione, il valore di `state` passerà allo stato `Ready`:

```json
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="list-an-app"></a>Elencare un'app

È possibile elencare tutte le app create correttamente con il comando `app list`.

Il comando seguente elenca tutte le applicazioni disponibili nel cluster Big Data:

```bash
azdata app list
```

Se si specifica un nome e una versione, vengono elencate l'app specifica e il relativo stato (Creating o Ready):

```bash
azdata app list --name <app_name> --version <app_version>
```

L'esempio seguente mostra questo comando:

```bash
azdata app list --name add-app --version v1
```

L'output dovrebbe essere simile all'esempio seguente:

```json
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="run-an-app"></a>Eseguire un'app

Se lo stato dell'app è `Ready`, è possibile usarla eseguendola con i parametri di input specificati. Usare la sintassi seguente per eseguire un'app:

```bash
azdata app run --name <app_name> --version <app_version> --inputs <inputs_params>
```

L'esempio seguente mostra il comando run:

```bash
azdata app run --name add-app --version v1 --inputs x=1,y=2
```

Se l'esecuzione riesce, l'output sarà lo stesso di quello specificato quando è stata creata l'app. Di seguito è riportato un esempio.

```json
{
  "changedFiles": [],
  "consoleOutput": "",
  "errorMessage": "",
  "outputFiles": {},
  "outputParameters": {
    "result": 3
  },
  "success": true
}
```

## <a name="create-an-app-skeleton"></a>Creare uno scheletro di un'app

Il comando init fornisce una sorta di impalcatura con gli elementi rilevanti necessari per la distribuzione di un'app. L'esempio seguente crea un elemento hello e a questo scopo è possibile eseguire il comando seguente.

```bash
azdata app init --name hello --version v1 --template python
```

Verrà creata una cartella denominata hello.  È possibile eseguire `cd` per passare alla directory ed esaminare i file generati nella cartella. Il file spec.yaml definisce l'app, specificandone ad esempio il nome, la versione e il codice sorgente. È possibile modificare le specifiche in modo da cambiare nome, versione, input e output.

Ecco un esempio di output del comando init, visualizzato nella cartella

```
hello.py
run-spec.yaml
spec.yaml
```

## <a name="describe-an-app"></a>Descrivere un'app

Il comando describe fornisce informazioni dettagliate sull'app, tra cui l'endpoint nel cluster. Viene usato in genere da uno sviluppatore di app per compilare un'app tramite il client Swagger e il servizio Web per interagire con l'app in modo RESTful. Per altre informazioni, vedere [Utilizzare applicazioni in cluster Big Data](big-data-cluster-consume-apps.md).

```json
{
  "input_param_defs": [
    {
      "name": "x",
      "type": "int"
    },
    {
      "name": "y",
      "type": "int"
    }
  ],
  "links": {
    "app": "https://10.1.1.3:30080/api/app/add-app/v1",
    "swagger": "https://10.1.1.3:30080/api/app/add-app/v1/swagger.json"
  },
  "name": "add-app",
  "output_param_defs": [
    {
      "name": "result",
      "type": "int"
    }
  ],
  "state": "Ready",
  "version": "v1"
}
```

## <a name="delete-an-app"></a>Eliminare un'app

Per eliminare un'app dal cluster Big Data, usare la sintassi seguente:

```bash
azdata app delete --name add-app --version v1
```

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su come integrare app distribuite in [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] nelle proprie applicazioni, vedere [Utilizzare applicazioni in cluster Big Data](big-data-cluster-consume-apps.md). È anche possibile fare riferimento ad altri esempi in [Esempi di distribuzione di app](https://aka.ms/sql-app-deploy).

Per altre informazioni su [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)], vedere [Che cosa sono i [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).
