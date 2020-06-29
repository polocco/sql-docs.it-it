---
title: Copia colonna - trasformazione | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.copycolumntrans.f1
helpviewer_keywords:
- columns [Integration Services], copying
- copying columns
- Copy Column transformation
ms.assetid: 1c72a313-9026-46bc-a57f-c6b3f47346f8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fd2745070a92ab71e89f3bfa9edd8673b676632b
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "85430888"
---
# <a name="copy-column-transformation"></a>Copia colonna - trasformazione
  La trasformazione Copia colonna consente di creare nuove colonne copiando le colonne di input e aggiungendo le nuove colonne all'output della trasformazione. Successivamente nel flusso di dati alle copie delle colonne sarà possibile applicare altre trasformazioni. È ad esempio possibile utilizzare la trasformazione Copia colonna per creare una copia di una colonna e quindi utilizzare la trasformazione Mappa caratteri per convertire in caratteri maiuscoli i dati copiati oppure utilizzare la trasformazione Aggregazione per applicare aggregazioni alla nuova colonna.  
  
## <a name="configuration-of-the-copy-column-transformation"></a>Configurazione della trasformazione Copia colonna  
 Per configurare la trasformazione Copia colonna, è necessario specificare le colonne di input da copiare. È possibile creare più copie di una stessa colonna oppure creare copie di più colonne in una singola operazione.  
  
 Questa trasformazione include un input e un output. Non supporta un output degli errori.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor trasformazione Copia colonna** , vedere [Editor trasformazione Copia colonna](../../copy-column-transformation-editor.md).  
  
 Nella finestra di dialogo **Editor avanzato** sono disponibili le proprietà che è possibile impostare a livello di codice. Per ulteriori informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor avanzato** o a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Proprietà comuni](../../common-properties.md)  
  
-   [proprietà personalizzate della trasformazione](transformation-custom-properties.md)  
  
 Per altre informazioni su come impostare le proprietà, vedere [Impostazione delle proprietà di un componente del flusso di dati](../set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Flusso di dati](../data-flow.md)   
 [Trasformazioni di Integration Services](integration-services-transformations.md)  
  
  
