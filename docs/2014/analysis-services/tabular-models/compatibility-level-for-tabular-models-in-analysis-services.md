---
title: Livello di compatibilità (SSAS tabulare SP1) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.versioncompat.f1
ms.assetid: 8943d78d-4a73-4be8-ad14-3d428f5abd06
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 57a1e67db8bcbf17dc964f7341df25a396c36ad0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/25/2020
ms.locfileid: "66067596"
---
# <a name="compatibility-level-ssas-tabular-sp1"></a>Livello di compatibilità (SSAS tabulare SP1)
  È possibile specificare il *livello di compatibilità* durante la creazione di nuovi progetti di modello tabulare, durante l'aggiornamento di progetti di modelli tabulari esistenti, durante l'aggiornamento di database modello tabulare distribuiti esistenti o durante l'importazione di cartelle di lavoro  
  
## <a name="compatibility-level"></a>Livello di compatibilità  
 In genere, prima di eseguire installazioni in computer di produzione, nei computer di sviluppo e test vengono installati nuove versioni e Service Pack. In questi casi è importante impostare il livello di compatibilità per i progetti di modelli tabulari nuovi e per quelli già distribuiti in un ambiente di produzione.  
  
 Un'istanza di Analysis Services di [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] supporta i seguenti livelli di compatibilità (versione del database):  
  
-   SQL Server 2012 (1100)  
  
-   SQL Server 2012 SP1 (1103)  
  
-   SQL Server 2014 (1103)  
  
### <a name="set-compatibility-level-when-creating-a-new-tabular-model-project"></a>Impostare il livello di compatibilità durante la creazione di un nuovo progetto di modello tabulare  
 Quando si crea un nuovo progetto di modello tabulare in SQL Server Data Tools (SSDT), nella finestra di dialogo **Opzioni nuovo progetto tabulare** è possibile specificare il livello di compatibilità. È possibile scegliere di creare un nuovo progetto da distribuire a un'istanza di Analysis Services di [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] o versione successiva o a un'istanza di Analysis Services di SQL Server 2012 (senza Service Pack 1).  
  
 È inoltre possibile specificare un livello di compatibilità predefinito se si seleziona l'opzione **Non visualizzare più questo messaggio** . In tutti i progetti successivi verrà utilizzato il livello di compatibilità specificato. È possibile modificare il livello di compatibilità predefinito nelle opzioni di SSDT.  
  
### <a name="upgrade-an-existing-tabular-model-project-to-1103-compatibility-level"></a>Aggiornare un progetto di modello tabulare esistente al livello di compatibilità 1103  
 È possibile aggiornare un progetto di modello tabulare creato in SSDT prima [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] di installare o versione successiva in modo che sia compatibile con la versione 1103 del database usando la proprietà **livello di compatibilità** nella finestra **proprietà** del modello. Per aggiornare un progetto di modello tabulare, nel computer in cui è installato SSDT deve essere installato [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] o versione successiva e nell'istanza di Analysis Services in cui si trova il database dell'area di lavoro deve essere installato [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] o versione successiva. Non è possibile effettuare il downgrade a una versione precedente.  
  
### <a name="upgrade-a-deployed-tabular-model-database-to-1103-compatibility-level"></a>Aggiornare un database modello tabulare distribuito al livello di compatibilità 1103  
 È possibile aggiornare un database modello tabulare distribuito esistente alla versione del database 1103 compatibile in SQL Server Management Studio (SSMS) utilizzando la proprietà **livello di compatibilità** in **Proprietà database**. Per eseguire l'aggiornamento, nel computer in cui si trova l'istanza di SQL Server Analysis Services deve essere installato [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] o versione successiva. Non è possibile effettuare il downgrade di un database modello tabulare distribuito a una versione precedente.  
  
### <a name="import-from-powerpivot"></a>Importare da PowerPivot  
 In fase di creazione di un nuovo progetto di modello tabulare eseguendo un'importazione da PowerPivot, è possibile specificare se si desidera eseguire l'aggiornamento al livello di compatibilità predefinito (se precedentemente configurato in SSDT) o mantenere il livello di compatibilità già specificato nella cartella di lavoro di PowerPivot.  
  
### <a name="check-compatibility-level-for-a-tabular-model-database-in-ssms"></a>Verificare il livello di compatibilità per un database modello tabulare in SSMS  
 È possibile controllare il livello di compatibilità per un database modello tabulare in SSMS visualizzando la proprietà **livello di compatibilità** ( [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]nuovo in) in **Proprietà database**.  
  
### <a name="check-supported-compatibility-level-for-an-analysis-services-instance-in-ssms"></a>Verificare il livello di compatibilità supportato per un'istanza di Analysis Services in SSMS  
 È possibile controllare il livello di compatibilità supportato in SSMS visualizzando la proprietà **livello di compatibilità supportato** nella pagina **informazioni** (nuovo in [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]) in **Analysis Services proprietà**. Il livello di compatibilità supportato 1103 indica che SQL Server SP1 o versione successiva è installato. Non è possibile modificare il livello di compatibilità supportato.  
  
  
