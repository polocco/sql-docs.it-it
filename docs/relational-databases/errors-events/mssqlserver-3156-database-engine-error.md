---
description: MSSQLSERVER_3156
title: MSSQLSERVER_3156 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3156 (Database Engine error)
ms.assetid: 345d8ed4-177e-4ec3-bab3-25d30000e323
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2fb5d71825e138c44cb0e7e756548fd610bbca73
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424353"
---
# <a name="mssqlserver_3156"></a>MSSQLSERVER_3156
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Dettagli  
  
| Attributo | valore |  
| :-------- | :---- |  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|3156|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|LDDB_CANT_WRITE|  
|Testo del messaggio|Impossibile ripristinare il file '%ls' in '%ls'. Utilizzare WITH MOVE per identificare un percorso valido per il file.|  
  
## <a name="explanation"></a>Spiegazione  
Questo messaggio generico identifica i nomi file logici o fisici dei file di cui è non stato possibile eseguire il ripristino a causa di un problema relativo al percorso specificato.  
  
### <a name="possible-causes"></a>Possibili cause  
Tra le cause possibili sono incluse le seguenti:  
  
-   Potrebbe essere necessario l'accesso alla directory di Windows specificata.  
  
-   Il percorso potrebbe essere stato digitato in modo non corretto oppure è possibile che il percorso specificato non esista.  
  
-   Il nome file potrebbe essere utilizzato da un file che non può essere sovrascritto.  
  
## <a name="user-action"></a>Azione dell'utente  
Esaminare i log degli errori alla ricerca di altri messaggi contenenti ulteriori dettagli.  
  
Correggere il problema relativo al percorso specificato, ad esempio concedendo l'accesso, oppure utilizzare l'opzione WITH MOVE nell'istruzione RESTORE per rilocare il file.  
  
## <a name="see-also"></a>Vedere anche  
[Ripristinare un database in una nuova posizione &#40;SQL Server&#41;](~/relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)  
[Ripristino dei file in una nuova posizione &#40;SQL Server&#41;](~/relational-databases/backup-restore/restore-files-to-a-new-location-sql-server.md)  
[RESTORE &#40;Transact-SQL&#41;](~/t-sql/statements/restore-statements-transact-sql.md)  
  
