---
title: Rimuovere le istruzioni che eliminano oggetti di sistema | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- drop system objects [SQL Server]
ms.assetid: cdfc3c50-c801-4039-a4bf-b35f876f1c61
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d9e8fbfd4a436e87cee413d95468ccf5dd36b9dd
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059176"
---
# <a name="remove-statements-that-drop-system-objects"></a>Rimuovere le istruzioni che eliminano oggetti di sistema
  Sono state rilevate istruzioni che eliminano oggetti di sistema. Gli oggetti di sistema, incluse le stored procedure estese, vengono distribuiti nel database **Resource** di sola lettura (mssqlsystemresource) e non possono essere eliminati. Modificare le applicazioni in modo da revocare o negare l'autorizzazione EXECUTE sugli oggetti di sistema.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Descrizione  
 Non è possibile utilizzare istruzioni quali DROP TABLE, DROP PROCEDURE e **sp_dropextendedproc** per rimuovere gli oggetti di sistema, poiché tali oggetti vengono distribuiti nel database **Resource** di sola lettura.  
  
## <a name="corrective-action"></a>Azione correttiva  
 Rimuovere dalle applicazioni tutte le istruzioni che tentano di eliminare oggetti di sistema. Modificare le applicazioni in modo da revocare o negare l'autorizzazione EXECUTE sugli oggetti di sistema. In alternativa è possibile utilizzare uno degli strumenti Configurazione superficie di attacco per disabilitare alcuni di questi oggetti. Ad esempio, il **xp_cmdshell** stored procedure esteso può essere disabilitato o abilitato mediante lo strumento SAC.  
  
## <a name="see-also"></a>Vedere anche  
 [Problemi di aggiornamento motore di database](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 preparazione aggiornamento &#91;nuova&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
