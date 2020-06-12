---
title: Spostare un database di Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- moving databases [Anlysis Services]
- moving databases
- operations [Analysis Services - multidimensional data]
ms.assetid: fa644e5d-e276-445e-98d9-673afcfb83fe
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4f10901625ece0a154248f99370e427c7a999c87
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546063"
---
# <a name="move-an-analysis-services-database"></a>Spostare un database di Analysis Services
  Spesso, un amministratore del database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] desidera spostare un database multidimensionale o tabulare in un percorso diverso. Queste situazioni spesso sono determinate da esigenze aziendali, ad esempio lo spostamento del database in un disco diverso per migliorare le prestazioni, la necessità di ottenere più spazio per la crescita del database oppure per aggiornare un prodotto.  
  
 Un database può essere spostato in vari modi. In questo documento vengono illustrati gli scenari comuni seguenti:  
  
-   In modo interattivo tramite SSMS  
  
-   A livello di programmazione tramite AMO  
  
-   Tramite script utilizzando XMLA  
  
 Tutti gli scenari richiedono all'utente di accedere alla cartella del database e utilizzare un metodo per lo spostamento dei file nella destinazione finale desiderata.  
  
> [!NOTE]  
>  Lo scollegamento di un database senza l'assegnazione di una password lascia il database in uno stato non protetto. Si consiglia di assegnare una password al database per proteggere le informazioni riservate. Inoltre, è necessario applicare la sicurezza dall'accesso corrispondente alla cartella del database, alle sottocartelle e ai file per impedire accessi non autorizzati.  
  
## <a name="procedures"></a>Procedure  
  
#### <a name="moving-a-database-interactively-using-ssms"></a>Spostamento di un database in modo interattivo tramite SSMS  
  
1.  Individuare il database da spostare nel riquadro sinistro o destro di SSMS.  
  
2.  Fare clic con il pulsante destro del mouse sul database e selezionare **Disconnetti...**  
  
3.  Assegnare una password al database da scollegare, quindi fare clic su **OK** per eseguire il comando.  
  
4.  Utilizzare un meccanismo del sistema operativo o un metodo standard di spostamento file per spostare la cartella del database nel nuovo percorso.  
  
5.  Individuare la cartella **Database** nel riquadro sinistro o destro di SSMS.  
  
6.  Fare clic con il pulsante destro del mouse sulla cartella **database** e scegliere **Connetti...**  
  
7.  Nella casella di testo **cartella** digitare il nuovo percorso della cartella del database. In alternativa, è possibile utilizzare il pulsante Sfoglia (**...**) per individuare la cartella del database.  
  
8.  Consente di selezionare la `ReadWrite` modalità del database.  
  
9. Digitare la password usata nel passaggio 3, quindi fare clic su **OK** per eseguire il comando di collegamento.  
  
#### <a name="moving-a-database-programmatically-using-amo"></a>Spostamento di un database a livello di programmazione tramite AMO  
  
1.  Nell'applicazione C# adattare il codice di esempio seguente e completare le attività indicate.  
  
 `private void MoveDb(Server server, string dbName,`  
  
 `string dbInitialLocation, string dbFinalLocation,`  
  
 `string dbPassword, ReadWriteMode dbReadWriteMode)`  
  
 `{`  
  
 `//Verify dbInitialLocation exists before continuing`  
  
 `if (server.Databases.ContainsName(dbName))`  
  
 `{`  
  
 `Database db;`  
  
 `//Save current cursor and change cursor to Cursors.WaitCursor`  
  
 `db = server.Databases[dbName];`  
  
 `db.Detach(dbPassword);`  
  
 `//Add your own code to copy the database files to the destination where you intend to attach the database`  
  
 `//Verify dbFinalLocation exists before continuing`  
  
 `server.Attach(dbFinalLocation, dbReadWriteMode, dbPassword);`  
  
 `//Restore cursor to its original`  
  
 `}`  
  
 `}`  
  
1.  Nell'applicazione C# richiamare `MoveDb()` con i parametri necessari.  
  
2.  Compilare ed eseguire il codice per spostare il database.  
  
#### <a name="moving-a-database-by-script-using-xmla"></a>Spostamento di un database tramite script utilizzando XMLA  
  
1.  Aprire una nuova scheda XMLA in SSMS.  
  
2.  Copiare il modello di script seguente per XMLA:  
  
 `<Detach xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">`  
  
 `<Object>`  
  
 `<DatabaseID>%dbName%</DatabaseID>`  
  
 `<Password>%password%</Password>`  
  
 `</Object>`  
  
 `</Detach>`  
  
1.  Sostituire `%dbName%` con il nome del database e `%password%` con la password. I caratteri % fanno parte del modello e devono essere rimossi.  
  
2.  Eseguire il comando XMLA.  
  
3.  Utilizzare un meccanismo del sistema operativo o un metodo standard di spostamento file per spostare la cartella del database nel nuovo percorso.  
  
4.  Copiare il modello di script seguente per XMLA in una nuova scheda XMLA:  
  
 `<Attach xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">`  
  
 `<Folder>%dbFolder%</Folder>`  
  
 `<ReadWriteMode xmlns="https://schemas.microsoft.com/analysisservices/2008/engine/100">%ReadOnlyMode%</ReadWriteMode>`  
  
 `</Attach>`  
  
1.  Sostituire `%dbFolder%` con il percorso completo in formato UNC della cartella del database, `%ReadOnlyMode%` con il valore `ReadOnly` o `ReadWrite` corrispondente e `%password%` con la password. I caratteri % fanno parte del modello e devono essere rimossi.  
  
2.  Eseguire il comando XMLA.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Collegamento e scollegamento di Analysis Services database](attach-and-detach-analysis-services-databases.md)   
 [Percorso di archiviazione del database](database-storage-location.md)   
 [Proprietà ReadWriteMode del database](database-readwritemodes.md)   
 [Connetti elemento](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element)   
 [Scollega elemento](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element)   
 [Elemento ReadWriteMode](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/readwritemode-element)   
 [Elemento DbStorageLocation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/dbstoragelocation-element)  
  
  
