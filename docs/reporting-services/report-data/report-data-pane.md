---
title: Riquadro dei dati del report
description: Informazioni su come usare il riquadro dei dati del report per visualizzare i parametri attualmente definiti, le origini dati, i set di dati, le raccolte di campi e le immagini nel report.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: c7afab0edc7afd86b16103e5364d17a93579d096
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85812616"
---
# <a name="report-data-pane-in-sql-server-reporting-services-ssrs"></a>Riquadro dei dati del report in SQL Server Reporting Services (SSRS)

  Usare il riquadro **Dati report** per visualizzare i parametri, le origini dati, i set di dati, le raccolte di campi e le immagini attualmente definiti nel report. Nel riquadro Dati report è riportata una visualizzazione gerarchica degli elementi che rappresentano i dati del report. I nodi di livello superiore rappresentano campi, parametri, immagini e riferimenti a origini dati predefiniti. Espandere ogni nodo per visualizzare gli elementi dei dati. Ad esempio, quando si espande il nodo di un'origine dati, verranno visualizzati i set di dati definiti per tale origine dati. Quando si espande un set di dati, verrà visualizzata la relativa raccolta di campi. Trascinare gli elementi nell'area di progettazione del report per collegare i dati a elementi del report nella pagina.  
  
## <a name="options"></a>Opzioni

 **Campi predefiniti**  
 Rappresenta i campi disponibili in Reporting Services comunemente utilizzati in un report, ad esempio il nome o il numero di pagina. Per altre informazioni, vedere [Raccolte predefinite nelle espressioni &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/built-in-collections-in-expressions-report-builder.md).  
  
 **Parameters**  
 Rappresenta la raccolta dei parametri del report, che possono essere a valore singolo o multivalore. Per ulteriori informazioni, vedere la pagina relativa al [Parametri report &#40;Generatore report e Progettazione report&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md).  
  
 **Immagini**  
 Rappresenta il set di immagini utilizzato nel report. Per altre informazioni, vedere [Immagini &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/images-report-builder-and-ssrs.md).  
  
 **Origine dati**  
 Rappresenta un singolo riferimento a un'origine dati incorporata o condivisa. In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]le origini dati condivise vengono visualizzate nella cartella Origini dati condivise in Esplora soluzioni. Un'origine dati specifica uno dei tipi di origine dati supportati da Reporting Services. L'origine dati rappresenta il nodo padre per la raccolta di set di dati basati su di essa. Per altre informazioni, vedere [Creare stringhe di connessione dati - Generatore report e SSRS](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
  
 **Set di dati**  
 Rappresenta un singolo set di dati. Il set di dati corrisponde al nodo padre per la raccolta di campi specificati dalla query, inclusi eventuali campi calcolati. Reporting Services supporta le finestre di progettazione query che consentono di specificare una query. Per altre informazioni, vedere [Set di dati del report &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md) e [Strumenti di progettazione query &#40;SSRS&#41;](../../reporting-services/report-data/query-design-tools-ssrs.md).  
  
## <a name="next-steps"></a>Passaggi successivi

 - [Raccolta di campi del set di dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)
 - [Riquadro di raggruppamento](../../reporting-services/tools/grouping-pane.md)