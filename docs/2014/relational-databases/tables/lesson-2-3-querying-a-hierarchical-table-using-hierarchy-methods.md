---
title: Esecuzione di query su una tabella gerarchica tramite metodi gerarchici | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- HierarchyID
ms.assetid: 3b4f7dae-65b5-4d8d-8641-87aba9aa692d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: be1d0dcd37dba9b1025ba3e4a93aa60d2198b237
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2020
ms.locfileid: "66110053"
---
# <a name="querying-a-hierarchical-table-using-hierarchy-methods"></a>Esecuzione di query su una tabella gerarchica utilizzando metodi gerarchici
  Ora che la tabella HumanResources.EmployeeOrg è completamente popolata, in questa attività verrà illustrato come eseguire una query sulla gerarchia utilizzando alcuni dei metodi gerarchici.  
  
### <a name="to-find-subordinate-nodes"></a>Per trovare nodi subordinati  
  
1.  Sariya ha un dipendente subordinato. Per eseguire una query sui subalterni di Sariya, eseguire la query seguente che usa il metodo [IsDescendantOf](/sql/t-sql/data-types/isdescendantof-database-engine) :  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ;  
  
    SELECT *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.IsDescendantOf(@CurrentEmployee ) = 1 ;  
    ```  
  
     I risultati indicano sia Sariya sia Wanida. Sariya viene indicata perché rappresenta l'elemento discendente al livello 0. Wanida rappresenta l'elemento discendente al livello 1.  
  
2.  È anche possibile eseguire una query per ottenere tali informazioni usando il metodo [GetAncestor](/sql/t-sql/data-types/getancestor-database-engine) . `GetAncestor` accetta un argomento per il livello che si tenta di restituire. Poiché Wanida è un livello sotto Sariya, utilizzare `GetAncestor(1)` come dimostrato nel codice seguente:  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ;  
  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(1) = @CurrentEmployee  
    ```  
  
     Questa volta nei risultati viene indicata solo Wanida.  
  
3.  Ora impostare `@CurrentEmployee` su David (EmployeeID 6) e il livello su 2. Eseguire quanto segue per restituire anche Wanida:  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 6 ;  
  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(2) = @CurrentEmployee  
    ```  
  
     Questa volta, due livelli più in basso, viene indicata anche Mary che riporta a David.  
  
### <a name="to-use-getroot-and-getlevel"></a>Utilizzo di GetRoot e GetLevel  
  
1.  Con il crescere della gerarchia diventa più difficile determinare la posizione dei membri nella stessa. Usare il metodo [GetLevel](/sql/t-sql/data-types/getlevel-database-engine) per scoprire quanti livelli ci sono al di sotto di ogni riga della gerarchia. Eseguire il codice seguente per visualizzare i livelli di tutte le righe:  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode.GetLevel() AS EmpLevel, *  
    FROM HumanResources.EmployeeOrg ;  
    GO  
  
    ```  
  
2.  Usare il metodo [GetRoot](/sql/t-sql/data-types/getroot-database-engine) per cercare il nodo radice della gerarchia. Il codice seguente restituisce la singola riga che è la radice:  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode = hierarchyid::GetRoot() ;  
    GO  
  
    ```  
  
 L'attività successiva riorganizzerà la gerarchia.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
 [Riordinamento di dati in una tabella gerarchica utilizzando metodi gerarchici](lesson-2-4-reordering-data-in-a-hierarchical-table-using-hierarchical-methods.md)  
  
  
