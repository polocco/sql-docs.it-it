---
title: Strumenti di calcolo (scheda azioni, Progettazione cubi) (Analysis Services-Dati multidimensionali) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.actionsview.calculationtoolspane.f1
ms.assetid: a3370370-43cd-4cc2-bb9f-c0d988b96f05
author: minewiskan
ms.author: owend
ms.openlocfilehash: 42336656ce19d36cf0eadc986450dd8f3b81f669
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2020
ms.locfileid: "84527644"
---
# <a name="calculation-tools-actions-tab-cube-designer-analysis-services---multidimensional-data"></a>Strumenti di calcolo (scheda Azioni, Progettazione cubi) (Analysis Services - Dati multidimensionali)
  Utilizzare il riquadro **Strumenti di calcolo** della scheda **Azioni** in Progettazione cubi per esplorare i metadati, le funzioni e i modelli disponibili per le azioni, le azioni drill-through e le azioni report.  
  
## <a name="options"></a>Opzioni  
 **Metadati**  
 Consente di visualizzare i metadati relativi al cubo selezionato.  
  
 Trascinare un elemento selezionato nel riquadro dell' **editor dei form delle azioni**, dell' **editor dei form delle azioni drill-through**o nell' **editor dei form delle azioni report** per inserire la sintassi MDX (Multidimensional Expressions) per questo elemento nella posizione selezionata all'interno del riquadro.  
  
 **Funzioni**  
 Consente di visualizzare le funzioni disponibili per espressioni e condizioni.  
  
 Trascinare un elemento selezionato nel riquadro dell'editor dei form delle azioni ****, dell'editor dei form delle azioni drill-through **** o dell'editor dei form delle azioni report **** per inserire la sintassi MDX per questo elemento nella posizione selezionata all'interno del riquadro.  
  
> [!NOTE]  
>  In modalità progetto, tramite la finestra di dialogo **Strumenti di calcolo** è possibile leggere le informazioni relative all'opzione da un file XML denominato MDXFunctions.xml, incluso in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. In modalità online, le informazioni relative all'opzione vengono recuperate dal set di righe dello schema MDSCHEMA_FUNCTIONS relativo all'istanza.  
  
 **Modelli**  
 Consente di visualizzare i modelli predefiniti disponibili per le azioni.  
  
 Trascinare un elemento selezionato nel riquadro dell'editor dei form delle azioni ****, dell'editor dei form delle azioni drill-through **** o dell'editor dei form delle azioni report **** per inserire la sintassi MDX per questo elemento nella posizione selezionata all'interno del riquadro.  
  
## <a name="context-menu"></a>Menu di scelta rapida  
 Nel menu di scelta rapida che viene visualizzato quando si fa clic con il pulsante destro del mouse su un elemento del riquadro **Strumenti di calcolo** sono disponibili le opzioni seguenti:  
  
|Opzione|Definizione|  
|------------|----------------|  
|**Copia**|Selezionare questa opzione per copiare negli Appunti l'elemento specificato in **Metadati** o **Funzioni** .<br /><br /> Si noti che questa opzione non viene visualizzata se si seleziona **modelli** . Si noti inoltre che questa opzione è disabilitata se non è possibile copiare il membro selezionato, ad esempio la cartella **set** di una dimensione visualizzata in **metadati** o la cartella del gruppo di funzioni per una funzione visualizzata in **funzioni**.|  
|**Filtra membri**|Selezionare questa opzione per visualizzare la finestra di dialogo **Filtra membri** e filtrare i membri visualizzati per l'elemento selezionato in **Metadati**. Per altre informazioni sulla finestra di dialogo **Filtra membri** vedere [Finestra di dialogo Filtra membri &#40;Analysis Services - Dati multidimensionali&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).<br /><br /> Si noti che questa opzione viene visualizzata solo se si seleziona **metadati** . Si noti inoltre che questa opzione è abilitata solo se nei **metadati**è selezionato un livello per un attributo.|  
|**Aggiungi modello**|Scegliere questa opzione per aggiungere al cubo una nuova azione, una nuova azione drill-through o una nuova azione report basata sul modello selezionato e visualizzare rispettivamente l'editor dei form delle azioni ****, l'editor dei form delle azioni drill-through **** oppure l'editor dei form delle azioni report ****.<br /><br /> Nota: questa opzione viene visualizzata solo se si seleziona **metadati** .|  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali sullo scripting MDX &#40;Analysis Services&#41;](multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)   
 [Azioni &#40;Progettazione cubi&#41; &#40;Analysis Services Dati multidimensionali&#41;](actions-cube-designer-analysis-services-multidimensional-data.md)   
 [Barra degli strumenti &#40;scheda azioni, Progettazione cubi&#41; &#40;Analysis Services Dati multidimensionali&#41;](toolbar-actions-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Libreria azioni &#40;scheda azioni, Progettazione cubi&#41; &#40;Analysis Services Dati multidimensionali&#41;](action-organizer-cube-designer-analysis-services-multidimensional-data.md)   
 [Editor dei form delle azioni &#40;scheda azioni, Progettazione cubi&#41; &#40;Analysis Services Dati multidimensionali&#41;](action-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [Editor dei form delle azioni drill-through &#40;scheda azioni, Progettazione cubi&#41; &#40;Analysis Services Dati multidimensionali&#41;](drillthrough-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [Editor dei form delle azioni report &#40;scheda azioni, Progettazione cubi&#41; &#40;Analysis Services Dati multidimensionali&#41;](report-action-form-editor-cube-designer-analysis-services-multidimensional-data.md)  
  
  
