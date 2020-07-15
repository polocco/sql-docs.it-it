---
title: Attività Pulizia file manutenzione (Piano di manutenzione) | Microsoft Docs
description: Informazioni su come rimuovere file obsoleti per i piani di manutenzione, inclusi i report in formato testo per i piani di manutenzione e i file di backup del database usando l'attività Pulizia file manutenzione.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql13.swb.maint.cleanup.f1
helpviewer_keywords:
- Maintenance Cleanup Task dialog box
ms.assetid: 022b679c-6799-4c13-9185-814224a20412
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b7e01cbee4a518b7b2f6b9ef9dea783f1a6ce24d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85666969"
---
# <a name="maintenance-cleanup-task-maintenance-plan"></a>Attività Pulizia file manutenzione (Piano di manutenzione)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Usare l' **Attività Pulizia file di manutenzione** per rimuovere file obsoleti correlati ai piani di manutenzione, inclusi i report in formato testo creati dai piani di manutenzione e i file di backup del database.  
  
> [!NOTE]  
>  L'attività Pulizia file manutenzione non elimina automaticamente i file nelle sottocartelle della directory specificata. Questa caratteristica riduce la possibilità di un attacco dannoso che utilizzi l'attività Pulizia file manutenzione per eliminare i file. Per eliminare i file nelle sottocartelle di primo livello è necessario selezionare **Includi sottocartelle di primo livello**.  
  
## <a name="options"></a>Opzioni  
 **Connection**  
 Consente di visualizzare la connessione corrente.  
  
 **Nuovo**  
 Consente di creare una nuova connessione server da utilizzare per l'esecuzione dell'attività. La finestra di dialogo **Nuova connessione** è descritta di seguito.  
  
 **File di backup**  
 Consente di eliminare i file di backup.  
  
 **Report in formato testo piano di manutenzione**  
 Elimina i report in formato testo relativi a piani di manutenzione eseguiti in precedenza.  
  
 **Elimina file specifico**  
 Consente di eliminare il file specifico indicato nella casella **Nome file** .  
  
 **Nome file**  
 Percorso e nome del file da eliminare.  
  
 **Cerca nella cartella ed elimina i file in base all'estensione**  
 Consente di eliminare tutti i file con l'estensione specificata contenuti nella cartella indicata. Utilizzare questa opzione per eliminare più file contemporaneamente, ad esempio tutti i file di backup con estensione bak contenuti nella cartella specificata.  
  
 **Cartella**  
 Percorso e nome della cartella contenente i file da eliminare.  
  
 **Estensione file**  
 Indica l'estensione del file da eliminare. Non includere altri caratteri prima o dopo l'estensione (ad esempio, BAK o TRN). 
  
 **Includi sottocartelle di primo livello**  
 Consente di eliminare i file con l'estensione specificata in **Estensione file** dalle sottocartelle di primo livello in **Cartella**.  
  
 **Elimina i file in base alla data del file al momento dell'esecuzione dell'attività**  
 Specificare il periodo di memorizzazione minimo trascorso il quale i file verranno eliminati, indicando un numero e un'unità di tempo nella casella **Elimina i file con data anteriore a** .  
  
 **Elimina i file con data anteriore a**  
 Consente di specificare la data minima dei file da eliminare indicando un numero e un'unità di tempo (giorno/i, settimana/e, mese/i o anno/i). I file con data anteriore alla data specificata verranno eliminati.  
  
 **Visualizza codice T-SQL**  
 Consente di visualizzare le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] eseguite sul server per questa attività, in base alle opzioni selezionate.  
  
> [!NOTE]  
>  Se il numero di oggetti interessato dall'attività è elevato, la visualizzazione del codice potrebbe richiedere una considerevole quantità di tempo.  
  
## <a name="new-connection-dialog-box"></a>Finestra di dialogo Nuova connessione  
 **Nome connessione**  
 Consente di immettere un nome per la nuova connessione.  
  
 **Selezionare o immettere il nome di un server**  
 Consente di selezionare il server a cui connettersi per l'esecuzione dell'attività.  
  
 **...**  
 Consente di visualizzare l'elenco dei server disponibili.  
  
 **Immettere le informazioni per l'accesso al server**  
 Consente di specificare le opzioni di autenticazione per l'accesso al server.  
  
 **Usa la sicurezza integrata di Windows NT**  
 Consente di connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] utilizzando l'autenticazione di Microsoft Windows.  
  
 **Usa nome utente e password specifici**  
 Consente di connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] utilizzando l'autenticazione di SQL Server. Questa opzione non è disponibile.  
  
 **Nome utente**  
 Consente di specificare un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da utilizzare per l'autenticazione. Questa opzione non è disponibile.  
  
 **Password**  
 Consente di specificare una password da utilizzare per l'autenticazione. Questa opzione non è disponibile.  
  
## <a name="see-also"></a>Vedere anche  
 [Piani di manutenzione](../../relational-databases/maintenance-plans/maintenance-plans.md)  
  
  
