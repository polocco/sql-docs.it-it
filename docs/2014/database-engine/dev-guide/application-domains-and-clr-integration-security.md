---
title: Domini applicazione e sicurezza dell'integrazione con CLR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- security [CLR integration]
- application domains [CLR integration]
ms.assetid: 54ee904e-e21a-4ee7-b4ad-a6f6f71bd473
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 85d6e66b1d51cc9d7c5829b8e83c510bea750e2a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2020
ms.locfileid: "84933762"
---
# <a name="application-domains-and-clr-integration-security"></a>Domini applicazione e sicurezza per l'integrazione con CLR
  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono caricati gli assembly che appartengono allo stesso proprietario in un dominio applicazione comune. Grazie a un set di assembly in esecuzione nello stesso dominio applicazione, gli assembly possono individuare altri assembly in fase di esecuzione utilizzando le API di reflection di .NET Framework o altri strumenti e possono effettuare una chiamata in tali assembly in modalità di associazione tardiva. Poiché tali chiamate vengono effettuate verso assembly che appartengono allo stesso proprietario, le autorizzazioni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per queste chiamate non vengono controllate. Lo schema di posizione degli assembly nei domini applicazione è stato progettato principalmente per realizzare obiettivi di scalabilità, sicurezza e isolamento e potrebbe cambiare nelle versioni future. Di conseguenza è consigliabile non basarsi sui meccanismi di associazione tardiva per individuare gli assembly nello stesso dominio applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza per l'integrazione con CLR](../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
  
