---
description: Proprietà personalizzate della destinazione elaborazione dimensione
title: Proprietà personalizzate della destinazione elaborazione dimensione | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9700f663-53f2-49b6-b1ef-92c7b752d6a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6cc1b502a64a30b5035b95b7d36207bc1cc281d2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/17/2020
ms.locfileid: "88348997"
---
# <a name="dimension-processing-destination-custom-properies"></a>Proprietà personalizzate della destinazione elaborazione dimensione

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  La destinazione elaborazione dimensione include sia proprietà personalizzate che le proprietà comuni a tutti i componenti del flusso di dati.  
  
 Nella tabella seguente vengono descritte le proprietà personalizzate della destinazione elaborazione dimensione. Tutte le proprietà sono di lettura/scrittura.  
  
|Proprietà|Tipo di dati|Descrizione|  
|--------------|---------------|-----------------|  
|ASConnectionString|string|Stringa di connessione a un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o a un progetto [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|KeyDuplicate|Integer (enumerazione)|Quando UseDefaultConfiguration è **False**, valore che indica come gestire gli errori di chiave duplicata. I valori possibili sono **IgnoreError** (0), **ReportAndContinue** (1) e **ReportAndStop** (2). Il valore predefinito di questa proprietà è **IgnoreError** (0).|  
|KeyErrorAction|Integer (enumerazione)|Quando UseDefaultConfiguration è **False**, un valore che indica come gestire gli errori di chiave. I valori possibili sono **ConvertToUnknown** (0) e **DiscardRecord** (1). Il valore predefinito della proprietà è **ConvertToUnknown** (0).|  
|KeyErrorLimit|Integer|Quando UseDefaultConfiguration è **False**, il limite massimo consentito di errori di chiave.|  
|KeyErrorLimitAction|Integer (enumerazione)|Quando UseDefaultConfiguration è **False**, un valore che indica l'azione da eseguire quando viene raggiunto il **KeyErrorLimit** . I valori possibili sono **StopLogging** (1) e **StopProcessing** (0). Il valore predefinito di questa proprietà è **StopProcessing** (0).|  
|KeyErrorLogFile|string|Quando UseDefaultConfiguration è **False**, il percorso e il nome del file di log degli errori.|  
|KeyNotFound|Integer (enumerazione)|Quando UseDefaultConfiguration è **False**, un valore che indica come gestire gli errori di chiave mancanti. I valori possibili sono **IgnoreError** (0), **ReportAndContinue** (1) e **ReportAndStop** (2). Il valore predefinito di questa proprietà è **IgnoreError** (0).|  
|NullKeyConvertedToUnknown|Integer (enumerazione)|Quando UseDefaultConfiguration è **False**, un valore che indica come gestire le chiavi Null convertite a un valore sconosciuto. I valori possibili sono **IgnoreError** (0), **ReportAndContinue** (1) e **ReportAndStop** (2). Il valore predefinito di questa proprietà è **IgnoreError** (0).|  
|NullKeyNotAllowed|Integer (enumerazione)|Quando UseDefaultConfiguration è **False**, un valore che indica come gestire i valori Null non consentiti. I valori possibili sono **IgnoreError** (0), **ReportAndContinue** (1) e **ReportAndStop** (2). Il valore predefinito di questa proprietà è **IgnoreError** (0).|  
|ProcessType|Integer (enumerazione)|Tipo di elaborazione della dimensione utilizzata dalla trasformazione. I valori sono **ProcessAdd** (1) (incrementale), **ProcessFull** (0), e **ProcessUpdate** (2).|  
|UseDefaultConfiguration|Boolean|Valore che specifica se la trasformazione utilizza la configurazione degli errori predefinita. Se questa proprietà è **False**, la trasformazione include informazioni sull'elaborazione degli errori.|  
  
 L'input e le colonne di input della destinazione elaborazione dimensione non includono proprietà personalizzate.  
  
 Per altre informazioni, vedere [Destinazione elaborazione dimensione](../../integration-services/data-flow/dimension-processing-destination.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà comuni](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
