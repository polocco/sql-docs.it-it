---
title: Script e PowerShell con Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services]
- Reporting Services, scripting
- scripting [Reporting Services]
ms.assetid: 1ac2646d-ed5a-4436-b18f-2150c33f3d87
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c5198b614047d36c53cf41a1d82a44f612c62be6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2020
ms.locfileid: "78177103"
---
# <a name="scripting-and-powershell-with-reporting-services"></a>Script e PowerShell con Reporting Services
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] supporta un'ampia gamma di scenari di sviluppo e gestione tramite script, tra cui l'utilità della riga di comando rs.exe, i cmdlet PowerShell per server di report in modalità SharePoint, sfruttando il modello a oggetti [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] da PowerShell per la modalità nativa e SharePoint.

-   Gli amministratori possono scrivere script in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] per automatizzare le procedure di distribuzione e gestione dell'installazione di un server di report. Gli amministratori possono anche generare ed eseguire script [!INCLUDE[tsql](../../includes/tsql-md.md)] che consentono di creare, configurare e aggiornare un database del server di report. Gli amministratori possono anche usare le funzionalità script di registrazione e riproduzione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] per automatizzare le attività di manutenzione di routine.

-   Gli sviluppatori possono creare applicazioni personalizzate che includono script. È possibile eseguire uno script che effettua chiamate al servizio Web ReportServer. Nello script è possibile scrivere quasi tutte le operazioni che si possono scrivere in codice gestito.

-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] supporta lo script .NET [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] come linguaggio di script che può essere elaborato dall'utilità RS.exe, un host di script che viene eseguito nel server di report.

## <a name="reporting-services-sharepoint-mode-powershell-cmdlets-and-samples"></a>Cmdlet ed esempi di PowerShell in modalità SharePoint di Reporting Services
 ![Contenuto correlato di PowerShell](../media/rs-powershellicon.jpg "Contenuto correlato di PowerShell")

 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] include i cmdlet [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] per l'amministrazione del server di report.

-   [PowerShell cmdlets for Reporting Services SharePoint Mode](../powershell-cmdlets-for-reporting-services-sharepoint-mode.md) Sono inclusi gli esempi seguenti:

    -   Creare un proxy e un'applicazione di servizio

    -   Rivedere e aggiornare un'estensione per il recapito

    -   Ottenere e impostare le proprietà del database dell'applicazione Reporting Service, ad esempio timeout database

    -   Elencare le estensioni per i dati

## <a name="reporting-services-object-model-and-powershell-samples"></a>Modello a oggetti di Reporting Services ed esempi di Powershell
 ![Contenuto correlato di PowerShell](../media/rs-powershellicon.jpg "Contenuto correlato di PowerShell")

 Le chiamate del modello a oggetti principale di PowerShell valide in generale per la modalità SharePoint e nativa, ad esempio l'attività di migrazione, l'attività di sottoscrizione ed esempi più correlati per le sottoscrizioni, funzionano in SQL15.

-   [Usare PowerShell per modificare ed elencare i proprietari di sottoscrizioni di Reporting Services ed eseguire una sottoscrizione](../subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).

-   [Usare PowerShell per creare una VM di Azure con un server di report in modalità nativa](https://msdn.microsoft.com/library/azure/dn449661.aspx).

-   Vedere la sezione "Accedere alle classi WMI utilizzando PowerShell" in [Accedere al provider WMI per Reporting Services](access-the-reporting-services-wmi-provider.md).

-   [Come amministrare SSRS con gli script di PowerShell](https://www.sqlshack.com/how-to-administer-sql-server-reporting-services-ssrs-subscriptions-using-powershell/)

## <a name="rsexe-scripting-samples"></a>Esempi di script RS.exe

-   [Esempio Reporting Services script RS. exe per eseguire la migrazione del contenuto tra server di report](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).

-   Per altri esempi di script, applicazioni ed estensioni, vedere gli [esempi di prodotti di Reporting Services di SQL Server](https://go.microsoft.com/fwlink/?LinkId=177889).

## <a name="see-also"></a>Vedere anche
 L' [Utilità rs. exe &#40;SSRS&#41;](rs-exe-utility-ssrs.md) [script di distribuzione e attività amministrative](script-deployment-and-administrative-tasks.md) [con l'utilità rs. exe e il servizio Web](script-with-the-rs-exe-utility-and-the-web-service.md)


