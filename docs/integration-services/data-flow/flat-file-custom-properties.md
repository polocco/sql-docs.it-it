---
description: Proprietà personalizzate del file flat
title: Proprietà personalizzate del file flat | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 7f2caeab-784c-4b0c-9b3e-6a88d1ccdbf9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9c20e9a830439e8065a1bbccfe7d25540c9ae639
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88430853"
---
# <a name="flat-file-custom-properties"></a>Proprietà personalizzate del file flat

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  **Proprietà personalizzate delle origini**  
  
 L'origine file flat include sia proprietà personalizzate che le proprietà comuni a tutti i componenti del flusso di dati.  
  
 Nella tabella seguente vengono descritte le proprietà personalizzate dell'origine file flat. Tutte le proprietà sono di lettura/scrittura.  
  
|Nome proprietà|Tipo di dati|Descrizione|  
|-------------------|---------------|-----------------|  
|FileNameColumnName|string|Nome di una colonna di output contenente il nome file. Se non si specifica alcun nome, non verrà generata alcuna colonna contenente il nome file.<br /><br /> Nota: questa proprietà non è disponibile in **Editor origine file flat**, ma può essere impostata tramite **Editor avanzato**.|  
|RetainNulls|Boolean|Valore che specifica se i valori Null dal file di origine devono essere mantenuti come tali durante l'elaborazione dei dati tramite il motore della pipeline di trasformazione dati. Il valore predefinito di questa proprietà è **False**.|  
  
 L'output dell'origine file flat non include proprietà personalizzate.  
  
 Nella tabella seguente vengono descritte le proprietà personalizzate delle colonne di output dell'origine file flat. Tutte le proprietà sono di lettura/scrittura.  
  
|Nome proprietà|Tipo di dati|Descrizione|  
|-------------------|---------------|-----------------|  
|FastParse|Boolean|Valore che indica se la colonna utilizza le routine di analisi più veloci ma indipendenti dalle impostazioni locali disponibili in DTS oppure le routine di analisi standard dipendenti dalle impostazioni locali. Per altre informazioni, vedere [Analisi veloce](https://msdn.microsoft.com/library/6688707d-3c5b-404e-aa2f-e13092ac8d95) e [Analisi standard](https://msdn.microsoft.com/library/dfe835b1-ea52-4e18-a23a-5188c5b6f013). Il valore predefinito di questa proprietà è **False**.<br /><br /> Nota: questa proprietà non è disponibile in **Editor origine file flat**, ma può essere impostata tramite **Editor avanzato**.|  
  
 Per altre informazioni, vedere [Origine file flat](../../integration-services/data-flow/flat-file-source.md).  
  
 **Proprietà personalizzate delle destinazioni**  
  
 La destinazione file flat include sia proprietà personalizzate che le proprietà comuni a tutti i componenti del flusso di dati.  
  
 Nella tabella seguente vengono descritte le proprietà personalizzate della destinazione file flat. Tutte le proprietà sono di lettura/scrittura.  
  
|Nome proprietà|Tipo di dati|Descrizione|  
|-------------------|---------------|-----------------|  
|Intestazione|string|Blocco di testo inserito nel file prima di iniziare a scrivere i dati.<br /><br /> È possibile specificare il valore di questa proprietà tramite un'espressione di proprietà.|  
|Overwrite|Boolean|Valore che specifica se sovrascrivere o aggiungere dati a un file di destinazione esistente con lo stesso nome. Il valore predefinito di questa proprietà è **True**.|  
  
 L'input e le colonne di input della destinazione file flat non includono proprietà personalizzate.  
  
 Per altre informazioni, vedere [Destinazione file flat](../../integration-services/data-flow/flat-file-destination.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà comuni](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
