---
title: Generale (Progettazione database) (Analysis Services-Dati multidimensionali) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.databasedesigner.dbconfigurationpane.f1
helpviewer_keywords:
- Database Designer
ms.assetid: 00c9c42b-db2b-4620-8fb6-1e165ff0cbdd
author: minewiskan
ms.author: owend
ms.openlocfilehash: e1e7b2e1e72263d8edf362941985bb775457fc6d
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544477"
---
# <a name="general-database-designer-analysis-services---multidimensional-data"></a>Generale (Progettazione database) (Analysis Services - Dati multidimensionali)
  Utilizzare la scheda **Generale** per modificare le proprietà di un database di [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
 **Per visualizzare la scheda Generale**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aprire un progetto [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
2.  In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , fare clic su **Modifica database**e quindi fare clic sulla scheda **Generale** .  
  
## <a name="basic-options"></a>Opzioni standard  
 Espandere la sezione **Standard** per modificare le informazioni di base relative al database. In questa sezione sono incluse le opzioni seguenti:  
  
 **Nome database**  
 Consente di visualizzare il nome del database.  
  
> [!NOTE]  
>  Per rinominare il database, in **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto e quindi scegliere **Proprietà**. Nella finestra di dialogo **Pagine delle proprietà** del database, nella pagina **Distribuzione** modificare il valore della proprietà **Database** digitando il nome desiderato.  
  
 **Descrizione**  
 Consente di digitare una descrizione del database.  
  
## <a name="translations-options"></a>Opzioni relative alle traduzioni  
 Espandere la sezione **Traduzioni** per creare e modificare le traduzioni della didascalia e della descrizione del database. Nella griglia visualizzata in questa sezione sono incluse le colonne seguenti:  
  
 **Lingua**  
 Consente di selezionare la lingua per la transazione specificata.  
  
 Per aggiungere una nuova traduzione alla griglia, fare clic su **\<Add new translation>** .  
  
 **Didascalia tradotta**  
 Consente di digitare la didascalia del database nella lingua della traduzione. Se vuota, viene utilizzata la didascalia predefinita del database.  
  
 **Descrizione tradotta**  
 Consente di digitare la descrizione del database nella lingua della traduzione. Se vuota, viene utilizzata la descrizione predefinita del database.  
  
## <a name="account-type-mapping-options"></a>Opzioni relative al mapping dei tipi di conto  
 Espandere la sezione **Mapping tipi di conto** per modificare la funzione di aggregazione predefinita associata a ogni **tipo** di conto nel database selezionato.  
  
> [!NOTE]  
>   Questa opzione si applica esclusivamente ai cubi nei quali una o più misure utilizzano la funzione di aggregazione *ByAccount* .  
  
 Nella griglia visualizzata in questa sezione sono incluse le colonne seguenti:  
  
 **Nome**  
 Consente di digitare il nome del tipo di conto.  
  
 Per aggiungere un nuovo tipo di conto, fare clic su **\<Add new account type>** .  
  
 **Alias**  
 Consente di impostare il nome predefinito del tipo di conto per l'utilizzo con Configurazione guidata funzionalità di Business Intelligence. Se la colonna è lasciata vuota, viene utilizzato il valore predefinito indicato nella colonna **Nome** .  
  
 **Funzione di aggregazione**  
 Consente di selezionare la funzione di aggregazione da utilizzare per il tipo di conto selezionato.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestre di progettazione e finestre di dialogo Analysis Services &#40;dati multidimensionali&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Database modello multidimensionale &#40;SSAS&#41;](multidimensional-models/multidimensional-model-databases-ssas.md)   
 [Avvisi &#40;progettazione database&#41; &#40;Analysis Services Dati multidimensionali&#41;](warnings-database-designer-analysis-services-multidimensional-data.md)  
  
  
