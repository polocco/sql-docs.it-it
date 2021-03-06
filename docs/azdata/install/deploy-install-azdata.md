---
title: Installare il modulo azdata
titleSuffix: ''
description: Informazioni su come installare lo strumento azdata.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 83da4e1554e1a6fa112c6fc8f629d30cbcb97d4d
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725256"
---
# <a name="install-azdata"></a>Installare `azdata`

[!INCLUDE[azdata](../../includes/applies-to-version/azdata.md)]

`azdata` è un'utilità da riga di comando scritta in Python per il bootstrap e la gestione di servizi dati tramite le API REST. 

## <a name="find-latest-version"></a>Trovare l'ultima versione

L'elenco dei file per la versione più recente è sempre disponibile all'indirizzo [https://aka.ms/azdata](https://aka.ms/azdata).

Per individuare la versione installata e verificare se è necessario aggiornarla, eseguire `azdata --version`.

## <a name="os-specific-instructions"></a>Istruzioni specifiche del sistema operativo

* [Eseguire l'installazione in Windows](../install/deploy-install-azdata-installer.md)
* [Eseguire l'installazione in macOS](../install/deploy-install-azdata-macos.md)
* Eseguire l'installazione in Linux o nel [sottosistema Windows per Linux (WSL)](/windows/wsl/about/)
   * [Eseguire l'installazione con APT in Debian o Ubuntu](../install/deploy-install-azdata-linux-package.md)
   * [Eseguire l'installazione con yum in RHEL o CentOS](../install/deploy-install-azdata-yum.md)
   * [Eseguire l'installazione con Zypper in openSUSE o SLE](../install/deploy-install-azdata-zypper.md)
   * [Eseguire l'installazione da script](../install/deploy-install-azdata-pip.md)

[!INCLUDE [azdata-package-installation-remove-pip-install](../../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="next-steps"></a>Passaggi successivi

Per informazioni sull'utilizzo dei cluster Big Data, vedere [Che cosa sono i [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]?](../../big-data-cluster/big-data-cluster-overview.md).

Usare azdata con i [servizi dati con abilitazione di Azure Arc](/azure/azure-arc/data/)
