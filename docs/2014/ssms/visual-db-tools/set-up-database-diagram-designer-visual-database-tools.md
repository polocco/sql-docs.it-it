---
title: Impostare Progettazione diagrammi di database (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.diagnostic.InstallSqlDiagramSupport
helpviewer_keywords:
- Database Diagram Designer
- database diagrams [SQL Server], Database Diagram Designer
- diagrams [SQL Server], Database Diagram Designer
ms.assetid: 927321ee-b459-4f5b-9719-4a7a95639143
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6d59fa2ed197a410de6b68e388e76d2bf21c334d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2020
ms.locfileid: "84994663"
---
# <a name="set-up-database-diagram-designer-visual-database-tools"></a>Impostazione di Progettazione diagrammi di database (Visual Database Tools)
  Per usare Progettazione diagrammi di database, è necessario che un membro del ruolo **proprietario_database** ne effettui preventivamente la configurazione per il controllo dell'accesso ai diagrammi.  
  
### <a name="to-set-up-database-diagramming"></a>Per impostare i diagrammi di database  
  
1.  In Esplora oggetti espandere un nodo di database.  
  
2.  Espandere il nodo dei diagrammi di database al di sotto della connessione al database.  
  
3.  Quando viene chiesto se si intende configurare i diagrammi di database, scegliere **Sì** .  
  
    > [!NOTE]  
    >  Nel database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verranno create la tabella del diagramma di database, le stored procedure di sistema e una funzione di sistema.  
  
4.  Tramite Visual Studio verranno creati i seguenti oggetti nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
    1.  Tabella sysdiagrams  
  
    2.  Stored procedure sp_alterdiagram  
  
    3.  Stored procedure sp_creatediagram  
  
    4.  Stored procedure sp_dropdiagram  
  
    5.  Stored procedure sp_renamediagram  
  
    6.  Funzione fn_diagramobjects  
  
    7.  Stored procedure sp_helpdiagrams  
  
    8.  Stored procedure sp_helpdiagramsdefinition  
  
    9. Stored procedure sp_upgraddiagrams  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sulla proprietà del diagramma di database &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Aggiornare i diagrammi di database delle precedenti edizioni &#40;Visual Database Tools&#41;](upgrade-database-diagrams-from-previous-editions-visual-database-tools.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-authorization-transact-sql)  
  
  
