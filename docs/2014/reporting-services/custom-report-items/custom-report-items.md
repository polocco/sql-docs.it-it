---
title: Elementi dei report personalizzati | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- extending Reporting Services
- Reporting Services, extending
- custom report items
ms.assetid: 64dcaf2c-1af5-4937-8ff7-98f1ec3b367e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 39860a2b147a2db392219552ebfd18cbbf7b7992
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "63264778"
---
# <a name="custom-report-items"></a>Elementi dei report personalizzati
  In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è disponibile un set completo di strumenti per la compilazione e la pubblicazione di report aziendali, la gestione di sicurezza e sottoscrizioni e l'estensione della funzionalità di report tramite un'API completa. I report vengono definiti utilizzando un linguaggio XML denominato Report Definition Language (RDL). RDL offre un set di istruzioni che descrivono le informazioni relative al layout e alle query e i tipi di elementi per un report. È possibile estendere RDL scrivendo un elemento del report personalizzato. Tale elemento è costituito da un componente runtime, che viene chiamato dal componente Elaborazione report in fase di esecuzione, e da un componente della fase di progettazione, che rende disponibile l'elemento del report personalizzato in Progettazione report.  
  
 Per un esempio di elemento del report personalizzato completamente implementato, vedere [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889) (Esempi del prodotto SQL Server Reporting Services).  
  
## <a name="custom-report-item-scenarios"></a>Scenari di elementi del report personalizzati  
 Gli sviluppatori che devono integrare [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nelle proprie applicazioni possono necessitare di funzionalità non supportate in RDL a livello nativo. Tali funzionalità includono ad esempio elementi quali controlli di mapping, elenchi orizzontali, elenchi in formato colonna e matrici di tabelle pivot. Un componente runtime dell'elemento del report personalizzato può essere sviluppato e distribuito con un'applicazione per soddisfare queste esigenze.  
  
 Oltre a disporre di funzionalità non supportate a livello nativo, alcuni sviluppatori potrebbero avere l'esigenza di estendere le funzionalità esistenti con versioni alternative di controlli già inclusi in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. In questo scenario, uno sviluppatore potrebbe disporre di tre componenti: un componente runtime, un componente della fase di progettazione e un componente di conversione dell'elemento del report in fase di progettazione che consente di convertire su richiesta un elemento del report esistente in un elemento del report personalizzato.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Architettura di un elemento del report personalizzato](custom-report-item-architecture.md)  
 Vengono descritti i componenti che costituiscono un elemento del report personalizzato.  
  
 [Requisiti per l'implementazione di elementi dei report personalizzati](custom-report-item-implementation-requirements.md)  
 Vengono descritti i prerequisiti per la creazione di un elemento del report personalizzato.  
  
 [Creazione di un componente runtime dell'elemento del report personalizzato](creating-a-custom-report-item-run-time-component.md)  
 Vengono descritte le procedure per la creazione di un componente runtime dell'elemento del report personalizzato.  
  
 [Creazione di un componente dell'elemento del report personalizzato per la fase di progettazione](creating-a-custom-report-item-design-time-component.md)  
 Vengono descritte le procedure per la creazione di un componente dell'elemento del report personalizzato in fase in progettazione.  
  
 [Procedura: Distribuire un elemento del report personalizzato](how-to-deploy-a-custom-report-item.md)  
 Vengono descritte le procedure per la distribuzione di un elemento del report personalizzato.  
  
 [Librerie di classi dell'elemento del report personalizzato](custom-report-item-class-libraries.md)  
 Vengono descritte le classi di infrastruttura dell'elemento del report personalizzato e classi wrapper gestite nello spazio dei nomi `Microsoft.ReportDesigner`.  
  
## <a name="see-also"></a>Vedi anche  
 [Riferimento tecnico &#40;SSRS&#41;](../technical-reference-ssrs.md)  
  
  
