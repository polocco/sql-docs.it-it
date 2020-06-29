---
title: Conversione di dati in un tipo di dati diverso tramite la trasformazione Conversione dati | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- converting data types [Integration Services]
- Data Conversion transformation
- data types [Integration Services], converting
ms.assetid: 4aabbe4f-7666-4672-865a-9627bd25fbfd
author: chugugrace
ms.author: chugu
ms.openlocfilehash: be66d40f5009a87859d5b55c8b46a4b67950f94a
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "85430928"
---
# <a name="convert-data-to-a-different-data-type-by-using-the-data-conversion-transformation"></a>Conversione di dati in un tipo di dati diverso utilizzando la trasformazione Conversione dati
  È possibile aggiungere e configurare una trasformazione Conversione dati solo se il pacchetto include già almeno un'attività Flusso di dati e un'origine.  
  
### <a name="to-convert-data-to-a-different-data-type"></a>Per convertire i dati in un tipo di dati diverso  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  Fare clic sulla scheda **Flusso di dati** e quindi, dalla **casella degli strumenti**, trascinare la trasformazione Conversione dati sull'area di progettazione.  
  
4.  Connettere la trasformazione Conversione dati al flusso di dati trascinando un connettore dall'origine o dalla trasformazione precedente alla trasformazione Conversione dati.  
  
5.  Fare doppio clic sulla trasformazione Conversione dati.  
  
6.  Nella tabella **Colonne di input disponibili** della finestra di dialogo **Editor trasformazione Conversione dati** selezionare le caselle di controllo accanto alle colonne di cui si vuole convertire il tipo di dati.  
  
    > [!NOTE]  
    >  È possibile applicare più conversioni di dati a una singola colonna di input.  
  
7.  Facoltativamente, modificare i valori predefiniti nella colonna **Alias di output** .  
  
8.  Nell'elenco **Tipo di dati** selezionare il nuovo tipo di dati per la colonna. Il tipo di dati predefinito è quello della colonna di input.  
  
9. A seconda del tipo di dati selezionato, aggiornare facoltativamente i valori nelle colonne **Lunghezza**, **Precisione**, **Scala**e **Tabella codici** .  
  
10. Per configurare l'output degli errori, fare clic su **Configura output errori**. Per altre informazioni, vedere [Configurazione di un output degli errori in un componente del flusso di dati](../../configure-an-error-output-in-a-data-flow-component.md).  
  
11. Fare clic su **OK**.  
  
12. Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
## <a name="see-also"></a>Vedere anche  
 [Data Conversion Transformation](data-conversion-transformation.md)   
 [Trasformazioni di Integration Services](integration-services-transformations.md)   
 [Percorsi in Integration Services](../integration-services-paths.md)   
 [Tipi di dati di Integration Services](../integration-services-data-types.md)   
 [Attività Flusso di dati](../../control-flow/data-flow-task.md)  
  
  
