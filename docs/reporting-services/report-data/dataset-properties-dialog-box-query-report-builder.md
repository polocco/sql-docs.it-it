---
title: Finestra di dialogo Proprietà set di dati, Query (Generatore report) | Microsoft Docs
description: Informazioni su come usare l'opzione Query nella finestra di dialogo Proprietà set di dati di Generatore report per scegliere un set di dati condiviso da un server di report o per creare un set di dati incorporato.
ms.date: 08/17/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: reference
f1_keywords:
- "10024"
- sql13.rtp.rptdesigner.datasetproperties.query.f1
- "10160"
ms.assetid: 75432318-0b00-4797-917c-0a2e74f9d951
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 14380ba698101c76a84d0b9eef27a4ea31953f2d
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2020
ms.locfileid: "86458933"
---
# <a name="dataset-properties-dialog-box-query-report-builder"></a>Finestra di dialogo Proprietà set di dati, Query (Generatore report)
 
Selezionare **Query** nella finestra di dialogo **Proprietà set di dati** per scegliere un set di dati condiviso da un server di report o per creare un set di dati incorporato. Per un set di dati incorporato, è necessario scegliere un'origine dati e compilare una query.  
  
## <a name="options"></a>Opzioni  
 **Nome**  
 Consente di digitare un nome per il set di dati. Non è possibile specificare un nome uguale a quello di un'area dati o di un gruppo nel report.  
  
 **Usa un set di dati condiviso**  
 Selezionare questa opzione per utilizzare un set di dati predefinito dal server di report.  
  
 **Sfoglia**  
 Selezionare una cartella in un server di report o sito di SharePoint e scegliere un set di dati condiviso (estensione rsd).  
  
 **Usa un set di dati incorporato nel report**  
 Selezionare questa opzione per creare un set di dati da utilizzare solo per il report specifico.  
  
 **Origine dati**  
 Consente di selezionare l'origine dati su cui basare il set di dati. Per creare una nuova origine dati, fare clic su **Nuova**.  
  
 **Tipo di query**  
 Consente di selezionare il tipo di comando o query da utilizzare per il set di dati. Selezionare **Testo** per eseguire una query che consenta di recuperare dati dal database. Selezionare **Tabella** per usare la funzionalità **TableDirect** di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e selezionare tutti i campi all'interno di una tabella. Selezionare **Stored procedure** per eseguire una stored procedure in base al nome. **Testo** è selezionato per impostazione predefinita e viene usato per la maggior parte delle query. Per modificare la query sull'origine dati selezionata, fare clic su **Progettazione query**.  
  
> [!NOTE]  
>  Non tutti i tipi di query sono supportati da tutte le origini dati. Il tipo **Tabella** , ad esempio, è supportato solo dalle origini dati di tipo **OLE DB** e **ODBC**.  
  
 **Query**  
 Questa opzione viene visualizzata quando si sceglie l'opzione del tipo di comando **Testo** . Digitare una query o importare una query preesistente facendo clic su **Importa**. Fare clic sul pulsante **Espressione** (*fx*) per modificare l'espressione.  
  
> [!NOTE]  
>  Se si usa una query compilata in una finestra di progettazione query, il relativo testo viene visualizzato in questa casella.  
  
**Nome tabella**  
Questa opzione viene visualizzata quando si seleziona **Tabella**. Immettere il nome della tabella che si desidera utilizzare come set di dati.   
  
**Selezionare o immettere un nome di stored procedure**  
Questa opzione viene visualizzata quando si sceglie l'opzione del tipo di comando Stored procedure. Digitare o scegliere il nome della stored procedure che si desidera utilizzare. Fare clic sul pulsante **Espressione** (*fx*) per modificare l'espressione.   
  
 **Timeout (in secondi)**  
 Consente di digitare il numero di secondi di attesa prima del timeout della query. Il valore predefinito è 30 secondi. Il valore nel campo **Timeout** deve essere vuoto o maggiore di zero. Se non si specifica alcun valore, non si verificherà mai il timeout della query.  
  
 **Aggiorna campi**  
 Eseguire il comando query per aggiornare l'elenco di campi nella **finestra di dialogo Proprietà set di dati, pagina Campi**.  
  
## <a name="see-also"></a>Vedere anche  
[Set di dati condivisi e incorporati del report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
[Set di dati del report &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)  
[Strumenti di progettazione query &#40;SSRS&#41;](query-design-tools-ssrs.md)  
  
  
