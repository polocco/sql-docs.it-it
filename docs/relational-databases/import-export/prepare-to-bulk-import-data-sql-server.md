---
title: Prepararsi all'importazione bulk dei dati (SQL Server) | Microsoft Docs
description: Per l'importazione bulk di dati da un file di dati, è possibile usare il comando bcp, l'istruzione BULK INSERT o la funzione OPENROWSET (BULK).
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bulk importing [SQL Server], about bulk importing
- BULK INSERT statement, guidelines
- BULK INSERT statement, restrictions
- bcp utility [SQL Server], guidelines
- bcp utility [SQL Server], restrictions
- hidden characters
- OPENROWSET function, BCP guidelines
ms.assetid: a82ef43c-d006-4c71-bfca-f001a3ba1ba0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 997033c334543e26b5f769d31b1816df707a84bf
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85772311"
---
# <a name="prepare-to-bulk-import-data-sql-server"></a>Prepararsi all'importazione bulk dei dati (SQL Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Per importare dati in blocco solo da un file di dati, è possibile usare il comando **bcp** , l'istruzione BULK INSERT o la funzione OPENROWSET (BULK).  
  
> [!NOTE]  
>  È possibile scrivere un'applicazione personalizzata che esegua l'importazione bulk di dati da oggetti diversi da un file di testo. Per importare dati in blocco dai buffer della memoria, usare le estensioni bcp dell'interfaccia API (Application Programming Interface) Native Client (ODBC) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o dell'interfaccia **IRowsetFastLoad** di OLE DB.  Per importare dati in blocco da una tabella dati C#, usare l'API della copia bulk ADO.NET, **SqlBulkCopy**.  
  
> [!NOTE]  
>  L'importazione bulk di dati in una tabella remota non è supportata.  
  
 Quando si esegue un'importazione bulk di dati da un file di dati in un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], attenersi alle linee guida seguenti:  
  
-   Ottenere le autorizzazioni necessarie per l'account utente in uso.  
  
     L'account utente usato per l'esecuzione dell'utilità **bcp**, dell'istruzione BULK INSERT oppure dell'istruzione INSERT ... L'istruzione SELECT * FROM OPENROWSET(BULK...) deve disporre delle autorizzazioni necessarie per la tabella, che vengono assegnate dal proprietario della tabella. Per altre informazioni sulle autorizzazioni necessarie per ogni metodo, vedere [Utilità bcp](../../tools/bcp-utility.md), [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)e [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md).  
  
-   Utilizzare il modello di recupero con registrazione minima delle operazioni bulk.  
  
     Questa linea guida riguarda un database che utilizza il modello di recupero con registrazione completa. Il modello di recupero con registrazione minima delle operazioni bulk risulta utile quando si eseguono operazioni bulk in una tabella non indicizzata (un *heap*). L'utilizzo del recupero con registrazione minima delle operazioni bulk consente di evitare i problemi di esaurimento dello spazio da parte del log delle transazioni in quanto questo tipo di recupero non inserisce righe nel log. Per altre informazioni sul modello di recupero con registrazione minima delle operazioni bulk, vedere [Modelli di recupero &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md).  
  
     È consigliabile modificare il database in modo da utilizzare il modello di recupero con registrazione minima delle operazioni bulk immediatamente prima dell'operazione di importazione bulk. Appena terminata l'operazione, reimpostare il modello di recupero con registrazione completa. Per altre informazioni, vedere [Visualizzazione o modifica del modello di recupero di un database &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md).  
  
    > [!NOTE]  
    >  Per altre informazioni sulla limitazione della registrazione durante le operazioni di importazione in blocco, vedere [Prerequisiti per la registrazione minima nell'importazione in blocco](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md).  
  
-   Eseguire il backup dopo l'importazione bulk dei dati.  
  
     Per un database che utilizza il modello di recupero con registrazione minima, è consigliabile eseguire un backup completo o differenziale al termine dell'operazione di importazione bulk. Per altre informazioni, vedere [Creare un backup completo del database &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md) o [Creare un backup differenziale del database &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md).  
  
     Per il modello di recupero con registrazione minima delle operazioni bulk o con registrazione completa, è sufficiente un backup del log. Per altre informazioni, vedere [Backup di log delle transazioni &#40;SQL Server&#41;](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md).  
  
-   Eliminare gli indici della tabella al fine di migliorare le prestazioni per le importazioni bulk di grandi dimensioni.  
  
     Questa linea guida riguarda i casi in cui viene importata una grande quantità di dati rispetto alla quantità di dati già presente nella tabella. In tal caso, l'eliminazione degli indici della tabella prima dell'operazione di importazione bulk può consentire un notevole miglioramento delle prestazioni.  
  
    > [!NOTE]  
    >  Se si sta caricando una quantità di dati ridotta rispetto a quella già presente nella tabella, l'eliminazione degli indici risulta controproducente. Il tempo necessario per ricompilare gli indici potrebbe essere superiore a quello risparmiato durante l'operazione di importazione bulk.  
  
-   Individuare e rimuovere i caratteri nascosti nel file di dati.  
  
     In molte utilità ed editor di testo vengono visualizzati i caratteri nascosti, che in genere sono presenti nella parte finale del file di dati. Durante un'operazione di importazione bulk, i caratteri nascosti in un file di dati ASCII possono causare problemi che generano un errore di tipo carattere NULL imprevisto. L'individuazione e la rimozione di tutti i caratteri nascosti dovrebbero consentire di risolvere questo problema.  
  
## <a name="see-also"></a>Vedere anche  
 [Importare ed esportare dati per operazioni bulk usando l'utilità bcp &#40;SQL Server&#41;](../../relational-databases/import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)   
 [Importazione di dati per operazioni bulk utilizzando BULK INSERT o OPENROWSET&#40;BULK...&#41; &#40;SQL Server&#41;](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)   
 [Utilità bcp](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [Formati di dati per l'importazione o l'esportazione bulk &#40;SQL Server&#41;](../../relational-databases/import-export/data-formats-for-bulk-import-or-bulk-export-sql-server.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)  
  
  
