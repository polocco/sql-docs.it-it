---
title: IServerVirtualDeviceSet2::ExecuteCompletionAgent
titlesuffix: SQL Server VDI reference
description: Questo articolo include informazioni di riferimento sul comando IServerVirtualDeviceSet2::ExecuteCompletionAgent.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 067767ebc40ef44b70a09a7f15872ea0fcdce5ba
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2020
ms.locfileid: "85894006"
---
# <a name="iservervirtualdeviceset2executecompletionagent-vdi"></a>IServerVirtualDeviceSet2::ExecuteCompletionAgent (VDI)

[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

La funzione **ExecuteCompletionAgent** viene usata per implementare il ciclo principale dell'agente di completamento.

## <a name="syntax"></a>Sintassi

```c
HRESULT IServerVirtualDeviceSet2::ExecuteCompletionAgent ();
```

## <a name="return-value"></a>Valore restituito

Restituisce un *HRESULT* che indica l'esito positivo o negativo della chiamata al metodo. Il valore NOERROR indica l'esito positivo della chiamata del metodo. Un valore diverso da zero indica che si è verificato un errore.

## <a name="remarks"></a>Osservazioni

L'agente di completamento fornisce un meccanismo tramite il quale SQL Server può sincronizzarsi con i completamenti dei comandi del dispositivo virtuale. Deve essere attivo prima che sia possibile inviare comandi e deve rimanere attivo fino alla chiusura di tutti i dispositivi.

Poiché SQL Server potrebbe dover eseguire un'inizializzazione speciale dei thread, questa interfaccia non avvia un nuovo thread di controllo. Al contrario, SQL Server configura un thread e quindi passa il controllo a questa routine. Il thread deve essere bloccabile nei meccanismi di comunicazione interprocesso (IPC) di Windows NT e in grado di chiamare qualsiasi funzione di callback fornita con i comandi inviati tramite IServerVirtualDevice::SendCommand.

Questa funzione non restituirà il controllo fino a quando non viene richiamato IServerVirtualDeviceSet2::Close o SignalAbort.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni, vedere [Informazioni di riferimento sull'interfaccia dispositivo virtuale di SQL Server](reference-virtual-device-interface.md).