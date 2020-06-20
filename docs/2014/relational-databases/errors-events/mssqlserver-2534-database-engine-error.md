---
title: MSSQLSERVER_2534 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2534 (Database Engine error)
ms.assetid: 121cf99d-0722-494c-be24-3369c1a0badc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: af86c3453edc2d18eb11e0cd58b3c677e69dc468
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054155"
---
# <a name="mssqlserver_2534"></a>MSSQLSERVER_2534
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|2534|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC_PAGE_ALLOCATED_TO_OTHER_OBJECT|  
|Testo del messaggio|Errore di tabella: la pagina P_ID, la cui intestazione indica che è allocata all'ID di oggetto ID O_ID, con ID di indice I_ID, ID di partizione PN_ID e ID di unità di allocazione ID A_ID (tipo TYPE), è allocata da un altro oggetto.|  
  
## <a name="explanation"></a>Spiegazione  
 L'intestazione della pagina contiene l'ID di unità di allocazione *A_ID*, ma nessuna delle pagine della mappa di allocazione degli indici (IAM, Index Allocation Map) relativa a tale unità di allocazione alloca la pagina. L'intestazione della pagina contiene pertanto l'ID di unità di allocazione errato e la pagina restituirà un corrispondente errore MSSQLServer_2533 in cui viene indicato l'ID di unità di allocazione a cui la pagina è effettivamente allocata.  
  
## <a name="user-action"></a>Azione dell'utente  
  
### <a name="look-for-hardware-failure"></a>Individuare errori hardware  
 Eseguire gli strumenti di diagnostica hardware e risolvere eventuali problemi. Esaminare inoltre il registro di sistema di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows e il registro delle applicazioni, nonché il log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per stabilire se l'errore è dovuto a un problema hardware. Risolvere tutti i problemi relativi all'hardware indicati nei log.  
  
 In caso di problemi persistenti che provocano il danneggiamento dei dati, provare a sostituire i vari componenti hardware per isolare il problema. Verificare che nel sistema non sia abilitata la memorizzazione nella cache in scrittura sul controller del disco. Se si ritiene che il problema sia dovuto alla memorizzazione nella cache in scrittura, rivolgersi al fornitore dell'hardware.  
  
 Infine, potrebbe essere conveniente passare a un nuovo sistema hardware. A tale scopo può essere necessario riformattare le unità disco e reinstallare il sistema operativo.  
  
### <a name="restore-from-backup"></a>Eseguire un ripristino da backup  
 Se il problema non è correlato all'hardware ed è disponibile un backup valido noto, ripristinare il database dal backup.  
  
### <a name="run-dbcc-checkdb"></a>Eseguire DBCC CHECKDB  
 Se non è disponibile un backup valido, eseguire DBCC CHECKDB senza la clausola REPAIR per determinare l'entità del danno. Verrà automaticamente suggerita la clausola REPAIR da usare. Eseguire quindi DBCC CHECKDB con la clausola REPAIR appropriata per correggere il database.  
  
> [!CAUTION]  
>  Se non si è certi dell'effetto prodotto sui dati dall'esecuzione di DBCC CHECKDB con la clausola REPAIR, contattare il personale del supporto tecnico prima di eseguire l'istruzione.  
  
 Se l'esecuzione di DBCC CHECKDB con una clausola REPAIR non consente di risolvere il problema, contattare il personale del supporto tecnico.  
  
### <a name="results-of-running-repair-options"></a>Risultati dell'esecuzione delle opzioni REPAIR  
 L'istruzione REPAIR ricompila l'indice se esistente.  
  
> [!CAUTION]  
>  L'esecuzione di REPAIR per l'errore [MSSQLSERVER_2533](mssqlserver-2533-database-engine-error.md) corrispondente dealloca la pagina prima della ricompilazione.  
  
> [!CAUTION]  
>  L'operazione di correzione può comportare la perdita di dati.  
  
  
