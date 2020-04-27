---
title: Implementazione di un'estensione per il rendering | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- rendering extensions [Reporting Services]
- custom rendering extensions [Reporting Services]
- transformations [Reporting Services]
- extensions [Reporting Services], rendering
- rendering extensions [Reporting Services], implementing
ms.assetid: 4a5c64f5-2391-4597-ba3f-81d265b23703
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 03deb7c818de8d875f69b585ae6015fc178e707d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "62986749"
---
# <a name="implementing-a-rendering-extension"></a>Implementazione di un'estensione per il rendering
  Un'estensione per il rendering è un componente o un modulo di un server di report che consente di trasformare le informazioni sul layout e i dati del report in un formato specifico del dispositivo. SQL Server Reporting Services include sei estensioni per il rendering, ovvero HTML, Excel, Word, CSV o Text, XML, Image e PDF. È possibile creare estensioni per il rendering aggiuntive per generare report in altri formati.  
  
> [!NOTE]  
>  Per determinare quali sono le estensioni per il rendering disponibili, è possibile visualizzare l'elenco delle estensioni installate nel file RSReportServer.config.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Panoramica delle estensioni per il rendering](rendering-extensions-overview.md)  
 Vengono fornite informazioni introduttive per la scrittura di un'estensione per il rendering personalizzata per [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Implementazione dell'interfaccia IRenderingExtension](implementing-the-irenderingextension-interface.md)  
 Vengono descritti gli attributi di un'estensione per il rendering.  
  
 [Distribuzione di un'estensione per il rendering](deploying-a-rendering-extension.md)  
 Viene descritto come distribuire un'estensione per il rendering in un server di report.  
  
 [Rimozione di un'estensione per il rendering](removing-a-rendering-extension.md)  
 Viene descritto come rimuovere un'estensione per il rendering da un server di report.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni di Reporting Services](../reporting-services-extensions.md)   
 [Libreria di estensioni di Reporting Services](../reporting-services-extension-library.md)  
  
  
