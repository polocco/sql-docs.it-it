---
title: Editor trasformazione Copia colonna | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.copymaptransformation.f1
helpviewer_keywords:
- Copy Column Transformation Editor
ms.assetid: d8e70541-d563-4ce4-bf66-bc888a0d3026
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 03d8cdb35372ed9850f3329f26e2647e018d9583
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66060296"
---
# <a name="copy-column-transformation-editor"></a>Editor trasformazione Copia colonna
  La finestra di dialogo **Editor trasformazione Copia colonna** consente di selezionare le colonne da copiare e di assegnare nomi alle nuove colonne di output.  
  
 Per altre informazioni sulla trasformazione Copia colonna, vedere [Trasformazione Copia colonna](data-flow/transformations/copy-column-transformation.md).  
  
> [!NOTE]  
>  Quando si copiano tutti i dati di origine in una destinazione, potrebbe non essere necessario utilizzare la trasformazione Copia colonna. In alcuni casi è possibile connettere un'origine direttamente a una destinazione qualora non sia necessaria alcuna trasformazione dei dati. In simili circostanze è spesso preferibile utilizzare l'Importazione/Esportazione guidata SQL Server per creare automaticamente il pacchetto. Successivamente è possibile perfezionare e riconfigurare il pacchetto in base alle necessità. Per altre informazioni, vedere [SQL Server Import and Export Wizard](import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).  
  
## <a name="options"></a>Opzioni  
 **Colonne di input disponibili**  
 Consente di selezionare le colonne da copiare mediante le caselle di controllo. Le selezioni effettuate determinano l'aggiunta delle colonne di input nella tabella sottostante.  
  
 **Colonna di input**  
 Consente di selezionare le colonne da copiare nell'elenco delle colonne di input disponibili. Le selezioni effettuate vengono riflesse nelle selezioni delle caselle di controllo nella tabella **Colonne di input disponibili** .  
  
 **Alias di output**  
 Consente di digitare un alias per ogni colonna di output. Per impostazione predefinita viene suggerito **Copia di**seguito dal nome della colonna di input. È comunque possibile scegliere qualsiasi nome descrittivo univoco.  
  
## <a name="see-also"></a>Vedi anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
