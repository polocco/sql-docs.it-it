---
title: Installare SQL Server PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 854c0b2f-02d2-46a4-a8cc-6b7a5d191cf8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a90a30a0ae7fe09d49b1d42b577b13370c48c0de
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62775441"
---
# <a name="install-sql-server-powershell"></a>Installare SQL Server PowerShell
  Il programma di installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene arrestato se viene rilevato che sono state selezionate funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che includono componenti di PowerShell, ma che Windows PowerShell 2.0 non è installato. È necessario installare PowerShell tramite Windows Management Framework, quindi rieseguire l'installazione.  
  
## <a name="installing-ssnoversion-powershell-support"></a>Installazione del supporto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell  
 Per installare il software che fornisce il supporto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per Windows PowerShell utilizzare l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Quando si seleziona qualsiasi funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che richiede il supporto di PowerShell, l'installazione controlla che sia stato installato Windows PowerShell 2.0. Se PowerShell 2.0 è presente, vengono installati i seguenti componenti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di PowerShell:  
  
-   Gli [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] snap-in di PowerShell. Gli snap-in sono file dll che implementano due tipi di supporto di Windows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]PowerShell per:  
  
    -   Set di cmdlet di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . I cmdlet sono comandi che implementano un'azione specifica, ad esempio **Invoke-Sqlcmd** esegue uno script [!INCLUDE[tsql](../../includes/tsql-md.md)] o XQuery che può essere eseguito anche con l'utilità **sqlcmd** , mentre **Invoke-PolicyEvaluation** segnala se gli oggetti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono conformi ai criteri di gestione basata su criteri.  
  
    -   Provider di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Il provider consente di spostarsi nella gerarchia degli oggetti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando un percorso simile a un percorso del file system. Ciascun oggetto è associato a una classe dei modelli SMO ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects). È possibile utilizzare i metodi e le proprietà della classe per eseguire azioni sugli oggetti. Utilizzando il comando cd per un oggetto di database in un percorso, ad esempio, è possibile utilizzare i metodi e le proprietà della classe Microsoft.SqlServer.Management.SMO.Database per gestire il database.  
  
-   Il modulo **sqlps** importato nelle sessioni di Windows PowerShell 2,0 per caricare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gli snap-in.  
  
-   L'utilità **sqlps** deprecata che avvia una sessione di Windows PowerShell 2,0 e importa il modulo **sqlps** .  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] supporta l'avvio delle sessioni di Windows PowerShell dall'albero di Esplora oggetti. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent supporta i passaggi del processo di Windows PowerShell.  
  
 Se Windows PowerShell 2,0 non è stato installato o è stato disinstallato, è necessario installarlo seguendo le istruzioni disponibili nella pagina relativa a [Windows Management Framework](https://go.microsoft.com/fwlink/?LinkId=186214) .  
  
 Se Windows PowerShell viene disinstallato al termine dell'installazione, non sarà possibile utilizzare le funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per Windows PowerShell. Windows PowerShell può essere disinstallato dagli utenti di Windows. La disinstallazione di Windows PowerShell potrebbe inoltre essere necessaria per eseguire alcuni aggiornamenti del sistema operativo Windows. Per utilizzare le funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell è necessario reinstallare PowerShell 2.0 tramite Windows Management Framework.  
  
## <a name="see-also"></a>Vedi anche  
 [SQL Server PowerShell](../../powershell/sql-server-powershell.md)  
  
  
