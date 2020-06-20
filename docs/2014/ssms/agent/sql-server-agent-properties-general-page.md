---
title: Proprietà SQL Server Agent (pagina Generale) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.general.f1
ms.assetid: b51601e9-5454-43c6-bb5e-24eb2ff043c8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 667a07744acf4b6d8b0dfa1e83adca738add0b4f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058706"
---
# <a name="sql-server-agent-properties-general-page"></a>Proprietà SQL Server Agent (pagina Generale)
  Utilizzare questa pagina per visualizzare e modificare le proprietà generali del [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servizio Agent.  
  
## <a name="options"></a>Opzioni  
 **Stato del servizio**  
 Visualizza lo stato corrente del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 **Riavvia automaticamente SQL Server in caso di arresto imprevisto**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent esegue il riavvio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] quando si verifica un arresto imprevisto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Riavvia automaticamente SQL Server Agent in caso di arresto imprevisto**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esegue il riavvio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent quando si verifica un arresto imprevisto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 **Nome file**  
 Consente di specificare il nome del file per il log degli errori.  
  
 **...**  
 Consente di individuare i file di log degli errori.  
  
 **Includi messaggi di traccia esecuzione**  
 Consente di includere messaggi di traccia dell'esecuzione nel log degli errori. Nei messaggi di traccia sono incluse informazioni dettagliate sull'operazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Se questa opzione è selezionata, per il file di log sarà necessario ulteriore spazio su disco. È consigliabile selezionare questa opzione solo durante la risoluzione di un problema che potrebbe coinvolgere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 **Scrivi file OEM**  
 Consente di scrivere il file di log degli errori come file non Unicode. In questo modo, è possibile ridurre la quantità di spazio su disco utilizzata dal file di log. Quando questa opzione è selezionata, è tuttavia possibile che i messaggi contenenti dati Unicode siano più difficili da leggere.  
  
 **Destinatario Net Send**  
 Consente di digitare il nome dell'operatore destinato a ricevere la notifica Net Send dei messaggi scritti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent nel file di log.  
  
## <a name="see-also"></a>Vedere anche  
 [Operatori](operators.md)   
 [Log degli errori di SQL Server Agent](sql-server-agent-error-log.md)  
  
  
