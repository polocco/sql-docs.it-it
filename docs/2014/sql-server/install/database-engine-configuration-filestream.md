---
title: Configurazione di motore di database-FILESTREAM | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], about FILESTREAM
ms.assetid: 641a10a1-ae52-4d26-8f1c-a032a4aeff02
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ab12b507246a3e13ac59be213813604d531d9a28
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012729"
---
# <a name="database-engine-configuration---filestream"></a>Configurazione del Motore di database - Filestream
  Utilizzare questa pagina per abilitare FILESTREAM per l'installazione corrente di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. FILESTREAM integra [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] con un file system NTFS archiviando `varbinary(max)` dati BLOB (Binary Large Object) come file nel file System. [!INCLUDE[tsql](../../includes/tsql-md.md)] offre istruzioni che consentono di inserire, aggiornare ed eseguire query, ricerche e back up dei dati FILESTREAM. Le interfacce del file system Win32 forniscono accesso ai dati tramite flusso.  
  
## <a name="ui-element-list"></a>Elenco elementi dell'interfaccia utente  
 **Abilita FILESTREAM per l'accesso Transact-SQL**  
 Selezionare questa opzione per abilitare FILESTREAM per l'accesso [!INCLUDE[tsql](../../includes/tsql-md.md)] . È necessario che questo controllo sia selezionato affinché le altre opzioni di controllo siano disponibili.  
  
 **Abilita FILESTREAM per l'accesso tramite il flusso di I/O dei file**  
 Selezionare questa opzione per abilitare l'accesso tramite flusso Win32 per FILESTREAM.  
  
 **Nome condivisione di Windows**  
 Utilizzare questo controllo per immettere il nome della condivisione di Windows in cui verranno archiviati i dati FILESTREAM.  
  
 **Consenti ai client remoti l'accesso tramite flusso ai dati FILESTREAM**  
 Selezionare questo controllo per consentire ai client remoti di accedere ai dati FILESTREAM nel server corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [Abilitare e configurare FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
