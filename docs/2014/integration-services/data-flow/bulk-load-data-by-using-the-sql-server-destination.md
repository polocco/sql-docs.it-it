---
title: Caricamento bulk dei dati tramite la destinazione SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server destination
- loading data
- destinations [Integration Services], SQL Server
- inserting data
- bulk load [Integration Services]
ms.assetid: 8f982f85-a82e-4e2d-9cd8-cd2f85402d8e
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 7c76318277d718f93bb5d33746a9bf3d62c9bf28
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84916721"
---
# <a name="bulk-load-data-by-using-the-sql-server-destination"></a>Caricamento bulk dei dati tramite la destinazione SQL Server
  È possibile aggiungere e configurare una destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] solo se il pacchetto include già almeno un'attività Flusso di dati e un'origine dati.  
  
### <a name="to-load-data-using-a-sql-server-destination"></a>Per caricare dati tramite una destinazione SQL Server  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  Fare clic sulla scheda **Flusso di dati** e quindi trascinare la destinazione **dalla**casella degli strumenti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] all'area di progettazione.  
  
4.  Connettere la destinazione a un'origine o una trasformazione precedente nel flusso di dati trascinando un connettore fino alla destinazione.  
  
5.  Fare doppio clic sulla destinazione.  
  
6.  Nella pagina **Gestione connessione**della finestra di dialogo **Editor destinazione SQL Server** selezionare una gestione connessione OLE DB esistente oppure fare clic su **Nuova** per creare una nuova gestione connessione. Per altre informazioni, vedere [Gestione connessione OLE DB](../connection-manager/ole-db-connection-manager.md).  
  
7.  Per specificare la tabella o vista in cui caricare i dati, eseguire una delle operazioni seguenti:  
  
    -   Selezionare una tabella o vista esistente.  
  
    -   Fare clic su **Nuovo**e quindi nella finestra di dialogo **Crea tabella** scrivere un'istruzione SQL che crea una tabella o una vista.  
  
        > [!NOTE]  
        >  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] genera un'istruzione CREATE TABLE predefinita basata sull'origine dati connessa. Questa istruzione CREATE TABLE predefinita non includerà l'attributo FILESTREAM anche se la tabella di origine include una colonna con l'attributo FILESTREAM dichiarato. Per eseguire un componente [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] con l'attributo FILESTREAM, implementare innanzitutto l'archiviazione di FILESTREAM nel database di destinazione. Aggiungere quindi l'attributo FILESTREAM all'istruzione CREATE TABLE nella finestra di dialogo **Crea tabella** . Per altre informazioni, vedere [Dati BLOB &#40;Binary Large Object&#41; &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
8.  Fare clic su **Mapping** ed eseguire il mapping delle colonne nell'elenco **Colonne di input disponibili** alle colonne nell'elenco **Colonne di destinazione disponibili** , trascinando le colonne da un elenco all'altro.  
  
    > [!NOTE]  
    >  La destinazione esegue automaticamente il mapping delle colonne con lo stesso nome.  
  
9. Fare clic su **Avanzate** e impostare le opzioni relative al caricamento bulk: **Mantieni valori Identity**, **Mantieni valori Null**, **Blocco di tabella**, **Verifica vincoli**e **Attiva trigger**.  
  
     Facoltativamente, specificare la prima e l'ultima riga di input da inserire, il numero massimo di errori che possono verificarsi prima che l'operazione di inserimento venga arrestata e le colonne in base alle quali viene ordinato l'inserimento.  
  
    > [!NOTE]  
    >  Il tipo di ordinamento è determinato dall'ordine in cui sono elencate le colonne.  
  
10. Fare clic su **OK**.  
  
11. Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Destination](sql-server-destination.md)   
 [Trasformazioni di Integration Services](transformations/integration-services-transformations.md)   
 [Percorsi in Integration Services](integration-services-paths.md)   
 [Attività Flusso di dati](../control-flow/data-flow-task.md)  
  
  
