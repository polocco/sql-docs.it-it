---
title: Eseguire operazioni online sugli indici | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index online operations [SQL Server]
- online index operations
- ONLINE option
ms.assetid: 1e43537c-bf67-4db3-9908-3cb45c6fdaa1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4d09bd99a0eaec5fdb433bd8c33351d7622957a2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85049873"
---
# <a name="perform-index-operations-online"></a>Eseguire operazioni online sugli indici
  In questo argomento si illustra come creare, ricompilare o eliminare gli indici online in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. L'opzione ONLINE consente l'accesso simultaneo degli utenti alla tabella sottostante o ai dati dell'indice cluster e a qualsiasi indice non cluster associato durante l'esecuzione di queste operazioni sugli indici. Durante la ricompilazione di un indice cluster da parte di un utente, ad esempio, tale utente e altri utenti possono continuare ad aggiornare ed eseguire query sui dati sottostanti. Quando si eseguono operazioni DDL (Data Definition Language) offline, ad esempio la compilazione o la ricompilazione di un indice cluster, tali operazioni mantengono blocchi esclusivi sui dati sottostanti e gli indici associati. Questo comportamento impedisce modifiche e query nei dati sottostanti fino al termine dell'operazione sull'indice.  
  
> [!NOTE]  
>  Le operazioni sugli indici online sono disponibili solo in alcune edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Per ulteriori informazioni, vedere [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 **Contenuto dell'articolo**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Sicurezza](#Security)  
  
-   **Per ricompilare un indice online tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   È consigliabile eseguire operazioni online sugli indici per ambiti aziendali in funzione 24 ore al giorno e sette giorni su sette, in cui l'esigenza di attività simultanee durante le operazioni sugli indici rappresenta un elemento essenziale.  
  
-   L'opzione ONLINE è disponibile nelle istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] seguenti.  
  
    -   [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql)  
  
    -   [ALTER INDEX](/sql/t-sql/statements/alter-index-transact-sql)  
  
    -   [DROP INDEX](/sql/t-sql/statements/drop-index-transact-sql)  
  
    -   [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) (per aggiungere o eliminare vincoli UNIQUE o PRIMARY KEY con l'opzione di indice CLUSTERED)  
  
-   Per altre limitazioni e restrizioni relative alla creazione, alla ricompilazione o all'eliminazione degli indici online, vedere [Linee guida per le operazioni di indice online](guidelines-for-online-index-operations.md).  
  
###  <a name="security"></a><a name="Security"></a> Sicurezza  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorizzazioni  
 È richiesta l'autorizzazione ALTER per la tabella o la vista.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Con SQL Server Management Studio  
  
#### <a name="to-rebuild-an-index-online"></a>Per ricompilare un indice online  
  
1.  In Esplora oggetti fare clic sul segno più per espandere il database contenente la tabella in cui si desidera ricompilare un indice online.  
  
2.  Espandere la cartella **Tabelle** .  
  
3.  Fare clic sul segno più per espandere la tabella in cui si desidera ricompilare un indice online.  
  
4.  Espandere la cartella **Indici** .  
  
5.  Fare clic con il pulsante destro del mouse sull'indice da ricompilare online e selezionare **Proprietà**.  
  
6.  In **Selezione pagina**selezionare **Opzioni**.  
  
7.  Selezionare **Consenti elaborazione DML online**, quindi selezionare **True** dall'elenco.  
  
8.  Fare clic su **OK**.  
  
9. Fare clic con il pulsante destro del mouse sull'indice da ricompilare online e selezionare **Ricompila**.  
  
10. Nella finestra di dialogo **Ricompila indici** verificare che nella griglia **Indici da ricompilare** sia presente l'indice corretto e fare clic su **OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Con Transact-SQL  
  
#### <a name="to-create-rebuild-or-drop-an-index-online"></a>Per creare, ricompilare o eliminare un indice online  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. Nell'esempio viene ricompilato un indice online esistente  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER INDEX AK_Employee_NationalIDNumber ON HumanResources.Employee  
    REBUILD WITH (ONLINE = ON);  
    GO  
    ```  
  
     Nell'esempio seguente viene eliminato un indice cluster online e la tabella risultante (heap) viene spostata nel filegroup `NewGroup` tramite la clausola `MOVE TO` . Vengono eseguite query sulle viste del catalogo `sys.indexes`, `sys.tables`e `sys.filegroups` per verificare la posizione dell'indice e della tabella nei filegroup prima e dopo lo spostamento.  
  
     [!code-sql[IndexDDL#DropIndex4](../../snippets/tsql/SQL14/tsql/indexddl/transact-sql/dropindex.sql#dropindex4)]  
  
 Per altre informazioni, vedere [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql).  
  
  
