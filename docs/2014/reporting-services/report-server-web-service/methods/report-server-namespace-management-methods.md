---
title: Metodi di gestione dello spazio dei nomi del server di report | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- reports [Reporting Services], managing
- management methods [Reporting Services]
- methods [Reporting Services], about methods
- methods [Reporting Services]
ms.assetid: 2aa43ce9-f51e-408a-8ce0-b40d3dd62561
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 64827063e6e406f91307e7db1b33d6b42a196168
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "63283980"
---
# <a name="report-server-namespace-management-methods"></a>Metodi di gestione dello spazio dei nomi del server di report
  Il servizio Web di gestione del server report include metodi che è possibile utilizzare per gestire report, cartelle e risorse nel database del server di report.  
  
|Metodo|Azione|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CancelJob%2A>|Annulla l'esecuzione di un processo.|  
|<xref:ReportService2010.ReportingService2010.CreateFolder%2A>|Aggiunge una cartella al database del server di report o alla raccolta di SharePoint.|  
|<xref:ReportService2010.ReportingService2010.CreateCatalogItem%2A>|Aggiunge un nuovo elemento a un database del server di report o alla raccolta di SharePoint. Questo metodo si applica ai tipi di elemento `Report`, `Model`, `Dataset`, `Component`, `Resource` e `DataSource`.|  
|M:ReportService2010.ReportingService2010.CreateReportEditSession(System.String,System.String,System.Byte[],ReportService2010.Warning[]@)|Crea una nuova sessione di modifica del report.|  
|<xref:ReportService2010.ReportingService2010.DeleteItem%2A>|Rimuove un elemento dal database del server di report o dalla raccolta di SharePoint.|  
|<xref:ReportService2010.ReportingService2010.FindItems%2A>|Restituisce gli elementi nel database del server di report o nella raccolta di SharePoint che corrispondono ai criteri di ricerca specificati.|  
|<xref:ReportService2010.ReportingService2010.FireEvent%2A>|Genera un evento in base ai parametri forniti.|  
|<xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A>|Restituisce un elenco di impostazioni per un'estensione specificata.|  
|<xref:ReportService2010.ReportingService2010.GetItemType%2A>|Recupera il tipo di un elemento nel database del server di report o nella raccolta di SharePoint, se l'elemento esiste.|  
|<xref:ReportService2010.ReportingService2010.GetProperties%2A>|Restituisce i valori di una o più proprietà di un elemento nel database del server di report o in una raccolta di SharePoint.|  
|<xref:ReportService2010.ReportingService2010.GetItemDefinition%2A>|Recupera la definizione o il contenuto per un elemento. Questo metodo si applica ai tipi di elemento `Report`, `Model`, `Dataset`, `Component`, `Resource` e `DataSource`.|  
|<xref:ReportService2010.ReportingService2010.GetItemReferences%2A>|Restituisce un elenco di riferimenti a elementi del catalogo associati a un elemento.|  
|<xref:ReportService2010.ReportingService2010.GetReportServerConfigInfo%2A>|Restituisce informazioni sull'istanza del server di report collegata o su tutte le istanze del server di report in una distribuzione con scalabilità orizzontale.|  
|<xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>|Restituisce una o più proprietà di sistema.|  
|<xref:ReportService2010.ReportingService2010.ListChildren%2A>|Ottiene un elenco di figli di una cartella specificata.|  
|<xref:ReportService2010.ReportingService2010.ListDatabaseCredentialRetrievalOptions%2A>|Restituisce un elenco di opzioni di recupero di credenziale supportate.|  
|<xref:ReportService2010.ReportingService2010.ListEvents%2A>|Restituisce un elenco di estensioni degli eventi come visualizzate nel file di configurazione del server di report.|  
|<xref:ReportService2010.ReportingService2010.ListJobs%2A>|Restituisce un elenco dei processi in esecuzione nel server di report.|  
|<xref:ReportService2010.ReportingService2010.ListExtensions%2A>|Restituisce un elenco delle estensioni configurate per un tipo di estensione specifico.|  
|<xref:ReportService2010.ReportingService2010.ListExtensionTypes%2A>|Restituisce un elenco di tipi di estensioni supportate.|  
|<xref:ReportService2010.ReportingService2010.ListItemTypes%2A>|Restituisce un elenco di tipi di elementi del catalogo.|  
|<xref:ReportService2010.ReportingService2010.ListJobActions%2A>|Restituisce un elenco di azioni del processo supportate.|  
|<xref:ReportService2010.ReportingService2010.ListJobStates%2A>|Restituisce un elenco di stati del processo supportati.|  
|<xref:ReportService2010.ReportingService2010.ListJobTypes%2A>|Restituisce un elenco di tipi di processo supportati.|  
|<xref:ReportService2010.ReportingService2010.ListParents%2A>|Recupera elementi padre per l'elemento specificato.|  
|<xref:ReportService2010.ReportingService2010.ListSecurityScopes%2A>|Restituisce un elenco di ambiti di sicurezza supportati.|  
|<xref:ReportService2010.ReportingService2010.Logoff%2A>|Disconnette l'utente corrente che effettua richieste del servizio Web. Questo metodo può essere applicato solo in modalità nativa.|  
|<xref:ReportService2010.ReportingService2010.LogonUser%2A>|Connette un utente e autentica una richiesta al servizio Web ReportServer. Questo metodo può essere applicato solo in modalità nativa.|  
|<xref:ReportService2010.ReportingService2010.SetItemReferences%2A>|Imposta gli elementi del catalogo associati a un elemento.|  
|<xref:ReportService2010.ReportingService2010.MoveItem%2A>|Sposta e/o rinomina un elemento.|  
|<xref:ReportService2010.ReportingService2010.SetProperties%2A>|Imposta una o più proprietà di un elemento.|  
|<xref:ReportService2010.ReportingService2010.SetItemDefinition%2A>|Imposta la definizione o il contenuto per un elemento specificato. Questo metodo si applica ai tipi di elemento `Report`, `Model`, `Dataset`, `Component`, `Resource` e `DataSource`.|  
|<xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>|Imposta una o più proprietà di sistema nel server di report o in una farm di SharePoint.|  
|<xref:ReportService2010.ReportingService2010.ValidateExtensionSettings%2A>|Convalida le impostazioni per l'estensione di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni tramite servizio Web e .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Servizio Web ReportServer](../report-server-web-service.md)   
 [Metodi del servizio Web ReportServer](report-server-web-service-methods.md)   
 [Riferimento tecnico &#40;SSRS&#41;](../../technical-reference-ssrs.md)  
  
  
