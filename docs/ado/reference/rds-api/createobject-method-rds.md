---
description: Metodo CreateObject (Servizi Desktop remoto)
title: Metodo CreateObject (RDS) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- CreateObject method [ADO]
ms.assetid: dec96be6-0b31-4953-9c9a-e962b5afcd18
author: rothja
ms.author: jroth
ms.openlocfilehash: ae158d217437184be4ead71beeb2d2404248396f
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/05/2020
ms.locfileid: "91722437"
---
# <a name="createobject-method-rds"></a>Metodo CreateObject (Servizi Desktop remoto)
Crea il proxy per l'oggetto business di destinazione e restituisce un puntatore a tale oggetto. Il proxy esegue il marshalling dei dati e li esegue il marshalling sullo Stub lato server per le comunicazioni con l'oggetto business per inviare richieste e dati tramite Internet. Per gli oggetti componente in-process non vengono usati proxy, ma viene fornito solo un puntatore all'oggetto.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server Servizi Desktop remoto non sono più inclusi nel sistema operativo Windows. per altri dettagli, vedere le informazioni di riferimento sulla compatibilità di Windows 8 e [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) . I componenti client Servizi Desktop remoto verranno rimossi in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano Servizi Desktop remoto devono eseguire la migrazione a [WCF Data Services](/dotnet/framework/wcf/).  
  
## <a name="syntax"></a>Sintassi  
 Remote Data Service supporta i protocolli seguenti: HTTP, HTTPS (HTTP over Secure Socket Layer), DCOM e in-process.  
  
|Protocollo|Sintassi|  
|--------------|------------|  
|HTTP|Set Object = DataSpace. CreateObject ("ProgId", "https \: //awebsrvr")|  
|HTTPS|Set Object = DataSpace. CreateObject ("ProgId", "https \: //awebsrvr")|  
|DCOM|Set object = DataSpace.CreateObject("ProgId", "computername")|  
|In-Process|Set object = DataSpace.CreateObject("ProgId", "")|  
  
## <a name="parameters"></a>Parametri  
 *Object*  
 Variabile oggetto che restituisce un oggetto che corrisponde al tipo specificato in *ProgID*.  
  
 *DataSpace*  
 Variabile oggetto che rappresenta un Servizi Desktop remoto [. Oggetto DataSpace](./dataspace-object-rds.md) utilizzato per creare un'istanza del nuovo oggetto.  
  
 *ProgID*  
 Valore **stringa** che contiene l'identificatore a livello di codice che specifica un oggetto business sul lato server che implementa le regole di business dell'applicazione.  
  
 *awebsrvr* o *nomecomputer*  
 Valore **stringa** che rappresenta un URL che identifica il server Web Internet Information Services (IIS) in cui viene creata un'istanza dell'oggetto business server.  
  
## <a name="remarks"></a>Osservazioni  
 Il *protocollo http* è il protocollo Web standard. *Https* è un protocollo Web protetto. Usare il *protocollo DCOM* quando si esegue una rete locale senza http. Il protocollo *in-process* è una libreria di collegamento dinamico (dll) locale; non usa una rete.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataSpace (Servizi Desktop remoto)](./dataspace-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di oggetto DataFactory, metodo di query e metodo CreateObject (VBScript)](./datafactory-object-query-method-and-createobject-method-example-vbscript.md)   
 [Esempio di oggetto DataSpace e metodo CreateObject (VBScript)](./dataspace-object-and-createobject-method-example-vbscript.md)   
 [Metodo CreateRecordset (Servizi Desktop remoto)](./createrecordset-method-rds.md)