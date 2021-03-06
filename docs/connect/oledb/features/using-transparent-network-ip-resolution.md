---
description: Uso della risoluzione dell'IP di rete trasparente
title: Uso della risoluzione dell'IP di rete trasparente | Microsoft Docs
ms.custom: ''
ms.date: 01/02/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: chris-rossi
ms.author: v-chross
ms.openlocfilehash: adaad0f80d6304c855af22f134d24f0d3f23d301
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88415017"
---
# <a name="using-transparent-network-ip-resolution"></a>Uso della risoluzione dell'IP di rete trasparente
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

## <a name="purpose"></a>Scopo
La risoluzione dell'IP di rete trasparente è una revisione della funzionalità MultiSubnetFailover esistente. Influisce sulla sequenza di connessione del driver quando il primo IP risolto del nome host non risponde e al nome host sono associati più IP. La risoluzione dell'IP di rete trasparente interagisce con MultiSubnetFailover per fornire le tre sequenze di connessione seguenti:<br />
* 0: Viene eseguito un tentativo con un indirizzo IP, seguito da tutti gli indirizzi IP in parallelo
* 1: Viene eseguito un tentativo con tutti gli indirizzi IP in parallelo
* 2: Viene eseguito un tentativo con tutti gli indirizzi IP uno dopo l'altro

|TransparentNetworkIPResolution|MultiSubnetFailover|Comportamento|
|--------|--------|--------|
|True|True|1|
|Vero|Falso|0|
|False|True|1|
|False|False|2|

## <a name="setting-transparent-network-ip-resolution"></a>Impostazione della risoluzione dell'ID di rete trasparente
TransparentNetworkIPResolution è abilitata per impostazione predefinita. MultiSubnetFailover è disabilitata per impostazione predefinita. Le pagine seguenti contengono altre informazioni sull'impostazione di queste proprietà: 
- [Utilizzo delle parole chiave delle stringhe di connessione con driver OLE DB per SQL Server](..\applications\using-connection-string-keywords-with-oledb-driver-for-sql-server.md)
- [Proprietà di inizializzazione e di autorizzazione](..\ole-db-data-source-objects\initialization-and-authorization-properties.md)

## <a name="see-also"></a>Vedere anche 
[Driver OLE DB per il supporto di SQL Server per il ripristino di emergenza a disponibilità elevata](./oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)
