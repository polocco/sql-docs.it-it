---
title: L'aggiornamento modificherà l'account proxy utente SQL Server Agent alla UpgradedProxyAccount temporanea | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server Agent]
ms.assetid: cd2d08c3-4e56-4034-8b68-0c78df8b5471
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2bca80580a50f2acebed1b6fbea2dec1f6458dbc
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058865"
---
# <a name="upgrading-will-change-the-sql-server-agent-user-proxy-account-to-the-temporary-upgradedproxyaccount"></a>In seguito all'aggiornamento l'account proxy utente per SQL Server Agent verrà sostituito dall'account temporaneo UpgradedProxyAccount
  I piani di manutenzione del database con il log shipping abilitato non verranno abilitati dopo l'aggiornamento.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
## <a name="description"></a>Descrizione  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è disponibile un nuovo set di funzioni di log shipping che non sono direttamente compatibili con i piani di manutenzione del database.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Gli utenti di [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] i cui piani di manutenzione del database contengono funzioni di log shipping devono configurare il log shipping utilizzando le nuove funzioni. Per ulteriori informazioni, cercare "log shipping" nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Agent log shipping categoria di processi causa l'esito negativo dell'aggiornamento](../../../2014/sql-server/install/sql-server-agent-log-shipping-job-category-causes-upgrade-to-fail.md)   
 [Il log shipping non verrà eseguito dopo l'aggiornamento](../../../2014/sql-server/install/log-shipping-will-not-run-after-upgrading.md)  
  
  
