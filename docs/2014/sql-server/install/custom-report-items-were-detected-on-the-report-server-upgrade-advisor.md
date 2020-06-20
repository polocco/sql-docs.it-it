---
title: Sono stati rilevati elementi del report personalizzati nel server di report (preparazione aggiornamento) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- custom report items, upgrading
ms.assetid: aee32006-65b2-4dfe-9570-d85a249d17b2
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: feacf6aa6f233f85a67b43e7b72d3a50913991bf
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059324"
---
# <a name="custom-report-items-were-detected-on-the-report-server-upgrade-advisor"></a>Sono stati rilevati elementi di report personalizzati nel server di report (Upgrade Advisor)
  Gli elementi del report personalizzati creati per le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] non sono compatibili con [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . L'aggiornamento può continuare, ma i report che utilizzano l'elemento del report personalizzato non verranno eseguiti come previsto. Sono stati rilevati elementi del report personalizzati. L'aggiornamento può continuare, ma è necessario spostare manualmente i file relativi agli elementi del report personalizzati nella nuova cartella di installazione dopo che l'aggiornamento è stato completato.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  Modalità nativa di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] &#124; Modalità SharePoint di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].|  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Descrizione  
 Nei file di configurazione sono state rilevate impostazioni di estensioni [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] personalizzate, indicanti che l'installazione include uno o più assembly personalizzati per il report.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Dopo che l'aggiornamento è stato completato, spostare manualmente i file relativi agli elementi del report personalizzati nella nuova cartella di installazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento Reporting Services &#40;preparazione aggiornamento&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
