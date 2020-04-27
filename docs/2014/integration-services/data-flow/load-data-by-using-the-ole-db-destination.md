---
title: Caricare dati tramite la destinazione OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- loading data
- OLE DB destination [Integration Services]
- destinations [Integration Services], OLE DB
ms.assetid: 78899498-725e-4300-a7af-f983f4ea384b
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 114460af84d4e820ccd263fc4bf5188b65775c85
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62902433"
---
# <a name="load-data-by-using-the-ole-db-destination"></a>Caricamento dei dati tramite la destinazione OLE DB
  È possibile aggiungere e configurare una destinazione OLE DB solo se il pacchetto include già almeno un'attività Flusso di dati e un'origine.  
  
### <a name="to-load-data-using-an-ole-db-destination"></a>Per caricare dati tramite una destinazione OLE DB  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  Fare clic sulla scheda **Flusso di dati** e quindi, dalla **Casella degli strumenti**, trascinare la destinazione OLE DB sull'area di progettazione.  
  
4.  Connettere la destinazione OLE DB al flusso di dati trascinando un connettore da un'origine dati o una trasformazione precedente alla destinazione.  
  
5.  Fare doppio clic sulla destinazione OLE DB.  
  
6.  Nella pagina **Gestione connessione** della finestra di dialogo **Editor destinazione OLE DB** selezionare una gestione connessione OLE DB esistente oppure fare clic su **Nuova** per creare una nuova gestione connessione. Per altre informazioni, vedere [Gestione connessione OLE DB](../connection-manager/ole-db-connection-manager.md).  
  
7.  Selezionare il metodo di accesso ai dati:  
  
    -   **Tabella o vista** Selezionare una tabella o una vista nel database che contiene i dati.  
  
    -   **Tabella o vista - Caricamento rapido** Selezionare una tabella o una vista nel database che contiene i dati e quindi impostare le opzioni relative al caricamento rapido: **Mantieni valori Identity**, **Mantieni valori Null**, **Blocco di tabella**, **Verifica vincoli**, **Righe per batch**o **Dimensioni massime commit inserimento**.  
  
    -   **Variabile nome vista o nome tabella** Selezionare una variabile definita dall'utente contenente il nome di una tabella o vista del database.  
  
    -   **Variabile nome vista o nome tabella - Caricamento rapido** Selezionare la variabile definita dall'utente contenente il nome di una tabella o vista del database che contiene i dati e quindi impostare le opzioni relative al caricamento rapido.  
  
    -   **Comando SQL** Digitare un comando SQL oppure fare clic su **Compila query** per scrivere un comando SQL utilizzando **Generatore query**.  
  
8.  Fare clic su **Mapping** e quindi eseguire il mapping delle colonne nell'elenco **Colonne di input disponibili** alle colonne nell'elenco **Colonne di destinazione disponibili** , trascinando le colonne da un elenco all'altro.  
  
    > [!NOTE]  
    >  La destinazione OLE DB esegue automaticamente il mapping delle colonne con lo stesso nome.  
  
9. Per configurare l'output degli errori, fare clic su **Output errori**. Per altre informazioni, vedere [Configurazione di un output degli errori in un componente del flusso di dati](../configure-an-error-output-in-a-data-flow-component.md).  
  
10. Fare clic su **OK**.  
  
11. Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
## <a name="see-also"></a>Vedere anche  
 [Destinazione OLE DB](ole-db-destination.md)   
 [Trasformazioni di Integration Services](transformations/integration-services-transformations.md)   
 [Percorsi in Integration Services](integration-services-paths.md)   
 [Attività Flusso di dati](../control-flow/data-flow-task.md)  
  
  
