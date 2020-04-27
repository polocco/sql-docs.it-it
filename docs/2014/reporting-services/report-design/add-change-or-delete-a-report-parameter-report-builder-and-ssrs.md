---
title: Aggiungere, modificare o eliminare un parametro di report (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d44a8e0a-10cf-4502-9391-09743ffc9bad
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ebf333b49c20c7eadef4fdbcd54834c450d274c6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66106691"
---
# <a name="add-change-or-delete-a-report-parameter-report-builder-and-ssrs"></a>Aggiungere, modificare o eliminare un parametro di report (Generatore report e SSRS)
  Un parametro di report consente di scegliere i dati del report, connettere report correlati e variare la presentazione del report. È possibile specificare un valore predefinito e un elenco di valori disponibili per consentire all'utente di modificare la selezione.  
  
 Dopo aver pubblicato un report, è possibile modificare i valori predefiniti, i valori disponibili e altre proprietà relative a un parametro di report sul server di report. Per fornire più set di valori predefiniti del parametro, è possibile creare report collegati. Per ulteriori informazioni, vedere "Impostazione delle proprietà dei parametri per un report pubblicato" nella documentazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] inclusa nella [documentazione online di SQL Server](https://go.microsoft.com/fwlink/?linkid=120955).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-or-edit-a-report-parameter"></a>Per aggiungere o modificare un parametro di report  
  
1.  Nel riquadro **Dati report** fare clic con il pulsante destro del mouse sul nodo **Parametri** e scegliere **Aggiungi parametro**. Verrà visualizzata la finestra di dialogo **Proprietà parametri report** .  
  
2.  In **Nome**digitare il nome del parametro o accettare il nome predefinito.  
  
3.  Nella casella **Messaggio di richiesta**digitare il testo da visualizzare accanto alla casella di testo del parametro quando l'utente esegue il report.  
  
4.  Nella casella **Tipo di dati**selezionare il tipo di dati per il valore del parametro.  
  
5.  Se il parametro può contenere un valore vuoto, selezionare **Consenti nessun valore**.  
  
6.  Se il parametro può contenere un valore Null, selezionare **Consenti valore Null**.  
  
7.  Per consentire agli utenti la selezione di più valori per il parametro, selezionare **Consenti più valori**.  
  
8.  Impostare l'opzione di visibilità.  
  
    -   Per visualizzare il parametro sulla barra degli strumenti all'inizio del report, selezionare **Visibile**.  
  
    -   Per nascondere il parametro in modo da non visualizzarlo sulla barra degli strumenti, selezionare **Nascosto**.  
  
    -   Per nascondere il parametro e proteggerlo da eventuali modifiche sul server di report in seguito alla relativa pubblicazione, selezionare **Interno**. Il parametro di report potrà essere visualizzato solo nella relativa definizione. Per questa opzione è necessario impostare un valore predefinito o consentire l'immissione di un valore Null per il parametro.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-report-parameter"></a>Per eliminare un parametro di report  
  
1.  Nel riquadro **dei dati del report** espandere il nodo **parametri** .  
  
2.  Fare clic con il pulsante destro del mouse sul parametro di report, quindi scegliere **Elimina**.  
  
## <a name="see-also"></a>Vedi anche  
 [Aggiunta, modifica o eliminazione dei valori disponibili per un parametro di report &#40;Generatore report e SSRS&#41;](add-change-or-delete-available-values-for-a-report-parameter.md)   
 [Aggiungere, modificare o eliminare valori predefiniti per un parametro di report &#40;Generatore report e SSRS&#41;](add-change-or-delete-default-values-for-a-report-parameter.md)   
 [Modificare l'ordine di un parametro di report &#40;Generatore report e SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)   
 [Parametri del report &#40;Generatore report e Progettazione report&#41;](report-parameters-report-builder-and-report-designer.md)   
 [Guida Generatore report per finestre di dialogo, riquadri e procedure guidate](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Aggiungere parametri di propagazione a un report &#40;Generatore report e SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [Esercitazione: aggiungere un parametro al report &#40;Generatore report&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Esercitazioni &#40;Generatore report&#41;](../report-builder-tutorials.md)   
 [Aggiungere filtri del set di dati, aree dati e gruppi &#40;Generatore report e SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Riferimenti alla raccolta Parameters &#40;Generatore report e SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md)   
 [Aggiunta di un parametro multivalore a un report](add-a-multi-value-parameter-to-a-report.md)  
  
  
