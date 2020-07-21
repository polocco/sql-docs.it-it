---
title: MSSQLSERVER_905 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 905 (Database Engine error)
ms.assetid: c828bb2e-e554-4f81-b76c-2b3740d2b944
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2db51e80ebe7df5f8793dba3b2c09e2afc199b59
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553116"
---
# <a name="mssqlserver_905"></a>MSSQLSERVER_905
    
## <a name="details"></a>Dettagli  
  
|Attributo|valore|  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|905|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBSTARTUP_EE_PARTITIONING|  
|Testo del messaggio|Impossibile avviare il database '%.*ls' in questa edizione di SQL Server, perché contiene la funzione di partizione '%.\*ls'. Il partizionamento è supportato solo in SQL Server Enterprise Edition.|  
  
## <a name="explanation"></a>Spiegazione  
 Il database contiene uno o più tabelle o indici partizionati. Il partizionamento non è supportato in questa edizione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il database non può pertanto essere avviato in modo corretto. Le tabelle e gli indici partizionati sono disponibili solo in alcune edizioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="user-action"></a>Azione dell'utente  
 Scollegare il database utilizzando la stored procedure sp_detach_db. Se necessario, spostare i file, quindi collegare il database a un'istanza di un'edizione supportata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando CREATE DATABASE con l'opzione FOR ATTACH o FOR ATTACH_REBUILD_LOG. Disabilitare il partizionamento in tutte le tabelle e rimuovere le funzioni di partizionamento. Scollegare di nuovo il database e ricollegarlo al server corrente.  
  
  
