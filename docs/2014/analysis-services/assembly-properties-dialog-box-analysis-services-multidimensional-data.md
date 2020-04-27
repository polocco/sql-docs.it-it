---
title: Finestra di dialogo Proprietà assembly (Analysis Services-Dati multidimensionali) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.assemblyproperties.f1
ms.assetid: da1174d6-d82b-4337-ac19-7368dbd95a84
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b21230ddff5a3db043b533a4f921a30b02da739b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66062302"
---
# <a name="assembly-properties-dialog-box-analysis-services---multidimensional-data"></a>Finestra di dialogo Proprietà assembly (Analysis Services - Dati multidimensionali)
  Utilizzare la finestra di dialogo **Proprietà assembly** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] per impostare le proprietà di un riferimento ad assembly in un database di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . È possibile visualizzare la finestra di dialogo **Proprietà assembly** facendo clic con il pulsante destro del mouse su un assembly in **Esplora oggetti** e scegliendo **Proprietà**.  
  
## <a name="options"></a>Opzioni  
  
|Termine|Definizione|  
|----------|----------------|  
|**Nome**|Consente di modificare il nome del riferimento a un assembly.<br /><br /> Nota: cambiando questo valore non si modifica il nome dell'assembly definito nel riferimento, ma il nome usato dall'istanza o dal database di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] per indicare il riferimento all'assembly.|  
|**ID**|Consente di visualizzare l'ID dell'assembly a cui si riferisce il riferimento a un assembly.|  
|**Descrizione**|Consente di modificare la descrizione del riferimento a un assembly.|  
|**Timestamp creazione**|Consente di visualizzare la data e l'ora di creazione del riferimento a un assembly.|  
|**Ultimo aggiornamento schema**|Consente di visualizzare la data e l'ora dell'ultimo aggiornamento ai metadati per il riferimento a un assembly.|  
|**Type**|Consente di visualizzare il tipo del riferimento a un assembly. Vengono visualizzati i valori seguenti:<br /><br /> **Assembly .NET**: il riferimento all'assembly fa riferimento [!INCLUDE[msCoName](../includes/msconame-md.md)] a un assembly .NET Framework.<br /><br /> **Dll com**: il riferimento all'assembly fa riferimento a una libreria com.|  
|**origine**|Consente di visualizzare l'origine del riferimento a un assembly. Questa proprietà in genere contiene il percorso completo e il nome file di assembly a cui si riferisce il riferimento a un assembly.|  
|**Set di autorizzazioni**|Consente di selezionare il set di autorizzazioni utilizzato per determinare l'accesso al riferimento a un assembly. Per ulteriori informazioni sui valori disponibili per questa proprietà, vedere <xref:Microsoft.AnalysisServices.ClrAssembly.PermissionSet%2A>.|  
|**Impostazioni di rappresentazione**|Consente di selezionare le impostazioni di rappresentazione da utilizzare per l'accesso al riferimento a un assembly. Per altre informazioni sui valori disponibili per questa proprietà, vedere [Elemento ImpersonationInfo &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl)|  
  
## <a name="see-also"></a>Vedi anche  
 [Finestre di progettazione e finestre di dialogo Analysis Services &#40;dati multidimensionali&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Gestione di assembly di modelli multidimensionali](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
