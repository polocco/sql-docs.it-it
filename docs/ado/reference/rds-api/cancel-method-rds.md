---
description: Metodo Cancel (Servizi Desktop remoto)
title: Metodo Cancel (RDS) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Cancel method [RDS]
ms.assetid: 560b5b3d-fba9-4275-8920-9c3e186134f7
author: rothja
ms.author: jroth
ms.openlocfilehash: 24f72c16e1c27d070bcc52fc29c6599cc11c737e
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/05/2020
ms.locfileid: "91722692"
---
# <a name="cancel-method-rds"></a>Metodo Cancel (Servizi Desktop remoto)
Annulla l'esecuzione di una chiamata al metodo asincrona in sospeso.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server Servizi Desktop remoto non sono più inclusi nel sistema operativo Windows. per altri dettagli, vedere le informazioni di riferimento sulla compatibilità di Windows 8 e [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) . I componenti client Servizi Desktop remoto verranno rimossi in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano Servizi Desktop remoto devono eseguire la migrazione a [WCF Data Services](/dotnet/framework/wcf/).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RDS.DataControl.Cancel  
```  
  
## <a name="remarks"></a>Osservazioni  
 Quando si chiama **Annulla**, [ReadyState](./readystate-property-rds.md) viene impostato automaticamente su **adcReadyStateLoaded**e il [Recordset](../ado-api/recordset-object-ado.md) sarà vuoto.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (Servizi Desktop remoto)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodo Cancel (VBScript)](./cancel-method-example-vbscript.md)   
 [Metodo Cancel (ADO)](../ado-api/cancel-method-ado.md)   
 [Metodo CancelBatch (ADO)](../ado-api/cancelbatch-method-ado.md)   
 [Metodo CancelUpdate (ADO)](../ado-api/cancelupdate-method-ado.md)   
 [Metodo CancelUpdate (RDS)](./cancelupdate-method-rds.md)   
 [Proprietà ExecuteOptions (Servizi Desktop remoto)](./executeoptions-property-rds.md)