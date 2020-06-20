---
title: Finestra di dialogo operazioni attive | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isoperations.executions.f1
- sql12.ssis.ssms.isoperations.general.f1
ms.assetid: 5bb0fcd6-0ce9-488a-85b8-25dddaa03cda
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 9c6cd168a852eca294e85de696a611b460423c5a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84926552"
---
# <a name="active-operations-dialog-box"></a>Finestra di dialogo Operazioni attive
  Utilizzare la finestra di dialogo **Operazioni attive** per visualizzare lo stato delle operazioni di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] attualmente in esecuzione nel server di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , ad esempio distribuzione, convalida ed esecuzione dei pacchetti. Questi dati vengono archiviati nel catalogo SSISDB.  
  
 Per altre informazioni sulle viste [!INCLUDE[tsql](../includes/tsql-md.md)] correlate, vedere[catalog.operations &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database), [catalog.validations &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-validations-ssisdb-database) e [catalog.executions &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database)  
  
 **Per saperne di più**  
  
1.  [Apertura della finestra di dialogo Operazioni attive](#open_dialog)  
  
2.  [Configurare le opzioni](#options)  
  
##  <a name="open-the-active-operations-dialog-box"></a><a name="open_dialog"></a>Aprire la finestra di dialogo operazioni attive  
  
1.  Aprire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
2.  Connettersi al motore di database di Microsoft SQL Server.  
  
3.  In Esplora oggetti espandere il nodo **Integration Services** , fare clic con il pulsante destro del mouse su **SSISDB**, quindi fare clic su **Operazioni attive**.  
  
##  <a name="configure-the-options"></a><a name="options"></a>Configurare le opzioni  
  
### <a name="options"></a>Opzioni  
 **Tipo**  
 Consente di specificare il tipo di operazione. Di seguito sono riportati i valori possibili per il campo **tipo** e i valori corrispondenti nella colonna operations_type della vista Transact-SQL `catalog.operations` .  
  
|||  
|-|-|  
|Inizializzazione di Integration Services|1|  
|Pulizia di operazioni (processo di SQL Agent)|2|  
|Pulizia delle versioni del progetto (processo di SQL Agent)|3|  
|Distribuzione del progetto|101|  
|Ripristino del progetto|106|  
|Creazione e avvio dell'esecuzione del pacchetto|200|  
|Arresto dell'operazione (arresto di una convalida o di un'esecuzione)|202|  
|Convalida del progetto|300|  
|Convalida del pacchetto|301|  
|Configurazione del catalogo|1000|  
  
 **Stop**  
 Fare clic per arrestare un'operazione in esecuzione.  
  
  
