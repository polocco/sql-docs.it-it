---
title: Selezione attributi dimensione (creazione guidata dimensione) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionattributes.f1
ms.assetid: f58a3e14-ab27-44d3-8c26-f5c9ee7583b0
author: minewiskan
ms.author: owend
ms.openlocfilehash: dcaf18ea2df3bbd3b227c8948d2fb15f54828853
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2020
ms.locfileid: "84537923"
---
# <a name="select-dimension-attributes-dimension-wizard"></a>Selezione attributi dimensione (Creazione guidata dimensione)
  La pagina **Selezione attributi dimensione** consente di selezionare e modificare gli attributi della dimensione da creare.  
  
> [!NOTE]  
>  Se non è possibile leggere i valori di una colonna, ingrandire la finestra della procedura guidata e modificare la larghezza di ogni intestazione di colonna fino a leggerne i valori.  
  
 **Per aprire la Creazione guidata dimensione.**  
  
-   In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]fare clic con il pulsante destro del mouse sulla cartella **Dimensioni**in **Esplora soluzioni** per scegliere un progetto di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , quindi fare clic su **Nuova dimensione**.  
  
## <a name="options"></a>Opzioni  
 (Colonna con caselle di controllo)  
 Selezionare questa opzione per includere un attributo nella dimensione.  
  
 Per includere un attributo specifico, selezionare la casella di controllo relativa a tale attributo.  
  
 Per includere tutti gli attributi, selezionare la casella di controllo nell'intestazione di colonna.  
  
> [!NOTE]  
>  Impossibile deselezionare la casella di controllo per l'attributo chiave.  
  
 **Nome attributo**  
 Elenca gli attributi disponibili.  
  
 Per modificare il nome di un attributo, fare clic sul nome dell’attributo e digitare un nuovo nome.  
  
 **Consenti esplorazione**  
 Selezionare per rendere disponibile l'attributo all'utente finale per l’esplorazione e l’applicazione di filtri. **Consenti esplorazione** deve essere selezionato per l'attributo chiave. Per gli attributi non chiave, **Consenti esplorazione** non è selezionato per impostazione predefinita. Gli attributi non chiave vengono pertanto visualizzati solo come proprietà del membro.  
  
 Nella maggior parte dei casi, l'attributo è reso disponibile o non disponibile per l'esplorazione impostando la proprietà `AttributeHierarchyEnabled` rispettivamente su `True` o su `False`. Nei tre casi seguenti, la procedura guidata utilizza comunque impostazioni diverse.  
  
|Caso|Impostazioni|  
|----------|--------------|  
|Una dimensione contiene una gerarchia padre-figlio e **Consenti esplorazione** non è selezionato.|La procedura guidata lascia la proprietà `AttributeHierarchyEnabled` impostata su `True` e imposta l'attributo `AttributeHierarchyVisible` su `False` per l'attributo chiave.|  
|Una tabella in una dimensione contiene una chiave esterna a una tabella che non è nella dimensione|La procedura guidata seleziona la chiave esterna come un attributo da includere, ma non selezionerà **Consenti esplorazione**. Se si mantengono queste impostazioni, la proprietà `AttributeHiearchyEnabled` dell’attributo sarà impostata su `True` e la proprietà `AttributeHierarchyVisible` sarà impostata su `False`.|  
|Una dimensione contiene tabelle con schema snowflake raggiungibili tramite colonne chiavi esterne che ammettono valori Null.<br /><br /> -e-<br /><br /> Consenti esplorazione per l'attributo basato sulla chiave della tabella con schema snowflake non è selezionato|La procedura guidata creerà il nuovo attributo con la proprietà `AttributeHiearchyEnabled` impostata su `True` e la proprietà `AttributeHierarchyVisible` impostata su `False`.|  
  
 **Tipo di attributo**  
 (Facoltativo) Impostare il tipo per l'attributo. Il valore predefinito è **Regolare**. Il tipo di attributo fornisce l’istruzione alle applicazioni client riguardo le informazioni che l'attributo potrebbe contenere.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida sensibile al contesto della creazione guidata dimensione](dimension-wizard-f1-help.md)   
 [Dimensioni &#40;Analysis Services Dati multidimensionali&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Dimensioni nei modelli multidimensionali](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
