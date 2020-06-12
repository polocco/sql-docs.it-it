---
title: Finestra di dialogo Aggiungi dimensione al cubo (Analysis Services-Dati multidimensionali) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.addcubedimensiondialog.f1
helpviewer_keywords:
- Add Cube Dimension dialog box
ms.assetid: 625a3b1f-183b-445f-9bb7-96945c324767
author: minewiskan
ms.author: owend
ms.openlocfilehash: d0de75c02c39b0690184f35f2b0b6a07d7ed9a4f
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528229"
---
# <a name="add-cube-dimension-dialog-box-analysis-services---multidimensional-data"></a>Finestra di dialogo Aggiungi dimensione al cubo (Analysis Services - Dati multidimensionali)
  Utilizzare la finestra di dialogo **Aggiungi dimensione al cubo** in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] per aggiungere a un cubo un riferimento a una dimensione del database. Per visualizzare la finestra di dialogo **Aggiungi dimensione al cubo** è possibile eseguire una delle operazioni seguenti:  
  
-   Fare clic su **Aggiungi dimensione al cubo** nel riquadro **Barra degli strumenti** della scheda **Struttura cubo** o **Utilizzo dimensioni** in Progettazione cubi.  
  
-   Fare clic con il pulsante destro del mouse nel riquadro **Dimensioni** della scheda **Struttura cubo** in Progettazione cubi e scegliere **Aggiungi dimensione al cubo** dal menu di scelta rapida.  
  
-   Fare clic con il pulsante destro del mouse nel riquadro **Griglia** della scheda **Utilizzo dimensioni** in Progettazione cubi e scegliere **Aggiungi dimensione al cubo** dal menu di scelta rapida.  
  
> [!NOTE]  
>  Ogni dimensione del cubo può avere solo una relazione con un gruppo di misure. È tuttavia possibile creare più dimensioni del cubo e aggiungerle al cubo, se la dimensione del database su cui si basa la dimensione del cubo è correlata a gruppi di misure mediante più di una relazione nella vista origine dati. Tali dimensioni sono definite dimensioni con ruoli multipli e sono normalmente presenti nelle dimensioni temporali.  
  
## <a name="options"></a>Opzioni  
 **Selezionare una dimensione**  
 Consente di selezionare una dimensione del database esistente per aggiungere al cubo selezionato una dimensione del cubo basata su tale dimensione esistente. È possibile definire più dimensioni del cubo dalla stessa dimensione del database.  
  
> [!NOTE]  
>  Se a un cubo vengono aggiunte più dimensioni del cubo basate sulla stessa dimensione del database, le dimensioni del cubo aggiuntive sono denominate dimensioni con ruoli multipli.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestre di progettazione e finestre di dialogo Analysis Services &#40;dati multidimensionali&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
