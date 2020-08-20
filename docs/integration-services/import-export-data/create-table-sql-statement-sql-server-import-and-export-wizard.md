---
description: Istruzione SQL CREATE TABLE (Importazione/Esportazione guidata SQL Server)
title: Istruzione SQL CREATE TABLE (Importazione/Esportazione guidata SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 02/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.impexpwizard.createtablesql.f1
ms.assetid: 0d6f6b3b-d023-4770-a8a9-65b2977c8d05
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7854a8121c16d263da900ffc3f8475a4fe4dddff
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88484135"
---
# <a name="create-table-sql-statement-sql-server-import-and-export-wizard"></a>Istruzione SQL CREATE TABLE (Importazione/Esportazione guidata SQL Server)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


Se nella finestra di dialogo **Mapping colonne** si seleziona **Crea tabella di destinazione** e quindi **Modifica codice SQL** , l'Importazione/Esportazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] visualizza la finestra di dialogo **Istruzione SQL CREATE TABLE** . In questa pagina è necessario esaminare ed eventualmente personalizzare il comando **CREATE TABLE** che verrà eseguito dalla procedura guidata per creare la nuova tabella di destinazione.
  
> [!NOTE]
> Per maggiori informazioni sull'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TABLE e non sulla finestra di dialogo **Istruzione SQL CREATE TABLE** dell'Importazione/Esportazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md). 
  
## <a name="screen-shot-of-the-create-table-sql-statement-page"></a>Screenshot della pagina Istruzione SQL CREATE TABLE  
 L'immagine riportata di seguito illustra la finestra di dialogo **Istruzione SQL CREATE TABLE** della procedura guidata.
 
In questo esempio, la finestra di dialogo **Istruzione SQL** contiene l'istruzione **CREATE TABLE** predefinita generata dalla procedura guidata. Questa istruzione crea una nuova tabella di destinazione, denominata **Person.AddressNew**, che è una copia della tabella di origine **Person.Address**. 
  
 ![Pagina per la creazione di una tabella dell'Importazione/Esportazione guidata](../../integration-services/import-export-data/media/create-table.png "Pagina per la creazione di una tabella dell'Importazione/Esportazione guidata")  
  
## <a name="review-or-regenerate-the-create-table-statement"></a>Rivedere o rigenerare l'istruzione CREATE TABLE  
 **Istruzione SQL**  
Consente di visualizzare l'istruzione SQL generata automaticamente ed eventualmente di personalizzarla.
 
Se si vuole modificare il comando CREATE TABLE predefinito, è possibile che sia necessario apportare modifiche anche ai mapping delle colonne associate quando si torna nella finestra di dialogo **Mapping colonne**.  
  
Per includere un ritorno a capo nel testo dell'istruzione SQL, premere CTRL+INVIO. Premere solo INVIO per chiudere la finestra di dialogo.  
  
Per altre informazioni sull'istruzione CREATE TABLE e la relativa sintassi, vedere [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).   
  
 **Genera automaticamente**  
 Il pulsante **Genera automaticamente** consente di ripristinare l'istruzione SQL predefinita, se è stata modificata.  
  
## <a name="create-a-table-that-includes-a-filestream-column"></a>Creare una tabella che include una colonna FILESTREAM  
 L'Importazione/Esportazione guidata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] genera un'istruzione CREATE TABLE predefinita basata sull'origine dati connessa. Questa istruzione CREATE TABLE predefinita non include l'attributo FILESTREAM anche se la tabella di origine include una colonna FILESTREAM.
 1.  Prima di copiare una colonna FILESTREAM tramite la procedura guidata, implementare l'archiviazione di FILESTREAM nel database di destinazione.
 2.  Aggiungere quindi manualmente l'attributo FILESTREAM all'istruzione CREATE TABLE nella finestra di dialogo **Istruzione SQL CREATE TABLE** .  

Per altre informazioni sulla sintassi, vedere [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md). Per altre informazioni su FILESTREAM, vedere [Dati BLOB &#40;Binary Large Object&#41; &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
## <a name="whats-next"></a>Passaggi successivi  
 Dopo aver rivisto e personalizzato il comando CREATE TABLE e fatto clic su **OK**, dalla finestra di dialogo **Istruzione SQL CREATE TABLE** si torna alla finestra di dialogo **Mapping colonne** . Per altre informazioni, vedere [Mapping colonne](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md).
 
 ## <a name="see-also"></a>Vedere anche
[Iniziare con questo semplice esempio dell'Importazione/Esportazione guidata](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)


